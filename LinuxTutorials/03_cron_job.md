# Cron Job In Linux

---

Cron Job works perfectly in server side workstation.

[] Check all cron job: ` crontab -l `
[] Edit cron job: ` crontab -e ` If you're in "Ubuntu", ` select-editor ` will select your editor for cron job or other editor.

`

|--------------------- minute (0 - 59)
| |------------------- hour (0 - 23)
| | |----------------- day of month (1 - 31)
| | | |--------------- month (1 - 12)
| | | | |------------- day of week(0 - 6) (Sun - Sat; 7 = Sunday on some system)
| | | | |
| | | | |
* * * * * command_to_execute

`

---

` * * * * * echo 'Hello' >> /temp/test.txt `
This command `echo 'Hello'` will run and save it to `/temp/test.txt` on every minute of every hour of everyday of the week of every month.

---


