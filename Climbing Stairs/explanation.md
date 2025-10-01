#order 
recursion--->memoization--->tabulation


# If we are on step i, that means our last step could have been i-1 or i-2, because at once we can only have 1 or 2 jump
# i.e number of ways to reach i=number of ways to reach i-1 + number of ways to reach i-2
# f(i)=f(i-1)+f(i-2)  //base case would be f(0th step)=1 && f(1st step)=1



#naive recursion approach
--just like the fibonacci code

--pseudocode
  fun climbStairs(n){
    if(n<=1) return 1

    return climbStairs(n-1) + climbStairs(n-2)
  }



##OVERLAPPING OF PROBLEMS

--so when we will make call for suppose 5th stair 
--we know that it depends on the number ways it took to reach 4th stair and the 3rd stair
--similary the 4th stair recuriver call will depend on again calculating 3rd stair(again) and 2nd stair , similarly the 3rd stair call will depend on calculating 2nd step and 1step

-- we can observe the pattern that there have been few calls which have been made multiple times, those were already precomputed

-- so the idea of dynamic programming arises when we wish to store the already computed calls which happen to be overlapping, to save us time

hence this is called DYNAMIC PROGRAMMING



#fix-1 The Top Down approach(memoization)


int climbStairs_memo(int n, unordered_map<int,int>& memo) {
    if (n <= 1) return 1;
    if (memo.count(n)) return memo[n];
    memo[n] = climbStairs_memo(n-1, memo) + climbStairs_memo(n-2, memo);
    return memo[n];
}



#fix-2 The Bottom Up Approach

-- In this approach we think of building the solution from the most basic facts we know of the problem
-- in this case we are aware of the fact that number of ways for us to take to 0th step or 1th step =1
-- so we try to build the solution for n, from there


#4. General Recipe for Building Bottom-Up Intuition

----Whenever you have a DP recurrence:

----Define dp[i] clearly. (e.g., ways to reach step i).

----Write the recurrence. (dp[i] = dp[i-1] + dp[i-2]).

----Identify base cases. (dp[0], dp[1]).

----Ask: If I wanted to compute dp[i], what must already be known?

----That gives you the filling order.

----Implement a loop to fill in states one by one until the target.




class Solution {
public:
    int climbStairs(int n) {
        //now we will think about the recursive solution
        vector<int> dp(n+1,0);
        dp[0]=1;
        dp[1]=1;
        for(int i=2;i<=n;i++)
        {
            dp[i]=dp[i-1]+dp[i-2];
        }

        return dp[n];
        
    }
};
