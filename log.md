# 100 Days Of Code - Log

### Day 0: January 21, 2019

**Today's Progress**: Found new parameters and return values for API function calls being made from before. Updated those calls to allow the basic functionality of the addon to work again.

**Thoughts:** While fixing this, I came up with several "enhancements" to the addon such as a menu with a available list of realms with check boxes to allow the user to mark which realms to auto decline.

### Day 1: January 22, 2019

**Today's Progress**: Working on updating the addon to not trigger when in a LFG group. Started looking into adding the functionality to not run the addon logic if you are not party/raid leader. Found new functions to use to gather needed data to determine instance character is currently in. Use that data to determine the logic mentioned earlier

**Thoughts** Learned about some new WoW API functions to gain data that I don't really need, but it was cool to see some of the return values. Also gathered information on the LFG list window being opened vs. closed. Currently if the window is closed and someone joins, if you open the window the "auto decline" works. However, if the window is already opened the auto decline fails and the applicant stays in the list. Once you perform a refresh by clicking the refresh button, everything works as expected. Pasting findings below from debugging statements

Window Closed - Works as intended. Calls below show applicant name and order things run when they sign up
[22:31] Applicant signs up
[22:31] Chubchub 
[22:31] APPLICANT UPDATED LFG_LIST_APPLICANT_UPDATED 1 
[22:31] LIST UPDATED LFG_LIST_APPLICANT_LIST_UPDATED true true 
[22:31] LFG Window Opened
[22:31] Chubchub 
[22:31] APPLICANT UPDATED LFG_LIST_APPLICANT_UPDATED 1 
[22:31] LIST UPDATED LFG_LIST_APPLICANT_LIST_UPDATED nil nil 
[22:31] LIST UPDATED LFG_LIST_APPLICANT_LIST_UPDATED false false
[22:31] Applicant was auto declined

Window Open - Currently doesn't fully work
[22:33] Applicant signs up
[22:33] Chubchub 
[22:33] APPLICANT UPDATED LFG_LIST_APPLICANT_UPDATED 2 
[22:33] LIST UPDATED LFG_LIST_APPLICANT_LIST_UPDATED true true
[22:33] Performed Refresh
[22:33] Chubchub 
[22:33] APPLICANT UPDATED LFG_LIST_APPLICANT_UPDATED 2 
[22:33] LIST UPDATED LFG_LIST_APPLICANT_LIST_UPDATED nil nil 
[22:33] LIST UPDATED LFG_LIST_APPLICANT_LIST_UPDATED false false

