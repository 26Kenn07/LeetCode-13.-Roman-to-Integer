# LeetCode-13.-Roman-to-Integer

class Solution:
    def romanToInt(self, s: str) -> int:
        num_rom = {'I':1,'V':5,'X':10,'L':50,'C':100,'D':500,'M':1000} #creating a dictionary with default values
        len_s = len(s)
        rslt = 0
        flag = 0
        for i in range(len_s): #loop
            sp_case = 0 #for 4,40,400,9,90,900 cases
            if(flag != 0): #flag to break a iteration after special case
                flag = 0
                continue
            if (i != len_s - 1) and (num_rom[s[i]] < num_rom[s[i+1]]): #condition for special case
                sp_case = num_rom[s[i+1]] - num_rom[s[i]]
                rslt = rslt + sp_case
                flag = 1
            else:
                rslt = rslt + num_rom[s[i]] #resultant number 
        return rslt
