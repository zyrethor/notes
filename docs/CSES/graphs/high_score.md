# High Score

## Code

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pb push_back


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
  vector<vector<int>> adj(n+1, vector<int>());
  vector<vector<int>> rv_adj(n+1, vector<int>());

  // adj list
  for (int i = 0; i < m; i++) {
    cin >> ed[i].a >> ed[i].b >> ed[i].w;
    adj[ed[i].a].pb(ed[i].b);
    rv_adj[ed[i].b].pb(ed[i].a);
  }
  
  // bfs
  queue<int> q;
  
  vector<bool> reach_from_start(n+1, false);
  q.push(1);
  reach_from_start[1] = true;
  while (!q.empty()) {
    int v = q.front();
    q.pop();

    for (auto& to : adj[v]) {
      if (!reach_from_start[to]) {
        reach_from_start[to] = true;
        q.push(to);
      }
    }
  }

  vector<bool> reach_to_end(n+1, false);
  q.push(n);
  reach_to_end[n] = true;
  while (!q.empty()) {
    int v = q.front();
    q.pop();

    for (auto& to : rv_adj[v]) {
      if (!reach_to_end[to]) {
        reach_to_end[to] = true;
        q.push(to);
      }
    }
  }

  vector<int> relevant(n+1, false);
  for (int v = 1; v <= n; v++) {
    if (reach_from_start[v] && reach_to_end[v])
      relevant[v] = true;
  }

  // dp
  const ll NEG_INF = -1e18;
  vector<ll> dp(n+1, NEG_INF);
  dp[1] = 0;
  for (int i = 1; i <= n-1; i++) {
    bool updated = false;

    for (auto& e : ed) {
      if (relevant[e.a] && relevant[e.b]) {
        if (dp[e.a] != NEG_INF && dp[e.b] < dp[e.a] + e.w) {
          dp[e.b] = dp[e.a] + e.w;
          updated = true;
        }
      }
    }

    if (!updated)
      break;
  }

  bool has_cycle = false;
  for (auto& e : ed) {
    if (relevant[e.a] && relevant[e.b]) {
      if (dp[e.a] != NEG_INF && dp[e.b] < dp[e.a] + e.w) {
        has_cycle = true;
        break;
      }
    }
  }

  if (has_cycle)
    cout << "-1\n";
  else
    cout << dp[n] << "\n";


  return 0;
}
```
