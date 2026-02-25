# Rule

| No                 | Node Type Name    | Node Type           | Settings (JSON) | Settings-1 / Operator              | Settings-2 / Operator | Settings-3 / Value | Settings-4 / Value | Support Node Filter | Branch Settings (JSON) | Branch Settings / Type | Memo                                                   | Validation | Validation-2 / Type | Validation-3 / Rule                     | Validation-4 / timing                                                                 | Timeline |
| ------------------ | ----------------- | ------------------- | --------------- | ---------------------------------- | --------------------- | ------------------ | ------------------ | ------------------- | ---------------------- | ---------------------- | ------------------------------------------------------ | ---------- | ------------------- | --------------------------------------- | ------------------------------------------------------------------------------------- | -------- |
| B1-1-1             | Yes/No Branch     | yes\_no\_branch     | (none)          | for "Filter", refer to "Condition" | -                     | -                  | -                  | No                  | Yes                    | Condition Split        |                                                        | needed     | textField           | {nodeName}: optional, max 32 characters | Display "Max 32 characters" when typing if the input exceeds the number of characters | P1-1     |
| B1-1-2             | (no label)        | -                   | -               | -                                  | -                     | -                  | -                  | No                  | Yes                    | Condition Split        |                                                        | needed     | textField           | {nodeName}: optional, max 32 characters | Display "Max 32 characters" when typing if the input exceeds the number of characters | P1-1     |
| B1-2               | Multi-branch      | multi\_branch       | (none)          | for "Filter", refer to "Condition" | -                     | -                  | -                  | No                  | Yes                    | Condition Split        | Limitation: Min 2 condition sets, Max 4 condition sets | n/a        | n/a                 |                                         |                                                                                       | Future   |
| B2-1               | Percentage Branch | (no type specified) | -               | -                                  | -                     | -                  | -                  | No                  | Yes                    | Percentage Split       |                                                        | n/a        | n/a                 |                                         |                                                                                       | Future   |
| B2-2               | A/B Testing       | (no type specified) | -               | -                                  | -                     | -                  | -                  | No                  | Yes                    | Percentage Split       |                                                        | n/a        | n/a                 |                                         |                                                                                       | Future   |
| B3-1               | Time Delay        | time\_delay         | \`\`\`json      |                                    |                       |                    |                    |                     |                        |                        |                                                        |            |                     |                                         |                                                                                       |          |
| {                  |                   |                     |                 |                                    |                       |                    |                    |                     |                        |                        |                                                        |            |                     |                                         |                                                                                       |          |
| "unit": "minutes", |                   |                     |                 |                                    |                       |                    |                    |                     |                        |                        |                                                        |            |                     |                                         |                                                                                       |          |
| "value": 60        |                   |                     |                 |                                    |                       |                    |                    |                     |                        |                        |                                                        |            |                     |                                         |                                                                                       |          |
| }                  |                   |                     |                 |                                    |                       |                    |                    |                     |                        |                        |                                                        |            |                     |                                         |                                                                                       |          |

````|
| B3-2 | Scheduled Time (排程時間) | time_schedule | Daily example: ```json
{
  "type": "daily",
  "schedules": [
    { "time": "HH:MM" }
  ]
}
``` Weekly example: ```json
{
  "type": "weekly",
  "schedules": [
    { "weekday": 1, "time": "HH:MM" }
  ]
}
``` Monthly example: ```json
{
  "type": "monthly",
  "schedules": [
    { "day": 1, "time": "HH:MM" }
  ]
}
``` | Specific time of everyday / Specific day and time of week / Specific day and time of month | - Time | - Day of week + Time | - Day of month + Time | - Time format is {HH}:{MM}<br>- Day of week format is {Monday/Thusday/Wednesday/Thursday/Friday/Saturday/Sunday}<br>- Day of month format is {1) to {31} |  |  |  |  | - Timezone: Bot.Timezone<br>- Need to notice the confliction with smart sending time settings. | needed | timePicker | {HH}: default 10, min 00, max 23<br>{MM}: defauld 00, min 00, max 59 | The date and time can't be clear to empty by keyboard or cursor so there're no field validation | P2 |
| (related controls) | singleSelect — Day of week |  | - default and min 1 group, max 7 group<br>- default is Monday<br>- Each option can only be selected once |  |  |  |  |  |  |  |  |  |  |  |  |  |
| (related controls) | singleSelect — Day of month |  | - default and min 1 group, max 31 group<br>- default is 1st<br>- Each option can only be selected once |  |  |  |  |  |  |  |  |  |  |  |  |  |
| B4-1 | Exit | exit | - | - | - | - | - | - | No | - | - |  | n/a | n/a |  |  | P1-1 |

Notes and clarifications:
- Keep all JSON examples exactly as shown above. Do not change any values or formats.
- For B1-1-1 and B1-1-2: Settings refer to "Condition" (Filter) elsewhere in the system.
- For B1-2: Condition Split supports 2–4 condition sets (min 2, max 4).
- For B3-1 (Time Delay): value ({#}) must be integer between 1 and 999. Non-integers should be auto-corrected to nearest integer.
- For B3-2 (Scheduled Time):
  - Time formats and defaults:
    - HH: default 10, min 00, max 23
    - MM: default 00, min 00, max 59
  - Timezone: Bot.Timezone
  - Note on conflict: scheduled time can conflict with smart sending time settings — UI should surface this.
  - The date/time fields cannot be cleared to empty via keyboard or cursor; thus no empty-value validation is required.
- SingleSelect controls:
  - Day of week: 1–7 groups, default Monday, each option selectable only once.
  - Day of month: 1–31 groups, default 1st, each option selectable only once.

If you want, I can convert each node into a separate GitBook page or add expandables per node for easier reading.
````
