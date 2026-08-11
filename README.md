# Peak-Element

class Solution {
    public int peakElement(int[] arr) {
        int n = arr.length;
        
        // Single element case
        if (n == 1) return 0;
        
        // Check boundary elements
        if (arr[0] > arr[1]) return 0;
        if (arr[n - 1] > arr[n - 2]) return n - 1;
        
        int low = 1, high = n - 2;
        
        while (low <= high) {
            int mid = low + (high - low) / 2;
            
            // Check if mid is a peak
            if (arr[mid] > arr[mid - 1] && arr[mid] > arr[mid + 1]) {
                return mid;
            }
            
            // If right neighbor is greater, a peak must lie on the right
            if (arr[mid] < arr[mid + 1]) {
                low = mid + 1;
            } else { // Otherwise, a peak lies on the left
                high = mid - 1;
            }
        }
        
        return 0;
    }
}
