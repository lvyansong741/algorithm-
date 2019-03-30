#### 题目描述 
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。
#### 1 暴力解法 
```
class Solution {
public:
    void reOrderArray(vector<int> &array) {
        if(&array==NULL) return;
        for(int i=0;i<array.size();i++){
            if ((array[i]&1)==0){
                int j=i+1;
                while((array[j]&1)==0  && j<array.size()){
                    j++;
                }
                if (j<array.size()){
                   int tmp=array[j];
                    for (int t=j;t>i;t--){
                        array[t]=array[t-1];
                    }
                    array[i]=tmp; 
                } else {
                    return ;
                }
            }
        }
    }
};
    
```
    
#### 2 直接将偶数删除 然后插入尾部。 


```
class Solution {
public:
    void reOrderArray(vector<int> &array) {
        //if(&array==NULL) return;
        int lenth=array.size();
        vector<int>::iterator iter1;
        iter1=array.begin();
        while (lenth){
            if ((*iter1&0x1)==0){
                int tmp=*iter1;
                //下面两行换个顺序会有bug，我也不知道为啥
                iter1=array.erase(iter1);
                array.push_back(tmp);
            } else {
                iter1++;
            }
            lenth--;
        }
  
    }
};
```
