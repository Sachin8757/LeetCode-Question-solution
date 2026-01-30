##  Move Zeroes long method
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

## Short Method
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
