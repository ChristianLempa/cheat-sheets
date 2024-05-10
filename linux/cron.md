# Cron

| Field | Allowed Values | Description |
|---|---|---|
| `SECOND` | 0-59 | Trigger every SECOND second(s) |
| `MINUTE` | 0-59 | Trigger every MINUTE minute(s) |
| `HOUR` | 0-23 | Trigger every HOUR hour(s) |
| `DAY` | 1-31 | Trigger every DAY day(s) of month |
| `MONTH` | 1-12 | Trigger every MONTH month(s) |
| `DAY OF WEEK` | 0-6 | MON-SUN Trigger on specific DAY OF WEEK |

## Special Characters

| Special Character | Description |
| --- | --- |
| `*` | Trigger on tick of every time unit |
| `,` | List separator |
| `–` | Specifies a range |
| `/` | Defines an increment |

## Examples

| Cron Expression | Description |
| --- | --- |
| `0 * * * * *` | Executes every minute |
| `0 0 * * * *` | Executes every hour |
| `0 0 0 * * *` | Executes every day |
| `0 0 0 0 * *` | Executes every month |
| `0 0 0 1 1 *` | Executes on first day of Jan each year |
| `30 20 * * SAT` | Executes at 08:30pm every Saturday |
| `30 20 * * 6` | Executes at 08:30pm every Saturday |
| `0 */5 * * * *` | Executes every five minutes |
| `0 0 8-10/1 * * *` | Executes every hour between 8am and 10am |
