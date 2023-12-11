# Adder

In computer, we must build a full adder to compute any given two number; full adder works with two **XOR Gate** which one of them handles the two inputs and another **XOR** handles the carry bit with the calculated result. There are **AND Gate** too for handling carry bit for the next bit. Here is the single bit of full adder:

<object data="../apps/circuitjs/circuitjs.html?ctz=CQAgjCAMB0l3BWc0FwCwCY0HYEA4cEMElURTJyBTAWjDACgwE1w1WNsMRPveoeAhExYgAzGIBsPBNLSSOsgd0rCA7jy6buYyBy2QGG3fp1TtUI+PNhJlfrcqHj5rPa1vLG-p59YvFhj+YOw8-s4WjoHhVhh4eOBxIPKsYEkR9HzxbBzZGaGZIHiUhRHF4GlF9kpl1dIhitL5qQWVDQGF7YVxCREpiQn97RES9QCcOnrgEwEm05OmAf3E0ggzK5bMJQVJPQPKQiKUo+DYcgqnTYKqItxDduQzUfaHADI5YanSQaxOIABmAEMADYAZyo5Es73KG1sMiulCBYIhSEM7262Thez+SPBkMMtm4a24UUkWii3AAJlQgQBXYEAFxowKolPAAicsEYhMefCUZL53xA1LpjOZrPZfxgkEYAHMQALwA9JJiHk4GPLFRsVQkNuqgA
" width="100%" height="500vh"></object><br>

Single bit of full adder is really useless because it can only calculate number between 0 - 3 (including the carry bit), so we always cascade multiple of them to perform larger number like shown which is a 4 bit adder:

<object data="../apps/circuitjs/circuitjs.html?ctz=CQAgjCAMB0l3BWcMBMcUHYMGZIA4UA2ATmIxAUgoqoQFMBaMMAKAEIQATOgMwEMArgBsALlBABBADQAhKQGEQAZSkAdAM6KAxgPUiA9gFsNQ-QHMAllvDNVAR1sA7ZpHuQwqx+4933nsH6+Hs5w9gGe7q4Orl6B4bFRoY4saHggKAiEIHhUACxgWTni3PzCYlSQLADuINgIKDYNuXCNUNUgzVTMTS1gGFmVNZ3g-en4IwPtqRNjaZgNg7PpGA0ZWfNtQy0ozR0tuLmbe1TYhGnDudgLU+OXq+P1aYvTB0vDi8OvL5CHi3UNp3O+zOR3+6V2wx2FXaFyubzhz1u20yxyO00e6RRGL+9WyeVyaSKOPu5wJS2JtVOHTJ2CpFNyhEOuTJDN+7TBuWIWWZ5y5bQAMpjCl0UISKuJ+EJ1HRqJVBWtWmBRa1xZLpbKWPKUdMlXNxqq+FKZUg5ULwSK5rsDUaNVqsrSsrrKQMJYb1SbNWbAeBld7re6BWbWT7zozxFQ1cbAwrOY7lbHwyBIxqCk0yUUEEq8ekuLxBKIGEI6JxwImYO4WKnqXq0pmSTmSvmRIXi6XxeXWFWec6KFmHQ282UWyWIO3YJ3CGnQ4c6x0ww1G0OiyOy+PK5Pqx0+bOEwvBwXl23w2uzL2GhnmdnoafZ+jL9Nr2eewhL-3Hzuwy+mWH31mE1+txdSppgVaZ8nWfVc1KURwxScYFX7cCeyoRcYOhECUWDJDgxQ-dyjaIA
" width="100%" height="650vh"></object><br>
