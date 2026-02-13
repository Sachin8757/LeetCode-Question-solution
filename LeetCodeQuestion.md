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

# Plus One
    class Solution {
    public:
        vector<int> plusOne(vector<int>& digits) {
            int i=digits.size()-1;
            vector<int> ans;
            int carray=1;
            for(int i=digits.size()-1;i>=0;i--){
                int sum=carray+digits[i];
                ans.push_back(sum%10);
                carray=sum/10;
            }
            if (carray == 1) {
                ans.push_back(1);
            }
            reverse(ans.begin(),ans.end());
            return ans;

        }
    };

# Add Binary

    class Solution {
    public:
        string addBinary(string a, string b) {
            string ans = "";
            int i = a.length() - 1;
            int j = b.length() - 1;
            int carry = 0;
            while (i >= 0 || j >= 0 || carry) {
                int sum = carry;
                if (i >= 0) sum += a[i--] - '0';
                if (j >= 0) sum += b[j--] - '0';
                ans.push_back((sum % 2) + '0');
                carry = sum / 2;
            }
            reverse(ans.begin(), ans.end());
            return ans;
        }
    };

#  Add to Array-Form of Integer

    class Solution {
    public:
        vector<int> addToArrayForm(vector<int>& num, int k) {
            int i = num.size() - 1;
            int carry = k;

            while (i >= 0 || carry > 0) {
                if (i >= 0) {
                    carry += num[i];
                    num[i] = carry % 10;
                    carry /= 10;
                    i--;
                } else {
                    num.insert(num.begin(), carry % 10);
                    carry /= 10;
                }
            }

            return num;
        }
    };

# Subsequences of String

    void solve(string str,vector<string>& ans,string op,int ind){
        if(ind>=str.length()){
            if(op.length()>0){
                ans.push_back(op);
            }
            return;
        }
        //exclude
        solve(str,ans,op,ind+1);

        //include 
        char ch=str[ind];
        op.push_back(ch);
        solve(str,ans,op,ind+1);

        return ;
    }
    vector<string> subsequences(string str){
        vector<string>ans;
        string op;
        int ind=0;
        solve(str,ans,op,ind);
        return ans;
        
    }

# subset Array
    class Solution {
        private:
        void solve(vector<int>nums,vector<vector<int>>& ans,vector<int>op,int ind){
            if(ind>=nums.size()){
                ans.push_back(op);
                return ;
            }

            //exclude
            solve(nums,ans,op,ind+1);

            //include

            int ele=nums[ind];
            op.push_back(ele);
            solve(nums,ans,op,ind+1);
        }
    public:
        vector<vector<int>> subsets(vector<int>& nums) {
            vector<vector<int>> ans;
            vector<int>op;
            int ind=0;
            solve(nums,ans,op,ind);
            return ans;
        }
    };