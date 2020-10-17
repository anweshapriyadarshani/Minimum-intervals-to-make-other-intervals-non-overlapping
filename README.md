# Minimum-intervals-to-make-other-intervals-non-overlapping
Given a collection of intervals, find the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.  Intervals can "touch", such as [0, 1] and [1, 2], but they won't be considered overlapping.  For example, given the intervals (7, 9), (2, 4), (5, 8), return 1 as the last interval can be removed and the first two won't overlap.  The intervals are not necessarily sorted in any order.  


#include<bits/stdc++.h>

using namespace std;

int minremovals(vector<vector<int>>&ranges)
  
{

int size=ranges.size, rem=0;

if(size<=1)

	return 0;

//sort by minimum starting point

sort(ranges.begin(), ranges.end(), [](const vector<int>&a, const vector<int>&b)

{ return a[0]<b[0];});

int end=ranges[0][1];

for(int i=1;i<ranges.size();i++)

{

	//if current starting point is less than previous interval point they overlap
  
	if(ranges[i][0]<end)
  
	{
  
		//increase rem
		rem++;
    
		//remove interval with highest ending point
		end=min(ranges[i][1],end);
    
	}
	else
  
		end=ranges[i][1];
}
return rem;

}
//driver code

int main()

{
	vector<vector<int>>input={{19,25},{10,20},{16,20}};
  
	cout<<minremovals(input)<<endl;
  
}
