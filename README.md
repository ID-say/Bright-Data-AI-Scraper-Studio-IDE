

> **视频讲解：**
> [https://vdn3.vzuu.com/HD/e4ba21e2-d9cb-11f1-aec2-32dbcce6fb9f-v4_f2_t1_OKpMr0hU.mp4?auth_key=1793964910-0-0-04d8f36ee82791f6caf321e434c06547&bu=09fd86c2&c=avc.4.0&disable_local_cache=1&expiration=1793964910&f=mp4&pu=e59e796c&v=tx&pp=ChMxNDAxNjIzODY1NzM5NTc5MzkyGGMiC2ZlZWRfY2hvaWNlMhMxMzY5MDA1NjA4NTk5OTA0MjU3PXu830Q%3D&pf=Web&pt=zhihu](https://vdn3.vzuu.com/HD/e4ba21e2-d9cb-11f1-aec2-32dbcce6fb9f-v4_f2_t1_OKpMr0hU.mp4?auth_key=1793964910-0-0-04d8f36ee82791f6caf321e434c06547&bu=09fd86c2&c=avc.4.0&disable_local_cache=1&expiration=1793964910&f=mp4&pu=e59e796c&v=tx&pp=ChMxNDAxNjIzODY1NzM5NTc5MzkyGGMiC2ZlZWRfY2hvaWNlMhMxMzY5MDA1NjA4NTk5OTA0MjU3PXu830Q%3D&pf=Web&pt=zhihu)

# 前言

现在利用 AI 生成爬虫已经不是什么难事，只需要描述目标网站和需要的数据，AI 就能够帮助我们生成采集代码。

但如果后续需求发生变化，比如最开始只需要商品标题，后来又需要价格、评分、品牌等详细信息，难道每次都要重新生成一个爬虫吗？

这次我选择 Amazon 商品榜单作为测试场景，通过 **Bright Data Scraper Studio IDE**，体验从 AI 生成基础爬虫，到修改 JavaScript、扩展商品字段以及多阶段抓取的完整过程。

# AI 生成爬虫后的问题

首先通过 Scraper Studio 的 AI Agent 描述需求，让 AI 生成基础采集代码。

初始目标比较简单：获取指定商品榜单前 5 个商品的信息，并将采集数量设置为可修改的变量。

但在实际使用中，仅有商品列表信息并不能完全满足需求。

例如商品的发货方、卖家以及首次上架时间等信息，可能需要进入商品详情页才能获取。

因此，接下来需要进入 IDE，对原有爬虫进行进一步调整。

# Scraper Studio IDE 二次开发

Scraper Studio IDE 主要包含交互代码和解析器代码。

交互代码负责网页导航、等待元素加载以及执行采集流程；解析器代码则负责从 HTML 中提取具体的数据字段。

代码运行时会先获取列表中的商品信息，再逐个访问商品详情页，尝试补充发货方、卖家以及首次上架日期等数据。

对于更加复杂的任务，Scraper Studio 还支持通过 `next_stage()` 将列表页和详情页拆分为不同采集阶段。

# 实际调试与运行

在测试过程中，我还尝试修改商品采集数量。

原本代码中设置的是：

max=输入值 or 5

将其调整为 `10` 后，实际运行结果却仍然只有 5 条。

这说明修改数量变量，并不一定能让最终输出数量同步增加，还需要检查解析器、页面加载以及其他代码限制。

Scraper Studio IDE 提供 Preview、Run Log 等调试功能，可以帮助开发者检查页面执行过程和数据解析情况。

另外，平台还提供 Code Worker 和 Browser Worker 两种执行引擎，分别适用于静态数据采集和需要浏览器交互的页面。

在完成调试以后，可以保存开发版本，并根据需要执行正式采集任务、导出 JSON 数据或配置定时运行。

# 体验总结

经过这次体验，我认为 Scraper Studio 的价值不仅在于能够使用 AI 快速生成爬虫，更在于**生成后的代码仍然可以继续修改、扩展和调试**。

对于简单的数据采集任务，AI Agent 能够降低开发门槛；而面对多页面抓取、字段扩展以及复杂的执行逻辑时，IDE 提供了更加灵活的控制方式。

当然，AI 生成的代码也不意味着可以完全跳过调试。实际运行过程中，仍然可能遇到数量限制、页面结构变化等问题。

**AI 负责提高开发效率，而 IDE 则让开发者能够进一步掌控采集过程。**

本次完整操作、代码调整及测试过程均在视频中进行了展示，感兴趣的朋友可以观看文首视频。

> 通过以下专属链接注册，在结账时输入brd09 即可获得专属优惠
> 福利入口：[https://www.bright.cn/products/web-scraper/studio?utm_source=brand&utm_campaign=brnd-mkt_cn_csdn_qidian202611](https://www.bright.cn/products/web-scraper/studio?utm_source=brand&utm_campaign=brnd-mkt_cn_csdn_qidian202611)
> 视频讲解：见文首



