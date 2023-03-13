>$links$: https://mp.weixin.qq.com/s/FeyRhHCAvAhL6YalmYt1_Q
>$tags$: 
>$date$: 2023.03.13

1. **为什么你应该使用 React “框架”** 
   - https://leerob.io/blog/react-frameworks
   - 无论是 Next.js、Gatsby、Remix 还是其他框架，采用一个底层使用 React 的上层框架已经成为 2023 年的潮流。Lee 进行了分析，使用了一种漂亮的冰山隐喻，并且很好地概括了基本的论点。
   - 最近的一项研究显示，全球前 10,000 个公共网站中有约 6% 是使用 React 框架构建的。文章指出，使用框架可以让团队将更多时间投入到组件和业务逻辑的开发上，同时依赖于经过实践检验的开源解决方案，如路由、渲染、数据获取、样式、身份验证和测试等。此外，框架还可以提供灵活性，以支持不同的呈现策略（服务器、客户端或静态），并减少团队在连接工具上花费的时间。最后，文章强调，React 已经演变成了一个库、架构、社区和生态系统，因此，如果您正在使用 React，应该考虑使用框架来避免重复造轮子。
2. **初学者常见的 React 错误**
   - https://www.joshwcomeau.com/react/common-beginner-mistakes/
   - 作为一名有丰富 React 教学经验的教育家，Josh 已经见过大多数人遇到的常见问题。在这里，他深入探讨了“9 个最险恶的陷阱”以及如何解决它们。这篇文章的目标读者是那些在他们的 React 之旅“还相对较早”的人，所以如果你比较资深，这篇文章不适合你。
   - 这篇文章介绍了 React 开发中的 9 个常见问题，包括条件渲染时使用 0 、修改状态时的副作用、遗漏 key 属性、缺少空格、访问已更改的状态、返回多个元素、从不受控制到受控制的翻转、样式属性的差异以及异步效果函数。对于每个问题，文章提供了解决方案和代码示例，并强调了一些最佳实践。作者还推荐了自己开发的交互式在线课程 “React 之乐”，旨在帮助学习者建立对 React 的直觉理解。
3. **React hooks 是一个错误吗？**
   - https://jakelazaroff.com/words/were-react-hooks-a-mistake/
   - 这并不完全是试图回到基于类的组件，而是关于 **基于 Signals 方式** 快速普及的观点（更多地在非 React 框架中看到，例如使用 **Preact Signals**）。Jake 深入地探讨了涉及到的概念，但结论是“时间会证明一切”。
   - 最近，Web 开发社区一直在讨论信号（signals），这是一种响应式编程模式，可以实现非常高效的 UI 更新。Devon Govett 在 Twitter 上写了一个有趣的帖子，讨论了信号和可变状态。Ryan Carniato 回应了一篇优秀的文章，将信号与 React 进行了比较。所有方面都有好的论点；这个讨论非常有趣。文章指出，有很多人对 React 编程模型不感冒。为什么会这样呢？作者认为问题在于人们对组件的心理模型与 React 中使用 Hooks 的函数组件不匹配。因此，作者提出了一个大胆的观点：人们喜欢信号，因为基于信号的组件更类似于类组件而不是使用 Hooks 的函数组件。文章进一步解释了这种说法，并探讨了类组件、使用 Hooks 的函数组件和信号之间的差异和权衡。
4. **全栈 TypeScript + tRPC + React 应用**
   - https://www.robinwieruch.de/react-trpc/
   - 如何在服务器上使用 Node/Express，在客户端使用 React，同时使用 **tRPC** 在两者之间进行通信，创建一个 CRUD 应用程序。
   - tRPC 是一种使用 TypeScript 创建全栈应用程序的 API 的方法。tRPC 允许开发人员在全栈应用程序中创建完全类型安全的 API。虽然服务器应用程序生成具有类型安全函数的类型安全路由器（例如 CRUD 操作：创建用户、按标识符获取用户、获取所有用户），但客户端应用程序可以直接调用这些函数。在幕后，仍然使用 HTTP 在客户端和服务器之间进行通信。与 GraphQL 和 REST 相比，tRPC 主要用于较小的项目，其中不需要协调许多服务（例如 GraphQL）或者不需要使用标准化的 RESTful 方法处理资源。但是，随时可以从 tRPC 迁移到 GraphQL/REST，因为 tRPC 最终只是服务器上的函数，可以直接在 REST 路由器或 GraphQL 解析器中使用。
