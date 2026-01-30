## Reverse The Array

    void reverseArray(vector<int> &arr , int m) {
    // Write your code here   
    int end=arr.size()-1;
    int st=m+1;
     while(st<=end){
        swap(arr[st],arr[end]);
        st++;
        end--;
     }
    }