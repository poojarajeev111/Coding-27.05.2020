
#include <bits/stdc++.h> 
using namespace std; 
  
vector<bool> prime(1000001, true); 
void sieve() 
{ 
    prime[0] = prime[1] = false; 
  
    for (long long i = 2; i * i <= 1000000; i++) { 
  
        if (prime[i]) { 
            for (long long j = i * i; j <= 1000000; j += i) 
                prime[j] = false; 
        } 
    } 
} 
  
int findNumber(int n) 
{ 
    vector<int> v; 
    bool flag = false; 
  
    int num; 
  
    for (num = n; num >= 1; num--) { 
  
        int x = num; 
        v.clear(); 
  
        while (x != 0) { 
            v.push_back(x % 10); 
  
            x /= 10; 
        } 
  
        sort(v.begin(), v.end()); 
        while (1) { 
            long long w = 0; 
 
            for (auto u : v) 
                w = w * 10 + u; 
  
            if (prime[w]) { 
  
                flag = true; 
                break; 
            } 
  
            if (flag) 
                break; 
  
            if (!next_permutation(v.begin(), v.end())) 
                break; 
        } 
  
        if (flag) 
            break; 
    } 
  
    return num; 
} 
 
int main() 
{ 
    sieve(); 
  
    int n = 99; 
    cout << findNumber(n) << endl; 
  
    n = 84896; 
    cout << findNumber(n) << endl; 
  
    return 0; 
} 
