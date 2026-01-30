##  Move Zeroes
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