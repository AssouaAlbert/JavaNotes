# Summary for the Deadlock topic
- Deadlock is a condition when two or more threads try to access the same resources at the same time. Then these threads can never access the resource and eventually go into the waiting state forever.
- So, the deadlock condition arises when there are more than two threads and two or more than two resources. Basically, a deadlock occurs when multiple threads request for the same resource but they are received in a different order.
- Eventually, they get stuck for an infinite period of time and cause a deadlock.
- Though it is not possible to completely get rid of the deadlock problem, we can take precautions to avoid such deadlock conditions. These preventive measures are as follows:
   - By avoiding Nested Locks
   - By avoiding unnecessary locks