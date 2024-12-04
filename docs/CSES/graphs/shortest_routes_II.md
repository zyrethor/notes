# Shortest Routes II

## Code

```c++
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define pii pair<ll, int>
#define INF 1e18

ll dist_mat[505][505];

int main() {
  ios::sync_with_stdio(false);
  cin.tie(NULL);
  int n, m, q;
  cin >> n >> m >> q;
  for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= n; j++) {
      dist_mat[i][j] = (i == j ? 0 : INF);
    }
  }

  int a, b;
  ll c;
  for (int i = 0; i < m; i++) {
    cin >> a >> b >> c;
    if (c < dist_mat[a][b]) {
      dist_mat[a][b] = c;
      dist_mat[b][a] = c;
    }
  }

  for (int k = 1; k <= n; k++) {
    for (int i = 1; i <= n; i++) {
      if (dist_mat[i][k] == INF)
        continue;
      for (int j = 1; j <= n; j++) {
        if (dist_mat[k][j] == INF)
          continue;

        if (dist_mat[i][j] > dist_mat[i][k] + dist_mat[k][j])
          dist_mat[i][j] = dist_mat[i][k] + dist_mat[k][j];
      }
    }
  }

  while (q--) {
    cin >> a >> b;
    if (dist_mat[a][b] < INF) {
      cout << dist_mat[a][b] << "\n";
    }
    else {
      cout << "-1\n";
    }
  }

  return 0;
}
```
