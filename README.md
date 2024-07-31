# Filing-bookcase-shelves
class Solution {
    public int minHeightShelves(int[][] books, int shelfWidth) {
             int n = books.length;
        int[] dp = new int[n + 1];
        dp[0] = 0; // Base case: no books, no height

        for (int i = 1; i <= n; i++) {
            int width = 0;
            int height = 0;
            dp[i] = Integer.MAX_VALUE;
            // Try to place books[j...i-1] on the current shelf
            for (int j = i - 1; j >= 0; j--) {
                width += books[j][0];
                if (width > shelfWidth) break; // Exceeding the shelf width
                height = Math.max(height, books[j][1]);
                dp[i] = Math.min(dp[i], dp[j] + height);
            }
        }
        return dp[n];
    }
} 
