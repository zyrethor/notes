# Flight Discount

## Code

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pb push_back
#define pii pair<int, int>
#define tp tuple<ll, int, int>

const ll INF = 1e18;

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);

  int n, m;
  cin >> n >> m;
  int a, b, c;

  vector<vector<pii>> adj(n+1);
  for (int i = 0; i < m; i++) {
    cin >> a >> b >> c;
    adj[a].emplace_back(b, c);
  }

  vector<ll> d0(n+1, INF);
  vector<ll> d1(n+1, INF);
  d0[1] = 0;

  // pq<cost, node, state>
  priority_queue<tp, vector<tp>, greater<tp>> pq;
  pq.emplace(0, 1, 0);
  while (!pq.empty()) {
    auto [cost, v, state] = pq.top();
    pq.pop();

    if (state == 0 && cost > d0[v]) continue;
    if (state == 1 && cost > d1[v]) continue;

    for (auto& [to, weight] : adj[v]) {
      ll w = (ll)weight;
      if (state == 0) {
        if (d0[to] > d0[v] + w) {
          d0[to] = d0[v] + w;
          pq.emplace(d0[to], to, 0);
        }

        ll new_cost = d0[v] + w / 2;
        if (d1[to] > new_cost) {
          d1[to] = new_cost;
          pq.emplace(d1[to], to, 1);
        }
      }
      else {
        if (d1[to] > d1[v] + w) {
          d1[to] = d1[v] + w;
          pq.emplace(d1[to], to, 1);
        }

      }
    }
  }
  
  cout << min(d0[n], d1[n]);

  return 0;
}
```

