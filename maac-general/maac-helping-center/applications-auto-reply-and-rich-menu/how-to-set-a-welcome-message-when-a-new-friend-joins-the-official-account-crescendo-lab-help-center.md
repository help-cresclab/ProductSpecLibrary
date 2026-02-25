# How to set a "Welcome message" when a new friend joins the official account? – Crescendo Lab Help Center

When a new friend joins the official account, most brands will set a welcome message. Some brands offer product introductions and special discounts in their welcome messages to increase interaction with friends. In MAAC you can refer to the following settings process for new friends who join.

#### Setting

**Auto reply**

{% stepper %}
{% step %}
### Plan scenario

Any friend who joins from any source will be able to see this welcome message.\
Examples: friends join LINE OA by searching the official account, searching the official account ID, or clicking the official account invitation button.
{% endstep %}

{% step %}
### Setting process

Click MAAC "Applications > Auto-reply > create auto-reply", and select "welcome message" in trigger.

📚 Review: [Tutorials｜Auto-reply](https://crescendolab.zendesk.com/hc/th/articles/4413212257689-%E0%B9%80%E0%B8%A3%E0%B8%B5%E0%B8%A2%E0%B8%99%E0%B8%A3%E0%B8%B9-%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%83%E0%B8%8A-%E0%B8%82-%E0%B8%AD%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%95%E0%B8%AD%E0%B8%9A%E0%B8%81%E0%B8%A5%E0%B8%B1%E0%B8%9A%E0%B8%AD%E0%B8%B1%E0%B8%95%E0%B9%82%E0%B8%99%E0%B8%A1%E0%B8%B1%E0%B8%95%E0%B8%B4)

![\_\_\_2022-05-13\_\_\_6.37.35.png](<../../../.gitbook/assets/___2022 05 13___6.37.35.png>)
{% endstep %}
{% endstepper %}

**Deeplink**

{% stepper %}
{% step %}
### Plan scenario

This welcome message can only be seen by friends who have joined from specific sources.\
Examples: specific Facebook posts, official website checkout page, physical store, physical campaign.
{% endstep %}

{% step %}
### Setting process

Click MAAC "Applications > Deeplink". Different deeplinks can be created for different official website pages, different stores, and different posts. Apply different tags to different sources to create segments afterward.

📚 Review: [Tutorials｜Deeplink](https://crescendolab.zendesk.com/hc/th/articles/4413223724441-%E0%B9%80%E0%B8%A3%E0%B8%B5%E0%B8%A2%E0%B8%99%E0%B8%A3%E0%B8%B9-%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%83%E0%B8%8A-deeplink)

![\_\_\_2022-05-13\_\_\_6.37.35.png](<../../../.gitbook/assets/___2022 05 13___6.37.35.png>)
{% endstep %}
{% endstepper %}

#### Notes on operation & Related applications

What will happen when "Auto-reply - Welcome Message" and "Deeplink" are turned on at the same time?

{% stepper %}
{% step %}
### Friends join by searching the official account / ID / invitation button

They'll only receive the welcome message from "Auto-reply - Welcome message".
{% endstep %}

{% step %}
### Friends join by scanning or clicking the Deeplink

They'll receive both the "Auto-reply - Welcome message" and the welcome message from the "Deeplink" at the same time.
{% endstep %}
{% endstepper %}

**Our advice for different scenarios**

{% stepper %}
{% step %}
### Provide special discounts & information to new friends from specific sources

If you want to enable both Auto-reply and Deeplink and provide special discounts/information to new friends from specific sources (for example, store-specific discounts), consider:

* Auto-reply - Welcome message: chat information, product information, official website discounts, etc.
* Deeplink: provide a unique website page in the deeplink welcome message or new-friend discounts at exclusive stores.
{% endstep %}

{% step %}
### Collect join-source tags but don't send exclusive messages

If you want to enable Auto-reply so friends don't miss any welcome message, but you don't want to give exclusive discounts to friends who join from specific stores/sources and only want to tag their join source for later segmentation, consider:

* Auto-reply - Welcome message: chat information, product information, official website discounts, etc.
* Deeplink: set the tags only, and turn the deeplink message Off.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Reminder: Remember to close the welcome message in the LINE OA backend, otherwise the welcome message in the LINE OA backend and MAAC will both be triggered when new friends join!
{% endhint %}

![\_\_\_2022-05-14\_\_\_8.56.09.png](<../../../.gitbook/assets/___2022 05 14___8.56.09.png>)

Related articles

* [Tutorials｜MAAC Message Module & Template Library](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkJIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpBg%3D%3D--ef674b2a5c794a7a4de1dfe37668d1c3b03a2769)
* [Tutorials｜How to let friend share LINE OA to other friends ?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJl9O9erBjoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkJIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJgL2hjL2VuLXVzL2FydGljbGVzLzczMzUxMjAxNzQ0ODktVHV0b3JpYWxzLUhvdy10by1sZXQtZnJpZW5kLXNoYXJlLUxJTkUtT0EtdG8tb3RoZXItZnJpZW5kcwY7CFQ6CXJhbmtpBw%3D%3D--6ab02662c947aaa16503d109df0394e2386df540)
* [Why are my button tags all the same?](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlyDKwDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkJIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJJL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM4MTc5MDk3ODUtV2h5LWFyZS1teS1idXR0b24tdGFncy1hbGwtdGhlLXNhbWUGOwhUOglyYW5raQg%3D--0c71d50f14b48475a1cd6011a85f651687e626a2)
* [How to add Tester and send test message](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkSiYkDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkJIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJNL2hjL2VuLXVzL2FydGljbGVzLzQ0MTMyMzg4NzQ2NDktSG93LXRvLWFkZC1UZXN0ZXItYW5kLXNlbmQtdGVzdC1tZXNzYWdlBjsIVDoJcmFua2kJ--2ad4fbe1497cdb31890874e52c10dbab51f8cf31)
* [Tutorials｜Game Interaction](https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlM0QcdBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCBnkJIkDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzQ1MjI3MzE3MTk3MDUtVHV0b3JpYWxzLUdhbWUtSW50ZXJhY3Rpb24GOwhUOglyYW5raQo%3D--754644de38932b4aecb523e010facf5e45c71a49)
