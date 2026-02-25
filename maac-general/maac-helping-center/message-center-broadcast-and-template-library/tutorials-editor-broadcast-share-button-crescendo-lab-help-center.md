# Tutorials｜Editor/Broadcast-Share button – Crescendo Lab Help Center

#### 💁🏻‍♀️ Advantage

* Encourage friends to share content designed by the brand's official account, create viral spread benefits, and increase the awareness of marketing messages!
* By sharing with familiar friends and family, there is a good chance of reaching the same segmented audience and attracting them to become new friends of the account.

**➤ Plan Availability**

All MAAC plans, including the Standard version and Enterprise version.

#### ▶︎ Setting Steps

{% hint style="warning" %}
Before using the Share button feature, please go to the LINE Developers console and perform the following checks. If you have any questions during the operation, you can click on the blue chat icon at the bottom right to contact the MAAC customer support team.
{% endhint %}

{% stepper %}
{% step %}
### Configure LIFF in LINE Developers console

1. Open the LINE Developers console: https://developers.line.biz/en/
2. Select the Provider of your official brand account.
3. Check the Channel where LIFF "MAAC COMMON COMPACT" is located (this could be a Messaging API Channel or Login Channel).
4. Click on the LIFF tab and open the Share Target Picker.
{% endstep %}

{% step %}
### Note about message templates

Due to LINE's technical limitations, it is not possible to have both a share button and certain message templates (for example: imagemap, video, prize, send message) in the action area. If you attempt to use both, the system will prompt you to adjust your message accordingly.
{% endstep %}

{% step %}
### Where the Share Button can be used

After the Share Button feature is launched, you can use the Share Button in any MAAC feature that has a message template editor, such as:

* Broadcast
* Template Library
* Deeplink
* Auto Reply
* Customer Journey
* Retargeting
* Brand Coupon Message Setting in Prize Management

Reminder: Only in Broadcast, after using the Share Button, the clicks of share and Unique clicks of share can be tracked in the performance section.
{% endstep %}

{% step %}
### How to add a Share Button to a message

To include a Share Button in your message, please select the Message Template Card or Carousel Card, then configure the button below the card.
{% endstep %}
{% endstepper %}

![](../../../.gitbook/assets/18237777634457)

{% stepper %}
{% step %}
### Add the Share Button action

1. After editing the entire message content, proceed to set up the button below the card.
2. In the action area option, select the Share Button.
{% endstep %}

{% step %}
### Name and tag the Share Button

3. Enter the Share Button name (this name will help you view the relevant Share Button performance in the detailed report of a single audience broadcast).
4. Set the Share Button tag. You can attach a tag to friends who have clicked the Share Button, then filter interested friends' names in the Member and Audience features, or trigger an auto-journey and offer a discounted product bundle or exclusive marketing campaign to multiple people.
{% endstep %}
{% endstepper %}

![](../../../.gitbook/assets/18240146745881)

{% hint style="warning" %}
Due to the special parameters of the existing module built-in by the Rapid Referral, please do not use the Share Button in the message content for the inviter and invitee. To ensure the smooth operation of the Rapid Referral module, there is a mechanism to prevent it from being set up. If the Share Button is clicked to share, the special parameter value of the module will be cleared.
{% endhint %}

![](../../../.gitbook/assets/18240221731609)

#### ▶︎ Performance List

In Broadcast, click to enter the detailed report page of a single broadcast to view the relevant Share Button performance (you can view it in all tabs or click to view the Share Button tab).

* Clicks of Share Button: The number of times the Share Button has been clicked.
* Unique Clicks of Share Button: The number of times the Share Button has been clicked by unique users (i.e., the number of unique people who have clicked the Share Button).

![](../../../.gitbook/assets/18372233567129)

### Related articles

* [Tutorials｜MAAC Message Module & Template Library](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlZTUSSEDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpBg%3D%3D--822a54790a93674d8a0453a076f331d94a7968ec)
* [Tutorials｜LINE Broadcast](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmdF4kDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlZTUSSEDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzE0MzkxMjktVHV0b3JpYWxzLUxJTkUtQnJvYWRjYXN0BjsIVDoJcmFua2kH--d9ce6c83de4e5aaac558f643b8cae724cf02dcbc)
* [Tutorials｜How to let friend share LINE OA to other friends ?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJl9O9erBjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlZTUSSEDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzczMzUxMjAxNzQ0ODktVHV0b3JpYWxzLUhvdy10by1sZXQtZnJpZW5kLXNoYXJlLUxJTkUtT0EtdG8tb3RoZXItZnJpZW5kcwY7CFQ6CXJhbmtpCA%3D%3D--642c067e786f39e7c72cb426348a37a0e143c476)
* [Tutorials｜Smart Sending](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJmDF4kDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlZTUSSEDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI9L2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzE0MzI2MDEtVHV0b3JpYWxzLVNtYXJ0LVNlbmRpbmcGOwhUOglyYW5raQk%3D--bf269d35e420cf5b83dd54470143b7f2916768f2)
* [What is the "notification text"? What is the difference between "notification text", "message preview" and "message"?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBldJIkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBlZTUSSEDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSIBiy9oYy9lbi11cy9hcnRpY2xlcy80NDEzMjMyMjc0NzEzLVdoYXQtaXMtdGhlLW5vdGlmaWNhdGlvbi10ZXh0LVdoYXQtaXMtdGhlLWRpZmZlcmVuY2UtYmV0d2Vlbi1ub3RpZmljYXRpb24tdGV4dC1tZXNzYWdlLXByZXZpZXctYW5kLW1lc3NhZ2UGOwhUOglyYW5raQo%3D--699b55f46d3d36787a95d1efdbc9f4798ac0d695)
