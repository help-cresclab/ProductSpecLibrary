# Basic setting

{% stepper %}
{% step %}
### Name (F1)

* Node Type Name: Name
* Settings (JSON): {name}
* Settings-1 / Operator: (none)
* Settings-2 / Operator: (none)
* Settings-3 / Value: (none)
* Settings-4 / Value: (none)
* Support Node Filter: (none)
* Memo:
  * Names must be unique
  * Name will be copied and added suffix "\{{name\}} copy" when duplicates
  * prefix supports multi-language
* Validation:
  * Validation-1: needed
  * Validation-2 / Type: textField
  * Validation-3 / Rule: {Name}: required, max 32 characters, must be unique
  * Validation-4 / timing: Display "Max 32 characters" when typing if the input exceeds the number of characters
* Timeline: P1-1
{% endstep %}

{% step %}
### Operating Schedule (F2)

* Node Type Name: Operating Schedule
* Settings (JSON): Start time / End time
* Settings-1 / Operator: (none)
* Settings-2 / Operator: YYYY-MM-DD HH:MM (for Start time)
* Settings-3 / Value: (none)
* Settings-4 / Value: (none)
* Support Node Filter: fields will be copied when duplicates ([thread](https://chatbotgang.slack.com/archives/C04305BTUBE/p1692946145313419))
* Memo: (none)
* Validation:
  * Validation-1: needed
  * Validation-2 / Type: date\&timePicker
  * Validation-3 / Rule:
    * Either of start time or end time is required if ON
    * Can't be earlier than now
  * Validation-4 / timing: Verify start time and end time together
* Timeline: P1-1

#### Start time

* Format: YYYY-MM-DD HH:MM

#### End time

* Format: YYYY-MM-DD HH:MM
* Additional Validation:
  * Can't be earlier than start time
{% endstep %}

{% step %}
### Trigger Limitation (F3)

* Node Type Name: Trigger Limitation
* Settings (JSON): {#} times
* Settings-1 / Operator: (none)
* Settings-2 / Operator: {#}
* Settings-3 / Value: (none)
* Settings-4 / Value: (none)
* Support Node Filter: fields will be copied when duplicates
* Memo: (none)
* Validation:
  * Validation-1: needed
  * Validation-2 / Type: number
  * Validation-3 / Rule: Required if ON; integer, min 1, max 10080
  * Validation-4 / timing: (none)
* Timeline: P1-1
{% endstep %}

{% step %}
### Message Sending Limitation (F4)

* Node Type Name: Message Sending Limitation
* Settings (JSON): {#} counts
* Settings-1 / Operator: (none)
* Settings-2 / Operator: {#}
* Settings-3 / Value: (none)
* Settings-4 / Value: (none)
* Support Node Filter:
  * fields will be copied when duplicates
  * After publication this value can only be increased.
* Memo: (none)
* Validation:
  * Validation-1: needed
  * Validation-2 / Type: number
  * Validation-3 / Rule: Required if ON; integer, min 1, max 10M
  * Validation-4 / timing: (none)
* Timeline: P1-1
{% endstep %}

{% step %}
### Do not disturb (F5)

* Node Type Name: Do not disturb
* Settings (JSON): Start time / End time
* Settings-1 / Operator: (none)
* Settings-2 / Operator: HH:MM (for Start time)
* Settings-3 / Value: (none)
* Settings-4 / Value: (none)
* Support Node Filter: fields will be copied when duplicates
* Memo: (none)
* Validation:
  * Validation-1: needed
  * Validation-2 / Type: timePicker
  * Validation-3 / Rule:
    * Required if ON
    * Default is empty
  * Validation-4 / timing: (none)
* Timeline: P1-1

#### Start time

* Format: HH:MM

#### End time

* Format: HH:MM
{% endstep %}
{% endstepper %}