5. **如何使 React Native 应用更快**
   - https://retool.com/blog/retool-mobile-react-native-apps-faster/
   - 内部工具构建平台 Retool 的开发人员最近发布了 **Retool Mobile**，这是一种类似于他们基于 Web 的应用程序的方式来构建原生应用程序的工具。本文介绍了他们进行的一些优化，以使应用程序尽可能快速。
   - Retool，一个用于构建内部软件工具的平台，已经发布了 Retool Mobile 的公共测试版，以便企业能够构建和推出 iOS 和 Android 内部移动应用程序。该公司使用 React Native 开发了跨平台移动应用程序来呈现和更新在 Retool 可视化编辑器中构建的应用程序。在创建其他应用程序所基于的基础时，性能至关重要，因此 Retool 进行了三项性能优化，使其应用尽可能快速流畅：使用定制轻量级库替换第三方组件库；避免在使用 Immutable.js 和 Redux 管理状态更改时不必要地重新渲染组件；并删除阻塞 React Native UI 线程的代码拆分。
6. **Next.js 直接拖拽图片上传到 S3**
   - https://blog.danoph.com/how-to-nextjs-drag-and-drop-image-uploads-directly-to-s3-and-displaying-with-cloudfront
   - 包括用于 S3/CloudFront 集成的 Terraform 代码。
   - 本文介绍了如何使用 Next.js 和 Amazon S3 构建多文件上传表单，并将上传的图像显示在页面上。文章首先演示如何修改文件上传器以仅允许上传图像，并通过 CloudFront 和 Amazon S3 在页面上显示这些图像。然后，文章演示了如何创建一个图像库并添加一个 API 端点来获取已上传的图像。最后，文章介绍了如何实时显示上传的图像，而无需刷新页面。
7. **使用 Mantine、Strapi 和 Refine 构建一个 React Admin 面板**
   - https://refine.dev/blog/react-admin-panel/
8. **用 React Native 和 ButterCMS 创建一个知识库**
   - https://buttercms.com/blog/building-a-knowledge-base-with-react-native/
9. **用 React Native 将你的照片可视化在地图上**
   - 该文章介绍了作者开发的一款名为 “Photo Map” 的移动应用程序，它可以将用户拍摄的照片位置标记在地图上。作者使用了 React Native 和 Expo 来构建这个应用程序，并使用了 react-native-maps、Expo Medialibrary、react-native-view-shot 等库来实现不同的功能。文章还讨论了在开发过程中遇到的问题和如何解决它们。最终，作者分享了他的经验并总结了 React Native 和 Expo 的优点和缺点。
10. 著名 JavaScript YouTuber Theo 认为 **▶️ React 现在是一个后端框架**。
    - https://www.youtube.com/watch?v=EhI6wb5nEEs
    - React正在成为后端框架，新版本的React和React服务器组件使API不再必要，这是一个革命性的变化。React服务器组件可以很方便地获得所需的数据，而且需要的信息仅仅是传递组件的名称。这种方法类似于早期的React方式，只需要传递数据，不需要API。同时，React服务器组件还可以使用迭代器进行数据的动态刷新，这给web开发带来了极大的便利。虽然此种方法还需进一步验证，但已越来越得到人们的认同和支持，它的将会是web开发的无限潜力和可能性。
    - 💡 React中的服务器组件利用单向数据流模型，使得开发者可以像传递props一样获取到需要的数据；服务器组件本身就像一个API，可以包装其他组件，并在需要时向其传递数据；服务器组件可以在服务端获取数据，然后通过HTML传递到客户端；开发者可以通过使用服务器组件来完全取代API，并且可以更方便地获取和更新数据。服务器组件中的数据更新可以通过React自带的迭代器实现；
11. 构建了 Next.js 与 Vercel 的开发团队
    - https://vercel.com/blog/framework-defined-infrastructure
    - **一直在思考如何利用框架帮助系统推断其基础设施需求**，以便更顺利地部署。
    - “框架定义的基础设施（FdI）是基础设施即代码（IaC）的演进，其中部署环境自动提供从框架和编写在其中的应用程序派生出来的基础设施。 FdI抽象了云原语，例如服务器、消息队列和无服务器函数，使它们成为框架概念的实现细节。这意味着通过真正无服务器体系结构实现更可预测、更低成本和更低风险的DevOps。 FdI利用控制反转和基于框架的应用程序可预测结构来自动将框架概念映射到适当的基础设施上，而不需要显式声明或配置基础设施。 基于无服务器体系结构的不变部署允许生产基础设施完全映射到运行在该基础设施上版本代码，同时在低使用率期间具有异常可扩展性和经济效益。”
