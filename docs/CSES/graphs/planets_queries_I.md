# Planets Queries I

Binary Lifting O(logk)

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

  int n, q;
  cin >> n >> q;
  vector<int> t(n+1);
  for (int i = 1; i <= n; i++)  {
    cin >> t[i];
  }

  int LOG = 30;

  // up[j][i] = 2^j th step from i
  vector<vector<int>> up(LOG, vector<int>(n+1));
  for (int i = 1; i <= n; i++) {
    up[0][i] = t[i];
  }

  for (int j = 1; j < LOG; j++) {
    for (int i = 1; i <= n; i++) {
      up[j][i] = up[j-1][up[j-1][i]];
    }
  }

  while (q--) {
    int x, k;
    cin >> x >> k;
    int cur = x;
    for (int j = 0; j < LOG; j++) {
      if (k & (1 << j)) {
        cur = up[j][cur];
      }
    }
    cout << cur << "\n";
  }

  return 0;
}
```

