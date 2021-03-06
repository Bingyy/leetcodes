# Meeting Rooms II

## Problem Description

Given an array of meeting time intervals consisting of start and end times`[[s1,e1],[s2,e2],...]`\(si&lt; ei\), find the minimum number of conference rooms required.

For example,  
Given`[[0, 30],[5, 10],[15, 20]]`,  
return`2`.

> Google, Snapchat, Facebook

## Analysis

This problem can be solved with sorting or heap \(kind of the same thing\)

**Heap**

sort intervals with start time.

put intervals into heap, sorting based on end time.

put first started interval into heap \(as ongoing meeting\).

for next started interval, first pull interval in heap, compare end time. if new interval start time bigger than ongoing meeting, it is okay and just update current ongoing meeting end time. else, put new interval into heap. put pulled interval back.

**without heap**

put start time and end time in two list. sort.

use a variable to track current available rooms, and a variable track number of rooms.

if first start no less than first end, available add one, move to next end.

if first start less than first end, if no available, required plus one, else available minus one.

Actually, these are the same thing

## Solution

```py
# Definition for an interval.
# class Interval(object):
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution(object):
    def minMeetingRooms(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: int
        """
        starts = []
        ends = []
        for i in intervals:
            starts.append(i.start)
            ends.append(i.end)
        starts.sort()
        ends.sort()
        s = e = 0
        numRooms = available = 0
        while s < len(starts):
            if starts[s] < ends[e]:
                if available == 0:
                    numRooms += 1
                else:
                    available -= 1
                s += 1
            else:
                available += 1
                e += 1
        return numRooms
```



