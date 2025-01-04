# leetcode--1930
Unique Length-3 Palindromic Subsequences
//code in java
import java.util.HashSet;
import java.util.Set;

public class Solution {
    public int countPalindromicSubsequence(String s) {
        int n = s.length();
        int[] left = new int[26];
        int[] right = new int[26];
        Set<String> palindromes = new HashSet<>();

        for (int i = 0; i < n; i++) {
            right[s.charAt(i) - 'a']++;
        }

        for (int i = 0; i < n; i++) {
            right[s.charAt(i) - 'a']--;
            for (char c = 'a'; c <= 'z'; c++) {
                if (left[c - 'a'] > 0 && right[c - 'a'] > 0) {
                    palindromes.add(c + "" + s.charAt(i) + c);
                }
            }
            left[s.charAt(i) - 'a']++;
        }

        return palindromes.size();
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        String s = "aabca";
        System.out.println(solution.countPalindromicSubsequence(s)); // Output: 3
    }
}

