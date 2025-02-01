import java.util.*;

public class TaskMaster {
    public static int tasks(int n, int[] a, int[] b) {
        // Step 1: Build the Graph (Adjacency List)
        Map<Integer, List<Integer>> graph = new HashMap<>();
        int[] inDegree = new int[n + 1]; // To track incoming edges

        for (int i = 0; i < a.length; i++) {
            graph.putIfAbsent(a[i], new ArrayList<>());
            graph.get(a[i]).add(b[i]);
            inDegree[b[i]]++; // Increment in-degree of dependent task
        }

        // Step 2: Topological Sorting using Kahn's Algorithm
        Queue<Integer> queue = new LinkedList<>();
        int count = 0;

        // Add all tasks with no dependencies (inDegree == 0) to queue
        for (int i = 1; i <= n; i++) {
            if (inDegree[i] == 0) {
                queue.add(i);
            }
        }

        while (!queue.isEmpty()) {
            int task = queue.poll();
            count++; // Task is completed
            
            if (graph.containsKey(task)) {
                for (int dependent : graph.get(task)) {
                    inDegree[dependent]--;
                    if (inDegree[dependent] == 0) {
                        queue.add(dependent);
                    }
                }
            }
        }

        // Step 3: Compute the maximum tasks that can be completed
        return count;
    }

    public static void main(String[] args) {
        int n = 7;
        int[] a = {1, 2, 3, 4, 6, 5};
        int[] b = {7, 6, 4, 1, 2, 1};

        System.out.println("Maximum tasks Eric can complete: " + tasks(n, a, b));
    }
}
