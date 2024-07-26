# Text Justification :-

[Problem Link] :--- (https://leetcode.com/problems/text-justification/description/)

<h3>
Given an array of strings words and a width maxWidth, format the text such that each line has exactly maxWidth characters and is fully (left and right) justified.
<br>
You should pack your words in a greedy approach; that is, pack as many words as you can in each line. Pad extra spaces ' ' when necessary so that each line has exactly maxWidth characters.
<br>
Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line does not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right.
<br>
For the last line of text, it should be left-justified, and no extra space is inserted between words.
<br>
Note:
<br>
A word is defined as a character sequence consisting of non-space characters only.<br>
Each word's length is guaranteed to be greater than 0 and not exceed maxWidth.<br>
The input array words contains at least one word.<br><br>
Example 1:

Input: words = ["This", "is", "an", "example", "of", "text", "justification."], maxWidth = 16
Output:
[
   "This    is    an",
   "example  of text",
   "justification.  "
]<br><br>
Example 2:

Input: words = ["What","must","be","acknowledgment","shall","be"], maxWidth = 16
Output:
[
  "What   must   be",
  "acknowledgment  ",
  "shall be        "
]
Explanation: Note that the last line is "shall be    " instead of "shall     be", because the last line must be left-justified instead of fully-justified.
Note that the second line is also left-justified because it contains only one word.<br><br>
Example 3:

Input: words = ["Science","is","what","we","understand","well","enough","to","explain","to","a","computer.","Art","is","everything","else","we","do"], maxWidth = 20
Output:
[
  "Science  is  what we",
  "understand      well",
  "enough to explain to",
  "a  computer.  Art is",
  "everything  else  we",
  "do                  "
]<br><br>
 
Constraints:
<br>
1 <= words.length <= 300<br>
1 <= words[i].length <= 20<br>
words[i] consists of only English letters and symbols.<br>
1 <= maxWidth <= 100<br>
words[i].length <= maxWidth<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    vector<string> fullJustify(vector<string>& words, int maxWidth) {
        int nows = 0;
        int newLen = 0;
        int mainLen = words.size();
        vector<string> updatedStrings;
        for(int i = 0; i < mainLen; i++){
            newLen = newLen + words[i].size();
            nows++;
            
            if(newLen + (nows-1) <= maxWidth){
                if(i == (mainLen - 1)){
                    string s = "";
                    for(int k = 0; k < nows; k++){
                        s += words[i - (nows - 1) + k];
                        if(k < (nows-1)) s += " ";
                    }
                    for(int l = s.size(); l < maxWidth; l++)
                        s += " ";
                
                    updatedStrings.push_back(s);
                    break;
                }
                else 
                    continue;
            }
            else{
                nows--;
                int spaces = maxWidth - (newLen - words[i].size());
                int ws = spaces, extra=0;
                string s1 = "";
                string s2 = "";
                if(nows > 1){
                    ws = spaces/(nows - 1);
                    extra = spaces%(nows - 1); 
                }
                for(int k = 0; k < ws; k++){
                        s2 += " ";
                }
                if(nows == 1){
                    s1 += words[i - 1];
                    s1 += s2;
                }
                else{
                    for(int j = 0; j < nows - 1; j++){
                        s1 += words[i - nows + j];
                        s1 += s2;
                        if(extra){
                            s1 += " ";  
                            extra--;
                        }                       
                    }
                    s1 += words[i - 1];
                }
                
                updatedStrings.push_back(s1);
                newLen = 0;
                nows = 0;
                
            }
            i -= 1;
        }
        return updatedStrings;
    }
};

```
