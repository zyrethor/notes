# Flight Routes

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pb emplace_back
#define pii pair<ll, int>
const ll INF = 1e18;


int main() {
  ios_base::sync_with_stdio(false);
  cin.tie(nullptr);

  int n, m, k;
  cin >> n >> m >> k;
  int a, b;
  ll c;

  vector<vector<pair<int, ll>>> adj(n+1);
  for (int i = 0; i < m; i++) {
    cin >> a >> b >> c;
    adj[a].emplace_back(b, c);
  }

  vector<int> count(n+1, 0);
  vector<ll> ans;
  priority_queue<pii, vector<pii>, greater<pii>> pq;
  pq.emplace(0, 1);

  while (!pq.empty()) {
    auto [cost, u] = pq.top();
    pq.pop();

    if (count[u] >= k)
      continue;

    count[u]++;

    if (u == n) {
      ans.pb(cost);
      if ((int)ans.size() == k)
        break;
    }

    for (auto& [to, w] : adj[u]) {
      if (count[to] < k)
        pq.emplace(cost + w, to);
    }

  }

  for (int i = 0; i < k; i++) {
    cout << ans[i] << (i == k-1 ? "\n" : " ");
  }

  return 0;
}
```

