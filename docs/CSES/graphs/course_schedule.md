# Course Schedule

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

  int n, m;
  cin >> n >> m;
  int a, b;

  vector<vector<int>> adj(n+1);
  vector<int> in_degree(n+1);
  for (int i = 0; i < m; i++) {
    cin >> a >> b;
    adj[a].pb(b);
    in_degree[b]++;
  }

  queue<int> q;
  for (int i = 1; i <= n; i++) {
    if (in_degree[i] == 0)
      q.push(i);
  }

  vector<int> ans;
  while (!q.empty()) {
    int u = q.front();
    q.pop();

    ans.pb(u);
    for (auto & to : adj[u]) {
      in_degree[to]--;
      if (in_degree[to] == 0)
        q.push(to);
    }
  }

  int len = ans.size();
  if (len == n) {
    for (int i = 0; i < len; i++) {
      cout << ans[i] << (i == len-1 ? "\n" : " ");
    }
  }
  else {
    cout << "IMPOSSIBLE";
  }

  return 0;
}
```

