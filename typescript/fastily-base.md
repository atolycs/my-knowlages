# fastifyの使い方

基本コード (公式より)
* Node.js
  * Async/Awaitあり
    ```javascript
    const fastify = require("fastify")({ logger: true })

    fastify.get('/', async (request, reply) => {
        return { hello: 'world' }
    })  

    const start = async () => {
    try {
       await fastify.listen({port: 3000})
    } catch (err) {
        fastify.log.error(err)
        process.exit(1)
        }
    }
    start()
    ```
  * Async/Awaitなし
    ```javascript
    const fastify = require('fastify')({ logger: true })

    fastify.get('/', (request, reply) => {
        reply.send({ hello: ' world' })
    })

    fastify.listen({ port: 3000}, (err) => {
        if (err) {
            fastify.log.error(err)
            process.exit(1)
        }
    })
    ```


* Typescript
```typescript
import fastify from 'fastify'

const server = fastify()

server.get('/ping', async (request, reply) => {
    return 'pong\n'
})

server.listen({port: 8080}, (err, address) => {
    if (err) {
        console.error(err)
        process.exit(1)
    } 

    console.log(`Server listening at ${address}`)
})
```

※Typescriptの場合は、必ず`tsc`を実行し、コンパイルする