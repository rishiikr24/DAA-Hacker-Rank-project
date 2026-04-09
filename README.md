# DAA-Hacker-Rank-project
Problem Statement:
Maria plays college basketball and wants to go pro. Each season she maintains a record of
her play. She tabulates the number of times she breaks her season record for most points
and least points in a game. Points scored in the first game establish her record for the
season, and she begins counting from there.
Given the scores for a season, determine the number of times Maria breaks her records for
most and least points scored during the season.
For example, the table below depicts the number of times Maria broke her best and worst
records for the scores = [12, 24, 10, 24]:
Game Score Minimum Maximum Count Min Count Max
0 12 12 12 0 0
1 24 12 24 0 1
2 10 10 24 1 1
3 24 10 24 1 1
Problem HackerRank Link:
https://www.hackerrank.com/challenges/breaking-best-and-worst-records/problem
GitHub Submission Link:
https://github.com/rishikumar/DAA-Lab/blob/main/DAA/BreakingRecords.java
Solution Steps:
In this HackerRank Breaking Best and Worst Records problem solution, we are given the
scores array for a season of basketball games. The first game's score sets the baseline for
both the best (maximum) and worst (minimum) records. Starting from the second game, we
compare each score to the current records and count how many times each record is broken.
A record is broken only if the new score is strictly greater (for max) or strictly less (for
min) than the current record. Here are the solution steps:
1. Start the program.
2. Read the input value n, the number of games.
3. Read the array scores[n] containing the points scored in each game.
4. Initialize maxScore = scores[0] and minScore = scores[0] using the first game's
score as the baseline.
5. Initialize counters maxCount = 0 and minCount = 0 to track record breaks.
6. Loop from index i = 1 to n - 1.
7. Inside the loop, check if scores[i] > maxScore. If true, update maxScore = scores[i]
and increment maxCount++.
8. Also check if scores[i] < minScore. If true, update minScore = scores[i] and
increment minCount++.
9. Note: Equal scores do NOT break a record — strictly greater/lesser condition
applies.
10. After the loop, return the array [maxCount, minCount].
11. Print maxCount followed by minCount as the final output.
12. End the program.
Complete JAVA Code:
import java.util.*;
public class Solution {
public static int[] breakingRecords(int[] scores) {
int maxCount = 0;
int minCount = 0;
int maxScore = scores[0];
int minScore = scores[0];
for (int i = 1; i < scores.length; i++) {
if (scores[i] > maxScore) {
maxScore = scores[i];
maxCount++;
}
if (scores[i] < minScore) {
minScore = scores[i];
minCount++;
}
}
return new int[]{maxCount, minCount};
}
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
int[] scores = new int[n];
for (int i = 0; i < n; i++) {
scores[i] = sc.nextInt();
}
int[] result = breakingRecords(scores);
System.out.println(result[0] + " " + result[1]);
sc.close();
}
}
Observation/Solution:
The given Java program calculates the number of times Maria breaks her best (maximum)
and worst (minimum) scoring records over a season of basketball games. The first game's
score is used as the initial baseline for both records and is never counted as a record break.
The algorithm works by iterating through the scores array starting from the second element.
For each score, two independent checks are performed: whether the score is strictly greater
than the current maximum (best record), and whether it is strictly less than the current
minimum (worst record). Each time a record is broken, the corresponding counter is
incremented and the record is updated to the new value.
A key observation is that equal scores do not break any record. This is why during game 3
in Sample 0 (score = 20, same as current max = 20), the best record counter is not
incremented.
The solution uses a simple greedy single-pass approach — no sorting, no extra data
structures, and no backtracking are needed. Only four integer variables are maintained
throughout the entire computation, making this highly memory-efficient.
The program handles all edge cases correctly: monotonically increasing arrays (only max
breaks), monotonically decreasing arrays (only min breaks), all-equal arrays (no breaks at
all), and mixed arrays (both records may break multiple times).
Finally, the program returns and prints an array of two values — the number of best record
breaks at index 0, and the number of worst record breaks at index 1. The time complexity is
O(n) and the space complexity is O(1).

Hope you find this usefull.
