//brut force
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {

        vector<int>ans; 
        int maxi; 
      for(int i=0; i<nums.size()-k+1; i++){
          maxi=INT_MIN;

          for(int j=i; j<i+k ; j++){

            maxi = max(nums[j], maxi); 
          }

        ans.push_back(maxi); 
      }   

      return ans; 
    }
};


//final approach

class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {

        int size = nums.size() ;

        int i = 0 ;
        int j = 0 ;    

        vector< int >ans ;

        list< int > q ;

        while ( j < size ){

            while( !q.empty()  &&  q.back() < nums[ j ] )
               q.pop_back() ;
        
            q.push_back( nums[ j ] ) ;

            if( j - i + 1 < k )
               j++ ;

            else if ( j - i + 1 == k ){

               ans.push_back( q.front() ) ;

               if( q.front() == nums[ i ] )
                   q.pop_front() ;
                
                i++ ; 
                j++ ;
            }  
        }

        return ans ;
        
    }
};
