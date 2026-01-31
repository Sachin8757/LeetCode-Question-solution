# Leetcode Question
# Peak Index in a Mountain Array
#### Using Leniar Search

    int peakIndexInMountainArray(vector<int>& arr) {
      int ans=-1;
       int mountain =INT_MIN;

       for(int i=0;i<arr.size();i++){
           if(arr[i]>mountain){
               mountain=arr[i];
               ans=i;
            }
        }
            return ans;
     }

#### Using Binary Search

    int peakIndexInMountainArray(vector<int>& arr) {
        int s=0;
        int e=arr.size()-1;
        int mid=s+(e-s)/2;
        while(s<e){
            if(arr[mid]<arr[mid+1]){
                s=mid+1;
            }else{
                e=mid;
            }
            mid=s+(e-s)/2;
        }
        return s;

    }
    
# Mearge sorted Array
    class Solution {
    public:
        void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
            int j=0;
            for(int i=0;i<nums1.size()&& n>=1;i++){

                if(nums1[i]==0){
                    nums1[i]=nums2[j];
                    j++;
                    n--;
                }
            }
            sort(nums1.begin(),nums1.end());

        }
    };

#  Move Zeroes long method
#### Long Method
    class Solution {
        public:
        void moveZeroes(vector<int>& nums) {
            if(nums.size()==1){
               return ;
            }

                for(int i=0;i<nums.size();i++){
                 for(int j=i+1;j<nums.size();j++){
                    if(nums[i]==0 && nums[j]!=0){
                        swap(nums[i],nums[j]);
                       break;
                    }
                  }
                }
        }
    };

#### Short Method
            class Solution {
            public:
                void moveZeroes(vector<int>& nums) {
                    int i=0;
                    for(int j=0;j<nums.size();j++){
                        if(nums[j]!=0){
                            swap(nums[i],nums[j]);
                            i++;
                        }
                    }
                    
                }
            };


# Reverse The Array

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

# Rotated Array

    class Solution {
    public:
        void rotate(vector<int>& nums, int k) {
            vector<int>temp(nums.size());

            for(int i=0;i<nums.size();i++){
                temp[(i+k)%nums.size()]=nums[i];
            }
            nums=temp;
        }
    };


# Search In Rotated Sorted Array

#### Using Binary Search

    int pvoit(vector<int>&nums){
        int s=0;
        int e=nums.size()-1;
        int mid=s+(e-s)/2;

        while(s<e){
            if(nums[mid]>=nums[0]){
                s=mid+1;
            }else{
                e=mid;
            }
            mid=s+(e-s)/2;
        }
        return s;
    }
    int binarysearch(vector<int>&nums,int k,int s,int e){
        int mid=s+(e-s)/2;
        while(s<=e){

            if(nums[mid]==k){
                return mid;
            }else if(k>nums[mid]){
                s=mid+1;
            }else{
                e=mid-1;
            }
            mid=s+(e-s)/2;
        }
        return -1;
    }
    int search(vector<int>& nums, int n, int k)
    {
    int mid=pvoit(nums);
    if(k>=nums[mid]&&k<=nums[n-1]){
        return binarysearch(nums,k,mid,n-1);
    }else{
        return binarysearch(nums,k,0,mid-1);
    }
    }


#### Using Leniar Search

    int search(vector<int>& nums, int n, int k){
      for(int i=0;i<nums.size();i++){
       if(nums[i]==k){
           return i;
       }
      }
     return -1;
    }

# Most Frequent Characte
        char getMaxOccuringChar(char* str) {
        // code here
        char ch[26]={0};
        
        for(int i=0;str[i]!='\0';i++){
            char c=str[i];
            ch[c-'a']++;
        }
        
        int ind=0;
        int value=-1;
        
        for(int i=0;i<26;i++){
            if(ch[i]>value){
                ind=i;
                value=ch[i];
            }
        }
        return ind+ 'a'; 
    }