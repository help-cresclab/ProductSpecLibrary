# smsplus\_asana\_history\_knowledge\_base\_final

## Investigation of Server Error During API Call for Contact Import

**Metadata**

* **Feature:** MAAC-MAAC Open API (except SMS+API)
* **Created At:** 2025-11-24
* **Asana Task ID:** [1212069322792739](https://app.asana.com/1/1184020052539844/task/1212069322792739)
* **Ticket Priority:** P2
* **Client Name:** \[REDACTED]
* **Resolution Owner:** David
* **Result Breakdown:** Fix Problems

### 1. Issue Description

Customers experienced a "Server Error" when using the import contact feature on 10/20 and 10/22. Despite API calls returning a success status (200), the import task failed.

### 2. Context & Details

* **Environment Conditions:**
  * Occurred on 10/20 and 10/22.
  * API calls returned a 200 status code.
  * Import tasks showed failure despite successful API response.
* **User Questions:**
  * Is the error a genuine server issue or a configuration error on the client's side?
* **Reproduction Steps:**
  * Attempt to import contacts using the API.
* **Expected vs Actual Behavior:**
  * Expected: Successful contact import.
  * Actual: Server error message and import failure.

### 3. Root Cause & Solution

* **Root Cause:**
  * The issue was identified as an intermittent conflict (409) during the update of metadata for objects in Google Cloud Storage (GCS) in the import process. This was due to an underlying system performance or concurrency issue.
* **Solution:**
  * A fix addressing the performance and concurrency issue has been deployed to production. The engineering team will monitor the system for several days to ensure stability.