12. **Mantine v6.0：功能齐全的 React 组件库**
    - https://mantine.dev/changelog/6-0-0/
    - 越来越受欢迎的 MIT 许可的、基于 TypeScript 的 100 多个组件集合 和 Hooks (每个都有详尽的文档，比如 **Button 系列组件**)。在 v6 中，所有组件都使用 `rem` 单位，这会一定程度上影响所有组件的样式。迁移到该版本时，需要额外注意这些不兼容的变更。
    - Mantine 发布了 v6.0 版本，该版本包含多个重大变更，其中包括所有组件现在使用 rem 单位，而非像素；theme.spacing、theme.radius、theme.fontSizes 等属性现在期望以 rem 为单位定义；createStyles 函数不再接受 getRef 作为第三个参数，取而代之的是从 @mantine/core 包中导出的 getStylesRef；@mantine/notifications 包不再导出 NotificationsProvider 组件，而是应将 Notifications 组件添加到应用程序的任何部分。此外，还有许多其他变更和更新，包括新的选择器、props 名称更改、包的弃用和重构等。
13. **Ink v4.0：使用 React 组件构建命令行应用**
    - https://github.com/vadimdemedes/ink
    - 使用 React 风格的组件构建命令行应用程序。从**v4.0** 开始，Ink 现在是纯 ESM 格式，需要 React 18+ 和 Node 14.16+。
14. **Mezze** **从 Figma 将图标导出为 React 组件**
    - https://www.figma.com/community/plugin/1206354900231909165/Mezze-%E2%80%93-Convert-and-Export-Icons-as-React-Components
15. **Evolu：一组为本地优先应用设计的 Hooks**
    - https://github.com/evoluhq/evolu
    - 一组为本地优先应用设计的 Hooks，使用 **CRDT** 实现端到端加密备份和同步，使用 WebAssembly 版本的 **SQLite** 用于存储。
    - Evolu 是一个 React Hooks 库，用于本地优先的应用程序，具有端到端加密备份和同步功能，使用 SQLite 和 CRDT。Evolu 旨在实现隐私、易用性和无供应商锁定。它可以在用户设备上存储数据，因此可以离线工作且不需要特定的服务器。Evolu 还提供了类型化数据库架构、反应式查询、实时体验等功能，并使用 Mnemonic 加密数据。Evolu 社区位于 GitHub 讨论区和 Discord 上。该库已准备好用于生产环境，但目前仍不支持 CRDT 交易。
16. **PNGR：Docker 化的(Postgres + Nginx + Go + React)**
    - https://github.com/karlkeefer/pngr
    - 包含用户和会话管理、JWT 身份验证和基本的 CRUD 示例。
    - PNGR Stack 是一个 Docker 化的起始工具包，包括了 postgres、nginx、golang 和 react。它仅实现了用户、会话、密码重置和玩具帖子类型以演示基本的 CRUD 操作，而不是一个 CMS。该工具包具有热重载功能，包括用于 golang 更改的测试运行器。后端使用了已配置好易于迁移的 golang-migrate、自动生成的 sql 绑定工具 sqlc、自动生成的 mock 工具 gomock 和顶级数据库驱动程序 pgx。前端使用了 React Router 进行前端路由，React Context 进行全局用户状态管理，语义化 UI 库 Semantic UI React 以及预渲染边车容器。此外还提供了用于异步任务的 golang 工作器容器存根。使用该工具包需要安装 docker 和 docker-compose。

**好库推荐**
-   **⌘K / cmdk v0.2**  
	↳ 命令菜单组件
-   **swr v2.1**  
	↳ 请求数据的 hook
-   **react-jsonschema-form v5.2**  
	↳ 通过 JSON Schema 声明式的创建表单
-   **mui-x v6.0**  
	↳ 优秀的 React 组件集合
-   **playroom v0.30**  
	↳ 为组件提供零安装的面向代码的设计环境
-   **react-player v2.12**  
	↳ 支持播放多种视频源的组件，包括但不限于 YouTube、Facebook、Twitch 和 SoundCloud 等
-   **ReacType v14.0**  
	↳ 快速搭建原型的工具
-   **visx v3.1**  
	↳ 来自 Airbnb 的底层可视化组件的集合
-   **metro v0.76**  
	↳ 用于 React Native 的 JS 打包器
-   **styled-components v5.3.8**