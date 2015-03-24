# CSND_black_githun
CSND black github

//
//  main.cpp
//  unforget
//
//  Created by apple on 15/3/11.
//  Copyright (c) 2015年 apple. All rights reserved.
//

#include <iostream>
#include <vector>
using namespace std;
int max(int a, int b)
{
    return a>=b?a:b;
}
int Memoized_cut_rod_aux(int p[],int n,int r[])
{
    
    if(r[n]>=0)
        return r[n];
    int q;
    if(0 == n)
        q = 0;
    else
    {
        q = -10000;
        for(int i = 1;i<=n; i++)
        {
            q = max(q,p[i]+Memoized_cut_rod_aux(p, n-i, r));
        }
        
    }
    r[n] = q;
    return q;
}
int BOTTOM_UP_CUT_ROD(int p[], int n, int r[])
{
    r[0]=0;
    int q;
    for(int j=1; j<=n; j++)
    {
        q = -1;
        for (int i=1; i<=j; i++) {
            q = max(q, p[i]+r[j-i]);
        }
        r[j] = q;
    }
    return r[n];
}


int main(int argc, const char * argv[]) {
    int p[11]={0,1,5,8,9,10,17,17,20,24,30};
    int r[11];
    for (int i=0; i<11; i++) {
        r[i] = -1000000;
    }
    cout<< BOTTOM_UP_CUT_ROD(p,10,r);
    return 0;
}
