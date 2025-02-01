import java.util.*;

public class NeuralTaskAllocation {
    public static int maxTasksCompleted(int n, int[] tasks, int m) {
        // List of sets to track unique tasks assigned to each node
        List<Set<Integer>> nodes = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            nodes.add(new HashSet<>()); // Each node has a set of unique tasks
        }

        int completedTasks = 0;
        
        // Try to allocate tasks efficiently
        for (int task : tasks) {
            // Try assigning the task to any node that does not already have it
            boolean assigned = false;
            for (Set<Integer> node : nodes) {
                if (!node.contains(task)) {
                    node.add(task);
                    completedTasks++;
                    assigned = true;
                    break; // Move to the next task once assigned
                }
            }
        }
        
        return completedTasks;
    }

    public static void main(String[] args) {
        int n = 7;
        int[] tasks = {1, 2, 2, 1, 3, 1, 3};
        int m = 2;

        System.out.println("Maximum tasks completed: " + maxTasksCompleted(n, tasks, m));
    }
}
