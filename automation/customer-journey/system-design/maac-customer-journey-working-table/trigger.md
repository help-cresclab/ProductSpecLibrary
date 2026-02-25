# Trigger

|                      No | Node Category | Node Type Name | Node Type | Settings (JSON) | Settings-1 / Operator | Settings-2 / Operator | Settings-2 / Value      | Settings-3 / Value                                                                         | Support Node Filter | Branch Settings (JSON) | Branch Settings / Type | Memo                                                                                                                     | Validation | Validation-2 / Type | Validation-3 / Rule | Validation-4 / timing | Timeline |
| ----------------------: | ------------- | -------------- | --------- | --------------- | --------------------- | --------------------- | ----------------------- | ------------------------------------------------------------------------------------------ | ------------------: | ---------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------- | ------------------- | ------------------- | --------------------- | -------- |
|                       1 |               | A0             | Empty     | -               | -                     | -                     | -                       |                                                                                            |                     |                        |                        |                                                                                                                          | n/a        | n/a                 |                     |                       | Future   |
|                       2 | Trigger       | A1             | Tag Added | \`\`\`json      |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|      { "tag\_id": 123 } |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|                  \`\`\` | was tagged    | -              | `{Tag}`   | -               | Yes                   | -                     | -                       | Cool Down Time of tag event: Every contact can only trigger the journey once every 1 hour. |              needed | singleSelect           | required               | Display "Please enter this field" when click outside the text field if ever clicked the text field, or click save button | P1-1       |                     |                     |                       |          |
|                       3 |               |                |           |                 | singleSelect          | max 1 tag             | single select component |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|                       4 |               | A2-1           | Page View | \`\`\`json      |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|                       { |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|      "op": "with\_any", |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|      "page\_url": null, |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
| "page\_duration": null, |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|     "page\_views": null |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |
|                       } |               |                |           |                 |                       |                       |                         |                                                                                            |                     |                        |                        |                                                                                                                          |            |                     |                     |                       |          |

````|
| 5 |  |  | viewed specific page | ```json
{
  "op": "with",
  "page_url": "https://example.com/products/123/",
  "page_duration": 30,
  "page_views": 2
}
``` | viewed specific page | specific | `{PageURL}` | greater or equal to {#} secs and (#) times | Yes | - | - | Cool Down Time of all GA event: Every contact can only trigger the journey once every 24 hour. | needed | textField | `{PageURL}:`<br>-- required<br>-- format: https:// | - Display "Please enter this field" when click outside the text field if ever clicked the text field, or click save button.<br>- Display "Please enter a valid URL" when click on blank space if entered the url. | P1-1 |
| 6 |  |  |  |  | number | {#} secs: required, default and min 1, max 999, integer and not allow symbols | Automatically correct the number to the nearest integer when the user enters a non-integer |  |  |  |  |  |  |  |  |  |
| 7 |  |  |  |  | number | (#) times: required, default and min 1, max 999, integer and not allow symbols | Automatically correct the number to the nearest integer when the user enters a non-integer |  |  |  |  |  |  |  |  |  |  |
| 8 | A2-2 | Purchase | ga_purchase | ```json
{
  "op": "with_any",
  "product_name": null
}
``` | purchased any item | any item | - | - | Yes | - | - | Cool Down Time of all GA event: Every contact can only trigger the journey once every 24 hour. | n/a | n/a |  |  |  |  | P1-1 |
| 9 |  |  | purchased specific item | ```json
{
  "op": "with",
  "product_name": "PlayStation"
}
``` | purchased specific item | specific item | `{ProductName}` | - | Yes | - | - |  | needed | textField | `{productName} is required` | Display "Please enter this field" when click outside the text field if or click save button | P1-1 |
| 10 | A2-3 | Add to Cart | ga_add_to_cart | ```json
{
  "op": "with_any",
  "product_name": null
}
``` | added any item to cart | any item | - | - | Yes | - | - | cart-drop=add to cart+waiting+purchase+action<br>Cool Down Time of all GA event: Every contact can only trigger the journey once every 24 hour. | n/a | n/a |  |  |  |  | P1-2 |
| 11 |  |  | added specific item to cart | ```json
{
  "op": "with",
  "product_name": "PlayStation"
}
``` | added specific item to cart | specific item | `{ProductName}` | - | Yes | - | - |  | needed | textField | `{productName} is required` | Display "Please enter this field" when click outside the text field if ever clicked the text field, or click save button | P1-2 |
| 12 | A3-1-1 | Join OA |  | - | joined(unblocked) LINE OA | - | - | - | Yes | - | - |  | n/a | n/a |  |  | Future |
| 13 | A3-1-2 | Block OA |  | - | blocked LINE OA | - | - | - | Yes | - | - |  | n/a | n/a |  |  | Future |
| 14 | A3-2-1 | Open Message | line_message_opened | ```json
{
  "op": "with_any",
  "msg_type": "broadcast",
  "msg_id": null
}
``` | opened any message (under the certain message type) | any message (under the certain message type) | `{MsgType}`<br>Options: "broadcast" | - | Yes | - | - |  | n/a | n/a |  |  |  |  | P2 |
| 15 |  |  | opened specific message (under the certain message type) | ```json
{
  "op": "with",
  "msg_type": "broadcast",
  "msg_id": 1
}
``` | opened specific message (under the certain message type) | specific message (under the certain message type) | `{MsgType}`<br>Options: "broadcast" | `{broadcast name/sent time/segmentName}` | Yes | - | - | sent broadcast only<br>8/8 updates: This node is expected to open for all message types. | needed | singleSelect | required | Display "Please enter this field" when click outside the text field if ever clicked the text field, or click save button | P2 |
| 16 | A3-2-2 | Click Message |  | - | clicked any message | any message | - | - | Yes | - | - |  | n/a | n/a |  |  | Future |
| 17 |  |  | clicked specific message |  | specific message |  | `{broadcast name/sent time/segmentName}` | Yes | - | - |  | n/a | n/a |  |  | Future |
| 18 | A4-1 | Binding Event |  | - | mapped | - | - | - | Yes | - | - |  | n/a | n/a |  |  | Future |
| 19 | A5-1 | CAAC Chat Status |  | - | changed to | - | resolved | - | Yes | - | - | new 待處理, follow-up 處理中, resolved 已完成 | n/a | n/a |  |  | Future |
| 20 | A6-1 | EC Event |  | - | - | - | - | - | Yes | - | - |  | n/a | n/a |  |  | Future |
| 21 | A7-1 | Segment |  | - | is | - | `{segmentName}` | - | Yes | - | - | can only select 1 segment | n/a | n/a |  |  | Future |

Notes / interpretation preserved exactly as in the source. JSON fields are shown as fenced code blocks for clarity. If you want this represented as a set of individual node docs (one section per node) or converted into a stepper for any sequential flows, tell me which subset to convert.
````
