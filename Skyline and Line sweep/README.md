## 850. https://leetcode.com/problems/rectangle-area-ii/

Thinking process:
1) need to build start and end event by x (also stores y1 and y2 along with each event), and when sees start event, add interval (y1,y2), when sees end event, remove interval (y1, y2), basically we are maintaining the active intervals for the current vertical sweep line
2) sort events by x. One thing to be careful here is that for the start and end event which have the same x and y1, y2, the sorting sequence or the event might matter in different language, becasue when remove(y1,y2) if it removes all the occurrences then we need to process the end event first and then start event which means sort by end event and then start event. But in python it's not needed since remove() only removes the first occurrence and we had two (y1,y2) in the intervals list before remove
3) once we have the intervals (also need to be sorted by y1), do line sweep each x by vertical line, every time we are at a new x, we can convert the rest to the "merge interval" problem. just get all the non-overlap intervals and multiply by the width to get the new area

## 218. https://leetcode.com/problems/the-skyline-problem/

Thinking process:
1) build start and end event  
2) use SortedList maintain max height for active buildings  
3) when current max height is different with last ans height, record the point  
4) to fix start/end events with same x, either process all events with same x together or use -h for start event and h for end event

## 1674. https://leetcode.com/problems/minimum-moves-to-make-array-complementary/

1) find range that needs 0/1 move for each pair  
2) base = n which means we can always use n (max moves) to make the arry complementary  
3) when entering the each range do -1, when out of the range +1  
4) line sweep from left to right and maintain the min value
