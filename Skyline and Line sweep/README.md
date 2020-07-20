**850. https://leetcode.com/problems/rectangle-area-ii/**

Thinking process:
1) need to build start and end event by x (also stores y1 and y2 along with each event), and when sees start event, add interval (y1,y2), when sees end event, remove interval (y1, y2), basically we are maintaining the active intervals for the current vertical sweep line
2) sort events by x. One thing to be careful here is that for the start and end event which have the same x and y1, y2, the sorting sequence or the event might matter in different language, becasue when remove(y1,y2) if it removes all the occurrences then we need to process the end event first and then start event which means sort by end event and then start event. But in python it's not needed since remove() only removes the first occurrence and we had two (y1,y2) in the intervals list before remove
3) once we have the intervals (also need to be sorted by y1), do line sweep each x by vertical line, every time we are at a new x, we can convert the rest to the "merge interval" problem. just get all the non-overlap intervals and multiply by the width to get the new area
