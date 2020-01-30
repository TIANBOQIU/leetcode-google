### [1007] Minimum Domino Rotations for Equal Row

#### description
> for this problem, we need to return the minimum number of rotations which makes an equal row on top tile. Return -1 if we can't.

#### Algorithms

**[solution 1]**
1. cnt1: -> # of rotations to make first row all A[0]
2. cnt2: -> # of rotations to make first row all B[0]
3. return the min(cnt1, cnt2) or -1

*Time complexity: O(n), n:= A.length*
*Space complexity: O(1)*

**[solution 2]**
> for i in 1 -> 6 if countA[i] + countB[i] -same[i] == A.length then we can return A.length - max(countA[i], countB[i]). 

> it will only have one solution or two equal solutions

*Time complexity: O(n), n:= A.length*
*Space complexity: O(n)*

**java**
```java
class Solution {
    public int minDominoRotations(int[] A, int[] B) {
        int[] countA = new int[7], countB = new int[7], same = new int[7];
        for (int i = 0; i < A.length; i++) {
            countA[A[i]]++; countB[B[i]]++;
            if (A[i] == B[i]) same[A[i]]++;
        }
        // only one possible answer
        for (int i = 1; i <= 6; i++) {
            if (countA[i] + countB[i] - same[i] == A.length)
                return A.length - Math.max(countA[i], countB[i]);
        }
        return -1;
    }
}   
```

**cpp**
```cpp
class Solution {
public:
    int minDominoRotations(vector<int>& A, vector<int>& B) {
        vector<int> countA(7), countB(7), same(7);
        for (int i = 0; i < A.size(); i++) {
            countA[A[i]]++; countB[B[i]]++;
            if (A[i] == B[i])
                same[A[i]]++;
        }
        
        for (int i = 1; i <= 6; i++) {
            if (countA[i] + countB[i] - same[i] == A.size())
                return A.size() - max(countA[i], countB[i]);
        }
        return -1;
    }
};
```
_____
