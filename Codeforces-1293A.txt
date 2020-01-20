#include <iostream>
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
bool BinarySearch(ll a[], ll k, ll s)
{
    bool ok = false;
    int f = 0;
    int last = k;
    while(f < last)
    {
        int mid = (f+last)/2;
        if(a[mid] == s)
        {
            return false;
        }
        else if(a[mid] > s)
        {
            last = mid;
        }
        else
        {
            f = mid+1;
        }
    }
    return true;
}
int main()
{
   int t;
   cin >> t;
   while(t--)
   {
       ll n, s, k;
       cin >> n >> s >> k;
       ll ar[k+5] = {};
       for(int i = 0; i < k; i++)
       {
           cin >> ar[i];
       }
       sort(ar, ar+k);
       ll ForWord = 0;
       ll start = s;
       while(BinarySearch(ar, k, start) == false)
       {
           start++;
           //cout << start << endl;
       }
       if(start <= n)
       {
           ForWord = start;
       }
       else
       {
           ForWord = 999999999999999;
       }
       //cout << ForWord << endl;
       ll BackWord = 0;
       start = s-1;
       while(BinarySearch(ar, k, start) == false)
       {
           start--;
       }
       if(start >= 1)
       {
           BackWord = start;
       }
       else
       {
           BackWord = 999999999999999;
       }
       //cout <<
       cout << min(abs(ForWord-s), abs(BackWord-s)) << endl;
   }
    return 0;
}
