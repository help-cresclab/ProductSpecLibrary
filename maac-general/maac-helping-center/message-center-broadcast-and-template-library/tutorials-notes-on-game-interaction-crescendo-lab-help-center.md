# Tutorials｜Notes on Game Interaction – Crescendo Lab Help Center

#### Notes on operation

**Basic notes**

* You can’t enter the fake template ID number.
* Be sure to keep one of the 6 prizes as the "No-winning prize". (If it’s a Lucky Wheel, avoid drawing the prize after the pin has nowhere to go. It may cause customer complaints.)
* If the marketing campaign rule is “everybody gets a prize”, you have to make sure there are enough prizes (and also enough prizes for prize management). The prizes will show “No-winning prize” if the prizes are drawn out.

{% hint style="info" %}
Reminder: If you check the number of prizes is almost used up, you can go to the game module edit page, and replenish the number of prizes.\
Example: If the original setting is 10, but you can see from the report that all the prizes have been drawn, please go to the game module edit page to set the number again — assuming it is reset to 20, then the system will still have 10 prizes valid. There is a note in the system: “Once the game is activated, the number of prizes can't be edited to the smaller number; please think carefully before setting it.”
{% endhint %}

* It is for an "Independent Event" chance. The number of prizes is not related to the set odds, and the odds are the same for everyone. (Different from variable odds systems where early draws affect later odds.)
* LINE will charge a fee for the winning message, but if the customer does not click "Claim Now" the message will not appear in the LINE official account.
* You can set the number of times a member can draw during the event and reset the number of games per day in the “No. of draws”. (e.g., activities for daily draw)
* Please do not adjust the settings after you start using it; if you must, please choose a non-peak time.
* If you want to distribute games to specific users (e.g., member binding to play the game, fill out the form to play the game), it is recommended to use "Game Tix", and avoid using Imagemap messages to send or combine with the rich menu, to prevent malicious people from cracking and sharing.

Review: Please review the Game Tix setting process Tutorials｜ Prize Management：Coupon、LINE Points、Vouchers、Game tixs、Brand Coupons

* Please separate the official and test modules "Prize" when setting up "Rapid Referral", avoiding the situation that the number of prizes in the “Rapid Referral” is not consistent with the number of prizes in the prize management, resulting in customer complaints.
* Please be sure to comply with the above notes; if the loss is caused by failure to comply, Crescendo Lab will not be responsible for compensation.

**What is the benefit of the MAAC game module "Independent Event" chance approach?**

* In the case of "Variable Event" odds, when 20 copies of prize A are drawn, there will be a chance to draw other prizes; although it is easy to achieve a prize for everyone, the prize may be drawn at the beginning.
* In the case of the "Independent Event" of the MAAC game interactive module, the first and 10,000th participants have an equal chance to draw the prize, so that the prize can be spread evenly during the event.

**Special operation notes on "Lucky Wheel"**

{% stepper %}
{% step %}
### Wheel basemap and custom images

Using the default basemap, the color and text of each frame of the wheel can be adjusted; custom basemap in some mobile phone device formats may run off (because of different resolutions).
{% endstep %}

{% step %}
### Prize positions

Please pay attention to the position and order of the prizes in the basemap of the custom wheel; please double-check to avoid setting the icon of prize one as prize six.
{% endstep %}

{% step %}
### No-winning prize

When setting up the lucky wheel, it is recommended that you always leave a No-winning prize.
{% endstep %}
{% endstepper %}

#### Is there any other application for "everyone gets a prize"?

Since the interaction game modules are "independent odds", it is still recommended to leave a No-winning prize.

Method 1: All six prizes need to be sufficient

* There is no distinction between large and small prizes.
* Each prize requires much more than the current target number of friends, and the prizes need to be drawn endlessly.
* When evaluating the number of prizes, be sure to consider the new friends' influence by the sharing from the game.

Method 2: Set five prizes and one "No-winning prize", and set the smallest prize as a consolation prize in the No-winning notification message

