Greedy search vs A* search

(1)
Simple Case (A* d<20):
Heuristic	Generated Nodes (A*)	Generated Nodes (Greedy)	Solution Depth (A*)	Solution Depth (Greedy)
H0 (h=0)	5	10	3	3
H1 (h=differences)	4	6	3	3
H2 (h=distances)	5	6	3	3
Hard Case (A* d>20):
Heuristic	Generated Nodes (A*)	Generated Nodes (Greedy)	Solution Depth (A*)	Solution Depth (Greedy)
H0 (h=0)	382629	2402	26	63
H1 (h=differences)	7971	40860	28	495
H2 (h=distances)	305685	2594	26	73

Discussion:
•	In the simple case, A* consistently generated fewer nodes and achieved similar solution depths compared to Greedy Search across different heuristics.
•	In the hard case, A* produced more nodes than Greedy Search but found solutions with notably lower depths, showcasing its capability to reach more optimal solutions despite increased computational load.
•	The choice of heuristic affected the number of generated nodes, but the optimality of solutions remained prominent, especially for A*.
These tables demonstrate the impact of different heuristic functions on the number of generated nodes and solution depths in both simple and hard cases, highlighting the strengths and trade-offs of A* and Greedy Search algorithms in solving problems.


(2)
// Heuristic H3 using Manhattan distance
int cal_score_h3(char *map, int *target_map, int num){
    int sum = 0;
    for(int i = 0; i < num; i++){
        // Calculate Manhattan distance for each tile position
        int row_diff = abs(i / 4 - target_map[i] / 4);
        int col_diff = abs(i % 4 - target_map[i] % 4);
        sum += row_diff + col_diff;
    }
    return sum;
}
Test case:
10
8 1 4 0 4 5 8 7 6 1
0 1 1 4 4 5 8 7 6 8

Results for A* Algorithm with Different Heuristics:
Heuristic	Generated Nodes (A*)	Solution Depth (A*)
H0 (h=0)	382629	26
H1 (h=differences)	7971	28
H2 (h=distances)	305685	26
H3 (Manhattan distance)	66550	26





(3)
Discussion:
•	Heuristic H0 generated a large number of nodes while maintaining a solution depth of 26.
•	H1 (differences) resulted in significantly fewer nodes but a slightly higher solution depth of 28.
•	H2 (distances) showcased a substantial number of nodes and the same solution depth as H0.
•	H3, employing the Manhattan distance heuristic, produced a moderate number of nodes (66550) with a solution depth of 26.
These results demonstrate the performance of different heuristics (H0, H1, H2, H3) in the A* algorithm for the provided test case. H3, utilizing the Manhattan distance heuristic, managed to find a solution with a moderate number of nodes and an optimal depth, providing a balanced performance compared to the other heuristics in this specific scenario.

(4)
Changing the heuristic functions significantly impacted the search efficiency and solution optimality in both simple and hard cases. A* algorithm's ability to strike a balance between the number of generated nodes and solution optimality makes it a more effective approach for solving complex problems compared to Greedy Search. The choice of heuristic plays a crucial role in determining the computational load and solution quality in these search algorithms.
