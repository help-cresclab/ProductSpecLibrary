# Condition

Below are the conditions, their JSON definitions, settings, validation rules and timeline notes. I kept the original content and JSON intact.

***

## Condition (Node Category: Condition)

### Tag (E1-1-1)

* Condition key: `tag`
* Variants:
  *   with specific tag

      ```json
      {
        "condition": "tag",
        "op": "with",
        "value": 123,
        "extra": null
      }
      ```

      * Settings / Operator: with specific tag
      * Settings-2 / Value: {Tag}
      * Settings-3 / Extra 1: -
      * Settings-4 / Extra 2: -
      * Memo: Tag is an integer. Can only select 1 tag. Multi-tag TBD.
      * Validation-1: needed
      * Validation-2 / Type: singleSelect
      * Validation-3 / Rule: max 1 tag
      * Timeline: P1-1
  *   without specific tag

      ```json
      {
        "condition": "tag",
        "op": "without",
        "value": 123,
        "extra": null
      }
      ```

      * Description: without specific tag
      * Settings-2 / Value: {Tag}
      * Validation-1: needed
      * Validation-2 / Type: singleSelect
      * Validation-3 / Rule: max 1 tag
      * Timeline: P1-1
  *   with any tag

      ```json
      {
        "condition": "tag",
        "op": "with_any",
        "value": null,
        "extra": null
      }
      ```

      * Description: with any tag
      * Settings: n/a
      * Timeline: P1-1
  *   without any tag

      ```json
      {
        "condition": "tag",
        "op": "without_any",
        "value": null,
        "extra": null
      }
      ```

      * Description: without any tag
      * Settings: n/a
      * Timeline: P1-1

***

## Page view (E1-2-1, condition key: `ga_page_view`)

