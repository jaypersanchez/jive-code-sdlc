# L-013: Session Timeout on Inactivity
**Preconditions**: user authenticated, lastActivityTs present
**Flow**: if now - lastActivityTs > MAX_IDLE → revoke token → redirect → toast
**Postconditions**: token invalid, user on /login
**Edge Cases**: clock skew, multiple tabs, background timers
**Pseudocode**:
- onActivity() updates lastActivityTs
- watchdog() checks diff every N seconds
- logout() centralizes revoke+redirect
