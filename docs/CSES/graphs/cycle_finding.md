# Cycle Finding

## Code

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pb push_back
const ll INF = 1e18;


int main() {
  ios_base::sync_with_stdio(false);
  cin.tie(nullptr);

  int n, m;
  cin >> n >> m;

  struct Edge {
    int a, b;
    ll w;
  };

  vector<Edge> ed(m);

  for (int i = 0; i < m; i++) {
    cin >> ed[i].a >> ed[i].b >> ed[i].w;
  }

  
  vector<ll> dist(n+1, 0);
  vector<int> pred(n+1, -1);
  dist[0] = 0;
  int x = -1;

  for (int i= 1; i <= n; i++) {
    x = -1;
    for (auto& e : ed) {
      if (dist[e.b] > dist[e.a] + e.w) {
        dist[e.b] = dist[e.a] + e.w;
        pred[e.b] = e.a;
        x = e.b;
      }
    }
  }
 
  if (x == -1) {
    cout << "NO\n";
    return 0;
  }

  for (int i = 0; i < n; i++) {
    x = pred[x];
  }

  int start = x;
  vector<int> cycle;
  cycle.pb(start);
  x = pred[start];
  while (x != start) {
    cycle.pb(x);
    x = pred[x];
  }

  cycle.pb(start);
  reverse(cycle.begin(), cycle.end());
  cout << "YES\n";
  int len = cycle.size();
  for (int i = 0; i < len; i++) {
    cout << cycle[i] << (i == len - 1 ? "\n" : " ");
  }


  return 0;
}
```
