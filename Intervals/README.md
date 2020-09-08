**1. minimum meeting rooms**

sort by start time, and then use pq to maintain eariest ending time, every time we have a new meeting, if start >= earlies ending, then we can reuse that meeting room (by heapq.heappop from the pq), and the length of the pq will be the meeting room needed. which also means the most intersections for all the intervals

253 - https://leetcode.com/problems/meeting-rooms-ii/  minimum meeting rooms  
732 - https://leetcode.com/problems/my-calendar-iii/ most intersections = minimum meeting rooms  

sort by start time, and then maintaining the end time, if the current start > end time, then we have a gap (free time)

759 - https://leetcode.com/problems/employee-free-time/
