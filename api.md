[Darabonba](https://github.com/aliyun/darabonba)

Darabonba 是一种用于 OpenAPI 的 DSL 语言，可以用来生成多语言的 SDK、Code Sample、Test Case 等代码

升级版 Node.js SDK 是基于阿里云自研的 DSL 语言 Darabonba 生成，通过 DSL 的灵活性不仅可以进行更多的表达而且通过解析 DSL 生成的 AST 也能抹平阿里云不同产品生产的不同风格 OpenAPI 的差异轻松的实现 OpenAPI 到 SDK 的生成。通过 DSL 的方式并结合以往 Node.js SDK 中的问题，阿里云提供的升级版 Node.js SDK 具备以下的特性：

解决原版 SDK 中产品 OpenAPI 风格不同（RPC 或 ROA）造成使用方式不一致问题，升级版 SDK 中所有云产品的 SDK 使用方式相同，使用体验一致。

通过 DSL 使 SDK 具备逻辑表达能力，从而使升级版 SDK 不用像原版 SDK 只有 CommonRequest 的请求模式，并且配合 TypeScript 的优势为 IDE 提供更好的编程体验。

升级版 SDK 支持更复杂的 OpenAPI 使用场景，例如阿里云的人体人脸（FaceBody）等产品中需要上传图片到 OSS 以后，通过该链接对图片进行人工智能分析处理，就可以通过升级版 SDK 组合上传鉴权、上传图片、图片分析三个操作从而实现对该 OpenAPI 使用的简化。

升级版 Node.js SDK 不仅为 SDK 中的所有的 OpenAPI 请求生成相应的示例，同时也通过对 SDK 中的多个 OpenAPI 请求进行组合从而提供 SDK 的场景化示例，这样的示例不仅可以帮助开发者降低接入 SDK 的成本，同时也可以帮助开发者更好的理解云产品的业务场景。

https://next.api.aliyun.com/