* Prizes are divided into big and small prizes.
* The smallest prize (consolation prize) is much larger than the target number of friends, and the prizes need to be drawn endlessly.
* When evaluating the number of smallest prize (consolation prize), be sure to consider the new friends' influence by the sharing from the game.
* A no-winning notification message will have a message push fee.

![Lucky wheel example image](../../../.gitbook/assets/7633344913433)

{% hint style="info" %}
Reminder: The above two methods both require observation of the number of prizes, and it is difficult to predict when LINE friends will draw prizes in practice. If you are sure that you need to execute the "everyone gets a prize" scenario, and if you want to match with advertisements and promotional literature, please evaluate and observe the number of prizes. If the loss is caused by not observing the cautions, Crescendo Lab will not be responsible for compensation.
{% endhint %}

<details>

<summary><strong>Why does an error screen appear when clicking on a game module?</strong></summary>

Interactive modules (e.g., lucky draws or games) require the system to recognize the user as a MAAC contact to function properly.

If a user clicks on the module link before joining the brand’s LINE Official Account, their identity cannot be recognized, resulting in an error screen. This behavior is expected by design.

Recommended Actions:

* Brands should import all LINE native friends into MAAC in advance to ensure the system can correctly identify user identities.
* If the error occurs during testing, please confirm that the tester has joined the LINE OA and become a MAAC contact.
* If the issue arises during an official campaign, check whether the user has successfully joined the LINE Official Account.

</details>

Related articles

* Tutorials｜Game Interaction: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBlM0QcdBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnzvNoDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJAL2hjL2VuLXVzL2FydGljbGVzLzQ1MjI3MzE3MTk3MDUtVHV0b3JpYWxzLUdhbWUtSW50ZXJhY3Rpb24GOwhUOglyYW5raQY%3D--90f197342329355bfc577aa77024cda175814d32
* Tutorials｜ Prize Management：Coupon、LINE Points、Vouchers、Game tixs、Brand Coupons: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBmFKXUDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnzvNoDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJ0L2hjL2VuLXVzL2FydGljbGVzLzQ0MTI4OTcwNjgzMTMtVHV0b3JpYWxzLVByaXplLU1hbmFnZW1lbnQtQ291cG9uLUxJTkUtUG9pbnRzLVZvdWNoZXJzLUdhbWUtdGl4cy1CcmFuZC1Db3Vwb25zBjsIVDoJcmFua2kH--121e4c970508af5967f045adab928679ff2ffc10
* Tutorials｜Rapid Referral: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkzBMgDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnzvNoDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSI%2BL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQyODcxMzE0MTctVHV0b3JpYWxzLVJhcGlkLVJlZmVycmFsBjsIVDoJcmFua2kI--6153e7ce82a04d8076d4d1f15551c1897baeaa21
* Tutorials｜ MAAC x SurveyCake Form: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCJkr5rYDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnzvNoDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJGL2hjL2VuLXVzL2FydGljbGVzLzQ0MTM5OTk5NTA3NDUtVHV0b3JpYWxzLU1BQUMteC1TdXJ2ZXlDYWtlLUZvcm0GOwhUOglyYW5raQk%3D--f5bc314a5db7e1b7aa928db969fca183dbdf79ed
* Tutorials｜MAAC Message Module & Template Library: https://crescendolab.zendesk.com/hc/en-us/related/click?data=BAh7CjobZGVzdGluYXRpb25fYXJ0aWNsZV9pZGwrCBkb49oDBDoYcmVmZXJyZXJfYXJ0aWNsZV9pZGwrCJnzvNoDBDoLbG9jYWxlSSIKZW4tdXMGOgZFVDoIdXJsSSJUL2hjL2VuLXVzL2FydGljbGVzLzQ0MTQ2MDM3Mjk2ODktVHV0b3JpYWxzLU1BQUMtTWVzc2FnZS1Nb2R1bGUtVGVtcGxhdGUtTGlicmFyeQY7CFQ6CXJhbmtpCg%3D%3D--777a82c18479a7d71ee0767cc8ea5a5d5eec8814
