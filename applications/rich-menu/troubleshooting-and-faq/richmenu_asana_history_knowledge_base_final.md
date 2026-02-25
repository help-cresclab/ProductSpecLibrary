# richmenu\_asana\_history\_knowledge\_base\_final

## Investigation of Incorrect Rich Menu Tagging After Contact Import via API

**Metadata**

* **Feature:** MAAC-Richmenu
* **Created At:** 2025-10-31
* **Asana Task ID:** [1211803131074457](https://app.asana.com/1/1184020052539844/task/1211803131074457)
* **Ticket Priority:** P2
* **Client Name:** Advance Medical Clinic
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

The system incorrectly assigned the 'Prestige' Rich Menu to a user tagged with 'Classic' after importing contacts via the MAAC API. The expected Rich Menu should have been 'Classic', but the user received 'Prestige' despite not having the 'Prestige' tag in their profile.

### 2. Context & Details

* **Environment Conditions:**
  * The account is configured with Rich Menus tagged by membership tiers: Classic, Prestige, Signature, and Elite.
  * Contacts were imported using the MAAC API.
* **Reproduction Steps:**
  1. Import contact with 'Classic' tag via MAAC API.
  2. Observe the assigned Rich Menu.
* **Expected vs Actual Behavior:**
  * **Expected:** User with 'Classic' tag receives 'Classic' Rich Menu.
  * **Actual:** User with 'Classic' tag received 'Prestige' Rich Menu.
* **Additional Information:**
  * The issue's impact on end users is unclear.
  * Occurrences were noted daily around 01:00 UTC+7 for specific users.

### 3. Root Cause & Solution

* **Root Cause:**
  * The MAAC system logs do not indicate any internal unlinking of Rich Menus. Engineering monitoring confirmed that specific members experienced daily unlinking. The issue is attributed to a third-party vendor's scheduled job interfering with LINE Rich Menu assignments.
* **Solution:**
  * No changes are required within the MAAC system. The client should collaborate with third-party vendors (Beacon, Loyalty, CDP) to identify and resolve the external processes causing the Rich Menu changes.
