# Why Are the Pre-set Auto-reply and Rich Menu Not Working? – Crescendo Lab Help Center

#### Q: When Auto-reply Are Not Working

<details>

<summary>Troubleshooting steps</summary>

Trigger ConditionsEnsure that the trigger conditions you set for the auto-response match the way you are activating it in the chat.KeywordsIf using keywords as the trigger, make sure they do not include any symbols, as this can cause failure.Webhook SettingsGo to LINE Backend > Settings > Response Settings, and make sure Webhook is "Enabled".Go to LINE Backend > Settings > Messaging API, and ensure the Webhook URL is set to the MAAC Webhook: https://event.cresclab.com/api/webhook/line//eventsKeywords SourceIf all the above are correct, check if you copied and pasted the keywords from other sources (such as forms, Excel, web pages) when initially setting up the auto-reply. Try manually entering the keywords again.

</details>

***

#### Q: When the Rich Menu Is Not Working

<details>

<summary>Troubleshooting steps</summary>

StatusEnsure the rich menu is set to "Active".User AttributesVerify there are no conflicts between the rich menu settings and your user attributes (e.g., if the menu is set for bound members, but you are an unbound friend).Webhook SettingsGo to LINE Backend > Settings > Response Settings, and make sure Webhook is "Enabled".Go to LINE Backend > Settings > Messaging API, and ensure the Webhook URL is set to the MAAC Webhook: https://event.cresclab.com/api/webhook/line//eventsImage File TypesEnsure the images uploaded in the rich menu are in jpg, jpeg, or png formats. Transparent png images are not supported.You can check the image file format using https://mediaarea.net/MediaInfoOnline

</details>

***

#### Q: Why didn't the Rich Menu update immediately after adding a user to a segment?

<details>

<summary>Answer</summary>

The "Segment-based switch" Rich Menu operates on a **daily scheduled update** mechanism (usually executed every morning around 7:00 AM).

* If you have just added a user to a segment, they will not see the new menu until after the system's scheduled update the **following morning**.
* If you require an "immediate" switch, please use the **"Tag"** trigger function instead.

</details>

***

#### Q: If a user belongs to multiple segments, which menu will they see?

<details>

<summary>Answer</summary>

If a user meets the conditions for multiple segments simultaneously, the system will prioritize displaying the **"Last Edited"** Rich Menu. You can adjust the priority by simply re-editing and publishing the menu you wish to display first.

If the above steps are correct but the problem persists, it might be due to an expired Access Token. For more information, refer to the article "What is an Access Token and What to Do When It Expires?" (https://crescendolab.zendesk.com/hc/en-us/articles/4413800932121-What-is-an-Access-Token-and-What-to-Do-When-It-Expires) or contact your Crescendo Lab CSM or use the assistant in the bottom right corner.

</details>

***

Related articles

* Tutorial｜Basic Setup and Multi-page Guide for Rich Menu: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkm6ocDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJletogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJdL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMTE2ODIzMjktVHV0b3JpYWwtQmFzaWMtU2V0dXAtYW5kLU11bHRpLXBhZ2UtR3VpZGUtZm9yLVJpY2gtTWVudQY7CFQ6CXJhbmtpBg%3D%3D--ae1a28cfc6f9139a5191ccb87bcf8b668f7da739
* What is an Access Token and What to Do When It Expires?: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBljCasDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJletogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJcL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM4MDA5MzIxMjEtV2hhdC1pcy1hbi1BY2Nlc3MtVG9rZW4tYW5kLVdoYXQtdG8tRG8tV2hlbi1JdC1FeHBpcmVzBjsIVDoJcmFua2kH--d96644842464ad19a681ea0d84ea73c074e2735d
* How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJletogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCA%3D%3D--c900855ce7563137a1993f1c3fa5972d437b5854
* What is the "notification text"? What is the difference between "notification text", "message preview" and "message"?: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBldJIkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJletogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSIBiy9oYy9lbi11cy9hcnRpY2xlcy80NDEzMjMyMjc0NzEzLVdoYXQtaXMtdGhlLW5vdGlmaWNhdGlvbi10ZXh0LVdoYXQtaXMtdGhlLWRpZmZlcmVuY2UtYmV0d2Vlbi1ub3RpZmljYXRpb24tdGV4dC1tZXNzYWdlLXByZXZpZXctYW5kLW1lc3NhZ2UGOwhUOglyYW5raQk%3D--c3f5dcccbba600bf852b38d90857f7bf14dffecb
* Tutorial | CAAC Conduct Conversation and Contact Information: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn6ysBcBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJletogDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzgwOTQ5NTI5MTM1NjEtVHV0b3JpYWwtQ0FBQy1Db25kdWN0LUNvbnZlcnNhdGlvbi1hbmQtQ29udGFjdC1JbmZvcm1hdGlvbgY7CFQ6CXJhbmtpCg%3D%3D--f1c8fac3a0049b5f773601c4a81a9b1c3ed7dd98
