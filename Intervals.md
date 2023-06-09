Home: [[🏠 Coding Interviews]] 

## Meeting Rooms II
- Given an array of meeting time intervals consisting of start and end times `[[s1, e1],[s2,e2],...] (si < ei)`, find the minimum number of conference rooms required

### Method 1
- Maintain a count of however many meetings are going on at any given time
	- At the start of a meeting, increase count
	- At the end of a meeting, increase count
- Return max of count
- Put start times and end times in a separate array (sorted)
	- Have a pointer for start and end
	- If the start pointer is less than the end pointer, increase count
	- If the end pointer is greater than or equal to the start, decrease count

**Solution**
```Python
def minMeetingRooms(intervals):
	
```