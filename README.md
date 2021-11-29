# Lightest Google
機能最小限で，最軽量のGoogle検索サイト．
スマホの通信制限下でも，最低限の調べ物ができるように作りました．
Google 検索結果のスニペットを10件出すだけ.


サイトURL 👉 https://lunain84.github.io/LightestGoogle/

# 検証動画
https://user-images.githubusercontent.com/52437973/143797729-52dc7adb-0fd6-4f3d-9578-10acf7bc7b84.MOV

Xcode の低速シミュレーションでは，

|                 | Downlink | Uplink | 
| --------------- | -------- | ------ | 
| Bandwidth       | 1 mbps   | 1 mbps | 
| Packets Dropped | 10 %     | 10 %   | 
| Delay           | 500  ms  | 500  ms| 

という条件下で，
通常ブラウジングでは検索結果の表示まで約10秒かかったのに対し，Lightest Google を使用した時は3.5秒まで短縮しました．
