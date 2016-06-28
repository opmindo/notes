LOOKING->
vote(sid, zxid)
find max(sid or zxid) and set it as server's vote
if some server's vote is greater than or equal to  (n/2 + 1), then set it as leader, state change to FOLLOWING, leader state change to LEADING, else continue to vote
