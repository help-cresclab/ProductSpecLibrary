# Why are  my button tags  all the same? – Crescendo Lab Help Center

The tag triggered by clicking a button will be paired with "Broadcast Message". For example: when you choose "send message" in the action area, enter the words "checking order" in the message column and add a tag "checking". When you send the message "checking order", it will automatically bring in the tag "checking". Therefore, it is recommended to set different text for sending messages so that the tag can be different.

You can refer to the following setting process.

Scenario: You want to ask friends questions by using auto-reply, letting friends click and be tagged with their preferences.

Setting process:

{% stepper %}
{% step %}
### Setting the first level of auto-reply

* Setting the keyword of auto-reply: Find flavor
* Setting the message and button from the Imagemap. There are three options: Thai Style, Japanese style, and Taiwanese style.
{% endstep %}

{% step %}
### Configure each flavor button

* Click "Thai Style" → Send the message " I love Thai Style", and friends will be tagged with "flavor\_Thai".
* Click "Japanese Style" → Send the message " I love Japanese Style", and friends will be tagged with "flavor\_Japanese".
* Click "Taiwanese Style" → Send the message " I love Taiwanese Style", and friends will be tagged with "flavor\_Taiwanese".
{% endstep %}

{% step %}
### Create a second level of auto-reply (optional)

If you want to ask further questions, you can create a second level of auto-reply (for example, product packaging type-related questions):

* Setting the keyword of auto-reply: " I love Thai Style"
* Setting the message and button from the Imagemap. There are two options: a small package, and a family-size package.
* You can set the content in the template library.
* Follow the previous steps to set all the content.
* You can use templates in the template library to create second-level questions for other answers quickly.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Reminder: It's the same setting rule and process if you use the "Quick Reply" function in the editor. The message will also be paired with a tag.
{% endhint %}

Images:

![Screenshot 1](../../../.gitbook/assets/6783009144601)

![Screenshot 2](../../../.gitbook/assets/6783167032217)

![Screenshot 3](../../../.gitbook/assets/6783193951641)

Related articles

* [Tutorials｜MAAC Message Module & Template Library](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyDKwDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpBg%3D%3D--51c1bdb24fd207d2853706fff995429b3fc1d38b)
* [What does “Open in external browser" mean?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmxIKsDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyDKwDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJNL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM4MDI0NTk1NDUtV2hhdC1kb2VzLU9wZW4taW4tZXh0ZXJuYWwtYnJvd3Nlci1tZWFuBjsIVDoJcmFua2kH--69f2c8b8d0c5bfd267b599abbcde53b69036d5a9)
* [Tutorial｜Segment](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlzlogDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyDKwDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI2L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMjI5NzQyMzMtVHV0b3JpYWwtU2VnbWVudAY7CFQ6CXJhbmtpCA%3D%3D--d6a8fcce8adf4b81d62058efb169633149273cfe)
* [How to share LINE OA platform, LINE Developers, GA(UA) / GA4 access to Crescendo Lab?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmp1FFgBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyDKwDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ1L2hjL2VuLXVzL2FydGljbGVzLzgxMTAyNzExNDYzOTMtSG93LXRvLXNoYXJlLUxJTkUtT0EtcGxhdGZvcm0tTElORS1EZXZlbG9wZXJzLUdBLVVBLUdBNC1hY2Nlc3MtdG8tQ3Jlc2NlbmRvLUxhYgY7CFQ6CXJhbmtpCQ%3D%3D--35c5f5c2d929802b41137c2feb5ee7a9193e440d)
* [Tutorial | CAAC Conduct Conversation and Contact Information](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJn6ysBcBzoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlyDKwDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzgwOTQ5NTI5MTM1NjEtVHV0b3JpYWwtQ0FBQy1Db25kdWN0LUNvbnZlcnNhdGlvbi1hbmQtQ29udGFjdC1JbmZvcm1hdGlvbgY7CFQ6CXJhbmtpCg%3D%3D--553231b65ee9853ba3b3522ed79b79044d311e22)
