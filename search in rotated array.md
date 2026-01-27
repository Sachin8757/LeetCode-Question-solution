## Search In Rotated Sorted Array

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


### Using Leniar Search

    int search(vector<int>& nums, int n, int k){
      for(int i=0;i<nums.size();i++){
       if(nums[i]==k){
           return i;
       }
      }
     return -1;
    }
