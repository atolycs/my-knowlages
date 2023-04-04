# fastifyのルーティング

* fastifyのルーティングは以下のコードで行う
  * 基本相当なコードが書けるようだ

* 基本コード (Node.js)
```javascript
fastify.route({
    method: 'GET', //メソッドを指定(HTTPメソッド全般書ける見たい)
    schema: {
        querystring: { // なんのクエリーを飛ばす? -> クエリーを定義って言ったほうが正しい?
            name: { type: 'string' },
            excitement: { type: 'integer' }
        },
        response: {
            200: {
                type: 'object',
                properties: {
                    hello: { type: 'string' }
                }
            }
        }
    },
    handler: function (request, reply) { // ハンドラー?
        reply.send({ hello: 'world'})
    }
})
```

`querystring`はドキュメントを見る限り、なんかヘッダー情報に付加してる…? (**要調査**)

* ショート版もあるらしい。
  * ~~というか、上のフル版はあまり使わないみたい…~~
* コード (GETメソッド)
```javascript
fastify.get('/',(request, reply) => {
    reply.send({ hello: 'world'})
})
```
* 最低限コールバックさえ設定しておけば後はどうにでもなりそう
* ルーティングはこっから追加できそう
  * うまくインポートを駆使するか、クラス分けしてあげることで、向き先を追加できそう
