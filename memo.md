・Client-Side Navigation
自動でコード分割するから、必要なページだけのコードをロードする事が出来る。  
ただ、リンク先のページなどは事前にバックグランドでロードする(プリフェッチ)  
ことにより、別ページにリンクした際も、サーバーと通信せずに、ページ遷移が可能。

・静的な画像やアセットは public に保存する

・Next.js では、事前に全てのページを Pre-Render している。
→ ブラウザの負荷を下げて、サーバー側で HTML を組み立てる。
・通常の React は、クライアントサイドレンダリングしている。
※ リクエストがあってから、HTML を組み立てている。
→ SEO 的に、クローラーが組み立てる前のページを見にきているので、
空っぽのページを誤認する。

・PreRendering の違い
ブラウザで JS を無効化した状態で、
Next.js のページをリロードすると、サーバーで HTML を組み立てられているので表示可能。
通常の React のページでは、クライアントサイドで HTML を組み立てるので表示不可。

## SSG

ビルド時に HTML を生成。(コードパイプラインのビルド時)
更新頻度が少ない。
ユーザ：コンテンツ = 1:N
ブログ、EC サイト

## SSR

ユーザがリクエスト時にサーバーで生成する。クライアントサイドで生成するよりも早い。
更新頻度が多い。
ユーザ：コンテンツ = N:N
チャット、SNS

getStaticProps
・外部データを取得するために使う
・asnyc/await で非同期処理を制御出来る。(getStaticProps に async を付けて使う。)
・page コンポーネントでのみ使用可能。(他のディレクトリでは使用出来ない)

getServerSideProps
SSR の時に使う。他は getStaticProps と同じ。

## 通常のクライアントサイドレンダリング

データが頻繁に更新されるようなページはこっちの方が向いている。
useEffect の事。
→ SWR という機能もある。{key: value}の形でキャッシュしてくれる。
Real-time でデータ更新(データの再 fetch)
JAM-Stack 指向