* Common note about numeric fields:
  * {#} secs: required, default and min 1, max 999, integer, do not allow symbols.
  * (#) times: required, default and min 1, max 999, integer, do not allow symbols.
  * (#) days: required, default & min 1, max 90 (FE default and max handling described per variant).
  * Automatically correct non-integers to nearest integer.
  * Automatically correct the number to 30 when the user enters a number exceeding 30 (FE behavior noted).

Variants:

### has viewed any page

```json
{
  "condition": "ga_page_view",
  "op": "with_any",
  "value": null,
  "extra": {
    "page_duration": 1,
    "page_views": 1,
    "days_within": 1
  }
}
```

* Settings-1 / Operator: has viewed any page
* Settings-2: greater or equal to {#} secs and (#) times
* Settings-3: past {#} days
* Validation-1: needed
* Validation-2 / Type: number
* Validation-3 / Rule: {#} secs: required, default and min 1, max 999, integer and not allow symbols; (#) times: required, default and min 1, max 999, integer and not allow symbols
* Validation-4 / timing: Automatically correct the number to the nearest integer when the user enters a non-integer
* Timeline: P1-3

### has viewed specific page

```json
{
  "condition": "ga_page_view",
  "op": "with",
  "value": "/products/<product_id>/",
  "extra": {
    "page_duration": 1,
    "page_views": 1,
    "days_within": 1
  }
}
```

* Settings-2 / Value: {PageURL}
* Settings-2 / Constraints: textField {PageURL} — required, format: https://
  * UI validations:
    * Display "Please enter this field" when clicking outside the text field if the field was focused and left empty, or when clicking save.
    * Display "Please enter a valid URL" when clicking on blank space if the entered URL is invalid.
* Settings-2: greater or equal to {#} secs and (#) times
* Settings-3: past {#} days
* Validation-1: needed
* Validation-2 / Type: number
* Validation-3 / Rule: {#} secs and (#) times rules same as above
* Validation-4 / timing: Automatically correct non-integers to nearest integer
* Timeline: P1-3

### has not viewed any page

```json
{
  "condition": "ga_page_view",
  "op": "without_any",
  "value": null,
  "extra": {
    "page_duration": null,
    "page_views": null,
    "days_within": 1
  }
}
```

* Description: has not viewed any page
* Settings-3: past {#} days
  * {#} default is 1, maximum is 30 for FE; 90 for BE (thread: https://chatbotgang.slack.com/archives/C04305BTUBE/p1687864176141149?thread\_ts=1686132636.068979\&cid=C04305BTUBE)
* Validation-1: needed
* Validation-2 / Type: number
* Validation-3 / Rule: same secs/times rules where relevant
* Validation-4 / timing: Automatically correct non-integers to nearest integer; FE clamps >30 to 30
* Timeline: P1-3

### has not viewed specific page

```json
{
  "condition": "ga_page_view",
  "op": "without",
  "value": "/products/<product_id>/",
  "extra": {
    "page_duration": null,
    "page_views": null,
    "days_within": 1
  }
}
```

* Settings-2 / Value: {PageURL}
* Settings-3: past {#} days
* Validation-1: needed
* Validation-2 / Type: number
* Validation-3 / Rule: (#) days: required, default & min 1, max 90, integer and not allow symbols
* Validation-4 / timing: Automatically correct non-integers to nearest integer; FE clamps >30 to 30
* Timeline: P1-3
* UI notes for {PageURL} text field: required; format https://; same validation messages as specific page above.

***

## Purchase (E1-2-2, condition key: `ga_purchase`)

Shared notes:

* (#) days: required, default & min 1, max 90, integer and not allow symbols.
* Automatically correct the number to the nearest integer when the user enters a non-integer.
* Automatically correct the number to 30 when the user enters a number exceeding 30.
* Timeline: P1-3 for variants.

Variants:

### has purchased any item

```json
{
  "condition": "ga_purchase",
  "op": "with_any",
  "value": null,
  "extra": {
    "days_within": 1
  }
}
```

* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

### has purchased specific item

```json
{
  "condition": "ga_purchase",
  "op": "with",
  "value": "<productName>",
  "extra": {
    "days_within": 1
  }
}
```

* Settings-2 / Value: {ProductName}
* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

### has not purchased any item

```json
{
  "condition": "ga_purchase",
  "op": "without_any",
  "value": null,
  "extra": {
    "days_within": 1
  }
}
```

* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

### has not purchased specific item

```json
{
  "condition": "ga_purchase",
  "op": "without",
  "value": "<productName>",
  "extra": {
    "days_within": 1
  }
}
```

* Settings-2 / Value: {ProductName}
* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

***

## Add to Cart (E1-2-3, condition key: `ga_add_to_cart`)

Shared notes:

* (#) days: required, default & min 1, max 90, integer and not allow symbols.
* Automatically correct non-integers to nearest integer and clamp >30 to 30 (FE).
* Timeline: P1-3 for variants.

Variants:

### has added any item to cart

```json
{
  "condition": "ga_add_to_cart",
  "op": "with_any",
  "value": null,
  "extra": {
    "days_within": 1
  }
}
```

* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

### has added specific item to the cart

```json
{
  "condition": "ga_add_to_cart",
  "op": "with",
  "value": "<productName>",
  "extra": {
    "days_within": 1
  }
}
```

* Settings-2 / Value: {ProductName}
* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

### has not added any item to cart

```json
{
  "condition": "ga_add_to_cart",
  "op": "without_any",
  "value": null,
  "extra": {
    "days_within": 1
  }
}
```

* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

### has not added specific item to the cart

```json
{
  "condition": "ga_add_to_cart",
  "op": "without",
  "value": "<productName>",
  "extra": {
    "days_within": 1
  }
}
```

* Settings-2 / Value: {ProductName}
* Settings: past {#} days
* Validation-1: needed
* Validation-2 / Type: number

***

## Friend status (E1-3-1)

* Condition name: Friend status
* Possible values:
  * is Active
    * JSON: not specified in table
    * Settings-2 / Value: Active
    * Validation: n/a
    * Timeline: Future
  * Blocked(/Auth)
    * Timeline: Future

***

## Open message (E1-3-2)

* Variants (Timeline: Future):
  * has opened any message — settings: past {#} days
  * has opened specific message — settings: {broadcast name/ID}, past {#} days
  * has not opened any message — settings: past {#} days
  * has not opened specific message — settings: {broadcast name/ID}, past {#} days
* Validation: n/a

***

## Click message (E1-3-3)

* Variants (Timeline: Future):
  * has clicked any message — settings: past {#} days
  * has clicked specific message — settings: {broadcast name/ID}, past {#} days
  * has not clicked any message — settings: past {#} days
  * has not clicked specific message — settings: {broadcast name/ID}, past {#} days
* Validation: n/a

***

## (Customer ID) (E2-1)

* Variants (Timeline: Future):
  * Binding completed
  * Binding incomplete
* Validation: n/a

***

## User profile attributes (E3 series) — Timeline: Future

### Gender (E3-1-1)

* Options: Man, Female, Other
* Note: no "all gender", no "no data", single select
* Validation: n/a

### Engagement Level (E3-1-2)

* Options: Level 1, Level 2, Level 3, Level 4, Level 5
* Note: no "all level", single select
* Validation: n/a

### Phone (E3-1-4)

* Options: Valid Phone, Invalid Phone
* Validation: n/a

### Email (E3-1-5)

* Options: Valid Email, Invalid Email
* Validation: n/a

### Birthday (E3-1-5)

* Variants:
  * is specific date — {MM}
    * {#} default is 1, maximum is 12
  * is specific date — {DD}
    * {#} default is 1, maximum is 31
* Validation: n/a

### Age (E3-1-6)

* Variants:
  * is — {age}
    * {#} default is 1, maximum is 999 (positive integers)
    * system calculates automatically: {current year} - {year} = age
  * is between — {age} and {age}
  * is greater or equal to — {age}
  * is less than or equal to — {age}
* Validation: n/a

***

If you want, I can:

* Convert each condition into individual markdown pages,
* Generate a table-of-contents with links to each condition,
* Or convert any repeated numeric-field rules into one reusable snippet to include across pages.
