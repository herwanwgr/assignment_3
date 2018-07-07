class GFG {
     
    // Function to Find Maximum Number
    static int findMaxSegment(String s, int k) {
     
        // Maximum segment length
        int seg_len = s.length() - k;
     
        // Find value of first segment of seg_len
        int res = 0;
         
        for (int i = 0; i < seg_len; i++)
            res = res * 10 + (s.charAt(i) - '0');
     
        // Find value of remaining segments using 
        // sliding window
        int seg_len_pow = (int)Math.pow(10,
                                    seg_len - 1);
        int curr_val = res;
         
        for (int i = 1; 
             i <= (s.length() - seg_len); i++) {
     
            // To find value of current segment, 
            // first remove leading digit from 
            // previous value
            curr_val = curr_val - 
            (s.charAt(i - 1) - '0') * seg_len_pow;
         
            // Then add trailing digit
            curr_val = curr_val * 10 + 
               (s.charAt(i + seg_len - 1) - '0');
         
            res = Math.max(res, curr_val);
        }
         
        return res;
    }
     
    // Driver code
    public static void main(String[] args) {
         
        String s = "30045";
        int k = 2;
         
        System.out.print("Maximum number = "
                        + findMaxSegment(s, k));
    }
}