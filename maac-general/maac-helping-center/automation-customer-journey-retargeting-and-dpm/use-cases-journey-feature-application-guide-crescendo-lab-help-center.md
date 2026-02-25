# Use Cases｜Journey Feature Application Guide – Crescendo Lab Help Center

This article summarizes common marketing use cases of the MAAC Journey feature to help marketers and Customer Success Managers (CSMs) understand how to best apply automated journeys for personalized and efficient customer communication flows.

For a feature overview, please refer to: [Tutorials｜Customer Journey ✨ New ✨](https://crescendolab.zendesk.com/hc/en-us/articles/4413212201113)

### Tag-Based Trigger: Automatically trigger journeys when a tag is applied

Use Cases

* Send a satisfaction survey when the “Paid” tag is applied
* Launch a welcome flow when the “New User” tag is applied

How to Set Up

* Select “Tag” as the trigger condition (MAAC or CAAC only)
* Specify the tag name and data source
* Design follow-up actions: message node, delay, additional tagging, etc.

Notes

* You can only select either MAAC or CAAC as the tag source (not both)
* Each contact can only trigger a tag-based journey once per hour

### Message Interaction Trigger: Start a journey based on user actions

Use Cases

* Start a follow-up sales journey when a user opens a specific message

How to Set Up

* Select "LINE Event - Message Opened" as the trigger condition
* Configure the flow after the trigger, such as sending a delayed message or branching

Notes

* Only supports LINE elements with tracked events (e.g., messages, buttons, rich menus)

### Friend Join Trigger: Welcome New Contacts Immediately

Use Cases

* When a user adds the brand’s LINE Official Account, the journey is automatically triggered to send a welcome message, onboarding guide, or introductory offer. This helps improve conversion and retention from the very beginning.

How to Set Up

* Select the trigger condition “LINE Event – New Contact Added.”
* Configure the follow-up flow, such as sending a welcome message, guiding the user through a purchase path, or creating branch processes.

Notes

* Ensure the LINE Official Account is correctly integrated with MAAC. It is recommended to use a delay node to avoid overwhelming users with multiple messages at once.

### Friend Block Trigger: Shift to Alternative Communication Channels

Use Cases

* When a user blocks the brand’s LINE Official Account, the journey is automatically triggered to apply a tag. Afterwards, follow-up actions can be taken through other channels (such as Email or SMS) to send surveys, collect feedback, or offer win-back promotions in order to understand the reason for blocking and maintain customer relationships.

How to Set Up

* Select the trigger condition “LINE Event – Contact Blocked.”
* Configure the flow after the trigger to apply a specific tag.
* Use segmentation filters to target these contacts and send SMS campaigns.

Notes

* The trigger condition only represents the “Contact Blocked” event. Follow-up marketing actions must be carried out via other channels. It is recommended to tag blocked users for segmentation and performance tracking.

### Website Behavior Trigger: Trigger journeys based on user actions on your website

Use Cases

* When a user adds a product to cart on your website, trigger a sales journey via LINE

How to Set Up

* Select "GA Event" as the trigger condition
* Configure the flow after the trigger, such as sending a delayed message or branching

Notes

* Only supports LINE elements with tracked events (e.g., messages, buttons, rich menus)

### Branch Node Applications: Split user paths for personalized handling

Use Cases

* Offer extra discounts based on whether a user clicked a message
* Deliver different content depending on whether a contact has the "High Value" tag

How to Set Up

* Insert a "Branch Node" in your flow
* Define branching conditions (e.g., has specific tag, message opened)
* Design custom content and actions for each path

### Delay and Schedule Nodes: Control the pacing of communication

Use Cases

* Send onboarding tutorials one hour after registration
* Remind users 3 days after they open a promo message

How to Set Up

* Insert a "Delay" or "Scheduled Time" node
* Set delay duration in minutes/hours/days or a specific time slot
* Continue with message or tag actions

### Add/Remove Tag Node: Record and classify user behavior

Use Cases

* Automatically tag a user as “Engaged\_Promo” after they open a LINE campaign message
* Remove the “HighPotentialBuyer” tag after a user completes a purchase on your website

How to Set Up

* Insert an "Add/Remove Tag" node after any action
* Configure the tag to be applied or removed

### Node Performance Analysis: Identify optimization opportunities

Available Metrics

| Node Type     | Metrics                                                 |
| ------------- | ------------------------------------------------------- |
| All Nodes     | Traffic (trigger count), Unique Contact Count           |
| Message Nodes | Push Count, Open Rate, Click Rate, Order Count, Revenue |
| Branch Nodes  | Volume and ratio of contacts per path                   |
| Tag Nodes     | Execution Count, Number of Affected Contacts            |

Suggestions

* Identify underperforming nodes to optimize content or timing
* Use tag-based segmentation to track behavior of specific groups

### Advanced Use Case: Automatically switch rich menus based on contact tags

Use Cases

* Display different rich menus for contacts tagged as VIP or Campaign Participants

How to Set Up

* In the Rich Menu settings, assign specific menus to specific tags
* Create a new journey or edit an existing one
* In the journey flow, set an action node to "Add Tag" (e.g., VIP\_USER)
* When a contact reaches this node and receives the tag, the system will automatically switch their visible rich menu

Notes

* If multiple rich menu tags are applied to the same contact, the display order cannot be guaranteed
* We recommend assigning only one rich menu tag per journey, or removing old tags before applying a new one
* You can also use a Branch Node to split contacts and ensure only one tag is applied per path
* For more details, see: [Tutorial｜Personalized Rich Menu](https://crescendolab.zendesk.com/hc/en-us/articles/26951166179609-Tutorial-Personalized-Rich-Menu)

Related articles

* [Tutorials｜Customer Journey ✨ New ✨](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkQ8ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlWIrwWLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJEL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTIyMDExMTMtVHV0b3JpYWxzLUN1c3RvbWVyLUpvdXJuZXktTmV3BjsIVDoJcmFua2kG--f9a82b931d9eb18efaa8f57fb8c9958470aebcdb)
* [Tutorial | SDK Web Behavior Tracking Tool](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJk0ii%2BuJToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlWIrwWLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzQxNDMwMDUyMTIzODAxLVR1dG9yaWFsLVNESy1XZWItQmVoYXZpb3ItVHJhY2tpbmctVG9vbAY7CFQ6CXJhbmtpBw%3D%3D--0bf3d10e67b1140049f94e1ee4fd703d05b82450)
* [Tutorials｜Editor/Broadcast-Share button](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlZTUSSEDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlWIrwWLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJOL2hjL2VuLXVzL2FydGljbGVzLzE4MjIwMzk3MTg5NDAxLVR1dG9yaWFscy1FZGl0b3ItQnJvYWRjYXN0LVNoYXJlLWJ1dHRvbgY7CFQ6CXJhbmtpCA%3D%3D--646aec4bc2e0a14ce50f2ffccb7159cccc8c355e)
* [Tutorials｜Game Interaction](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlM0QcdBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlWIrwWLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzQ1MjI3MzE3MTk3MDUtVHV0b3JpYWxzLUdhbWUtSW50ZXJhY3Rpb24GOwhUOglyYW5raQk%3D--2fe18eeab8d1a1f1a80fb8456c6d555fbebfc9b0)
* [Feature Overview｜Retargeting](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJlhmbH9JToYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlWIrwWLToLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJDL2hjL2VuLXVzL2FydGljbGVzLzQxNzcxNTM2NTcyODI1LUZlYXR1cmUtT3ZlcnZpZXctUmV0YXJnZXRpbmcGOwhUOglyYW5raQo%3D--29756d9107a9e303df293bb865f7740a009e1e52)
