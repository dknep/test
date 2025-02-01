import java.util.*;

public class SubsequenceSort {
    // Function to check if a given binary string can be sorted into "000...111"
    public static boolean canBeSorted(String binary) {
        // The only condition where it's NOT possible to sort is if "10" exists in the string.
        return !binary.contains("10");
    }

    // Function to check each query in arr
    public static List<String> checkQueries(String binary, String[] arr) {
        List<String> result = new ArrayList<>();

        for (String query : arr) {
            // Replace '?' with both '0' and '1' to check all possibilities
            String minQuery = query.replace('?', '0'); // Try all '?' as '0'
            String maxQuery = query.replace('?', '1'); // Try all '?' as '1'

            // If either version can be sorted into "000...111", it's a YES
            if (canBeSorted(minQuery) || canBeSorted(maxQuery)) {
                result.add("YES");
            } else {
                result.add("NO");
            }
        }

        return result;
    }

    public static void main(String[] args) {
        String binary = "101";
        String[] arr = {"1?1", "0??", "110", "0?1"};

        List<String> results = checkQueries(binary, arr);
        for (String res : results) {
            System.out.println(res);
        }
    }
}
