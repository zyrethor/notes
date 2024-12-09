# Investigation

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pb emplace_back
#define pii pair<ll, int>
const int MOD = 1e9+7;
const ll INF = 1e18;


int main() {
  ios_base::sync_with_stdio(false);
  cin.tie(nullptr);

  int n, m;
  cin >> n >> m;
  int a, b, w;

  vector<vector<pair<int, int>>> adj(n+1);
  for (int i = 0; i < m; i++) {
    cin >> a >> b >> w;
    adj[a].pb(b, w);
  }

  vector<ll> dist(n+1, INF);
  vector<ll> ways(n+1, 0);
  vector<int> min_flights(n+1, 1e9);
  vector<int> max_flights(n+1, 0);

  dist[1] = 0;
  ways[1] = 1;
  min_flights[1] = 0;
  max_flights[1] = 0;

  priority_queue<pii, vector<pii>, greater<pii>> pq;
  pq.emplace(0, 1);

  while (!pq.empty()) {
    auto [cur_dist, u] = pq.top();
    pq.pop();

    if (cur_dist > dist[u]) continue;

    for (auto& [to, w] : adj[u]) {
      if (dist[to] > dist[u] + w) {
        dist[to] = dist[u] + w;
        ways[to] = ways[u];
        min_flights[to] = min_flights[u] + 1;
        max_flights[to] = max_flights[u] + 1;
        pq.emplace(dist[to], to);
      }
      else if (dist[to] == dist[u] + w) {
        ways[to] = (ways[to] + ways[u]) % MOD;
        min_flights[to] = min(min_flights[to], min_flights[u] + 1);
        max_flights[to] = max(max_flights[to], max_flights[u] + 1);
      }
    }
  }

  cout << dist[n] << " " << ways[n] << " " << min_flights[n] << " " << max_flights[n];

  return 0;
}
```

