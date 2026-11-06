---
title: "AtCoder ABC482_c"
date: 2026-11-02
categories: [AtCoder]
---

### AtCoder ABC482 c번 문제 해설입니다.

[AtCoder ABC482_c  문제원문](https://atcoder.jp/contests/abc482/tasks/abc482_c)
<br>

문제를 읽어보면 질의한 구간안에 있는 점의 개수를 출력하면 되는 문제입니다. ( x~x 와 같은 점 하나 구간에서도 여러 점이 있을 수 있다는 것이 조금 함정입니다)<br><br>

해설하자면 질의하는 구간은 너비와 높이가 따로이고 서로 관련이 없기 떄문에 따로 저장해서 관리하면 됩니다. 그리고 그 두 배열에 점들을 저장해두고 정렬하면 이분탐색을 사용할 수 있습니다.<br>
여기서 제가 몰랐던 트릭이 있는데 한 점을 이분탐색해서 찾을 인덱스가 그 이전에 있던 점들의 개수로 볼 수 있어서 구간에 있는 점들의 개수를 알 수 있습니다.
<br><br><br><br><br>

아래는 정답 코드입니다.
<br>

``` cpp
#include <bits/stdc++.h>
using namespace std;

int main(void){
        ios::sync_with_stdio(0);
        cin.tie(0);

        int h, w, n, q;

        int a, b;
        vector<int> x, y;

        cin >> h >> w >> n >> q;


        for(int i = 0 ; i < n ; i++){
                cin >> a >> b;
                x.push_back(a);
                y.push_back(b);
        }

        sort(x.begin(), x.end());
        sort(y.begin(), y.end());

        int t;
        int ans;
        for(int i = 0 ; i < q ; i++){
                cin >> t >> a >> b;

                //여기서 upper_bound 와 lower_bound를 사용해야 중복점을 처리할 수 있습니다. (생각할 거리~)
                if(t == 1) ans = upper_bound(x.begin(), x.end(), b) - lower_bound(x.begin(), x.end(), a);
                if(t == 2) ans = upper_bound(y.begin(), y.end(), b) - lower_bound(y.begin(), y.end(), a);

                cout << ans+1 << endl;
        }

        return 0;
}
```
<br>

여담<br>
구현 트릭하나 배웠다. 야호~<br>
그리고 잘하는 친구 보니까 cin을 써야 코드가 짧다는 말이 있더라고요 한번 써봤는데 이것도 익숙해져야겠어요.<br>
마지막으로 여기까지 보는 거면 저 위에 생각할 거리나 다시 생각해봅시다.