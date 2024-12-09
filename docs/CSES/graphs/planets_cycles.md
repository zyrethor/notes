# Planets Cycles

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

  int n;
  cin >> n;
  vector<int> t(n+1);
  for (int i = 1; i <= n; i++)  {
    cin >> t[i];
  }

  // 0=unvisited, 1=visiting, 2=done
  vector<int> state(n+1, 0);
  vector<int> ans(n+1, 0);
  vector<bool> inCycle(n+1, false);

  function<void(int)> dfs = [&](int u) {
    state[u] = 1;
    int to = t[u];

    if (state[to] == 0) {
      dfs(to);
    } else if (state[to] == 1) {
      int cur = to;
      int cycle_len = 0;

      do {
        cur = t[cur];
        cycle_len++;
      } while (cur != to);

      cur = to;
      do {
        inCycle[cur] = true;
        ans[cur] = cycle_len;
        cur = t[cur];
      } while (cur != to);
    }

    state[u] = 2;
  };

  for (int i = 1; i <= n; i++) {
    if (state[i] == 0) {
      dfs(i);
    }
  }

  function<int(int)> calcAns = [&](int u) -> int {
    if (ans[u] != 0) return ans[u];

    ans[u] = 1 + calcAns(t[u]);
    return ans[u];
  };

  for (int i = 1; i <= n; i++) {
    if (!inCycle[i] && ans[i] == 0)
      calcAns(i);
  }

  for (int i = 1; i <= n; i++) {
    cout << ans[i] << (i == n ? "\n" : " ");
  }

  return 0;
}
```

