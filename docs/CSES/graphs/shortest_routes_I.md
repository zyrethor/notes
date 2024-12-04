# Shortest Routes I

## Code

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pii pair<ll, int>

int main() {
  ios::sync_with_stdio(false);
  cin.tie(NULL);
  int n, m;
  cin >> n >> m;
  vector<vector<pair<int, ll>>> adj(n + 1);
  for (int i = 0; i < m; i++) {
    int a, b;
    ll c;
    cin >> a >> b >> c;
    adj[a].emplace_back(b, c);
  }

  vector<ll> dist(n+1, 1e18);
  dist[1] = 0;
  priority_queue<pii, vector<pii>, greater<pii>> pq;
  pq.emplace(0, 1);

  while (!pq.empty()) {
    auto [cur_dist, u] = pq.top();
    pq.pop();

    if (cur_dist > dist[u])
      continue;

    for (auto& [v, w] : adj[u]) {
      if (dist[v] > dist[u] + w) {
        dist[v] = dist[u] + w;
        pq.emplace(dist[v], v);
      }
    }
  }

  for (int i = 1; i <= n; i++) {
    cout << dist[i] << (i == n ? "\n" : " ");
  }
}
```
