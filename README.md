# Carbon-Jar---SaaS-Technical-Test

Question 18: Backend Error Handling and Resilience
Overview:
This solution makes a flaky backend service more reliable by adding retries with the tenacity library and explains circuit breakers.
Solution
Retries:
Used tenacity to retry call_flaky_service if it fails with a ConnectionError.
Set 3 retry attempts with delays of 1s, 2s, 4s (exponential backoff) to avoid overloading the system.
Added logging to track failures, retries, and successes.

