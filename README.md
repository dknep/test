
import java.util.*;

public class NeuralTaskAllocation {
    public static int maxTasksCompleted(int n, int[] tasks, int m) {
        // Step 1: Count occurrences of each task
        Map<Integer, Integer> taskFrequency = new HashMap<>();
        for (int task : tasks) {
            taskFrequency.put(task, taskFrequency.getOrDefault(task, 0) + 1);
        }

        // Step 2: Sort tasks by frequency (descending order)
        List<Integer> frequencies = new ArrayList<>(taskFrequency.values());
        Collections.sort(frequencies, Collections.reverseOrder());

        // Step 3: Distribute tasks across m nodes
        int[] nodeLoad = new int[m];  // Tracks the number of tasks each node has
        int completedTasks = 0;

        for (int freq : frequencies) {
            Arrays.sort(nodeLoad); // Always assign to the least loaded node
            for (int i = 0; i < Math.min(m, freq); i++) { // Distribute among nodes
                nodeLoad[i]++;
                completedTasks++;
            }
        }

        return completedTasks;
    }

    public static void main(String[] args) {
        int n = 4;
        int[] tasks = {1, 2, 1, 1, 2};
        int m = 2;

        System.out.println("Maximum tasks completed: " + maxTasksCompleted(n, tasks, m));
    }
}
