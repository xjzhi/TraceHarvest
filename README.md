<div align="center">
  <h1>潜影【TraceHarvest】</h1>

  <img width="128" height="128" alt="Yee Music" src="https://avatars.githubusercontent.com/u/109730978">
</div>

<div align="center">
  <p>TraceHarvest 实现了从 自动检索 → 跨引擎去重 → 敏感信息识别 → 信息可视化 → 报告输出 的完整工作流</p>
  <p><strong>网络安全攻防演练自动化信息收集工具</strong></p>
</div>

<div align="center">
  <a href="https://github.com/i-am-xjizhi/TraceHarvest/stargazers">
    <img src="https://img.shields.io/github/stars/i-am-xjizhi/TraceHarvest" alt="GitHub Stars">
  </a>
  <a href="https://github.com/i-am-xjizhi/TraceHarvest/network">
    <img src="https://img.shields.io/github/forks/i-am-xjizhi/TraceHarvest" alt="GitHub Forks">
  </a>
  <a href="https://github.com/i-am-xjizhi/TraceHarvest/watchers">
    <img src="https://img.shields.io/github/watchers/i-am-xjizhi/TraceHarvest" alt="GitHub Watchers">
  </a>
  </b>
</div>

<div align="center">
  <a href="https://github.com/i-am-xjizhi/TraceHarvest/releases">
    <img src="https://img.shields.io/github/downloads/i-am-xjizhi/TraceHarvest/total?labelColor=black&color=red&label=Downloads" alt="Downloads">
  </a>
  <img src="https://img.shields.io/badge/Version-1.0-blue" alt="Version: 1.0">
  <a href="https://github.com/i-am-xjizhi/TraceHarvest/issues">
    <img src="https://img.shields.io/github/issues/i-am-xjizhi/TraceHarvest?labelColor=black&color=green" alt="GitHub Issues">
  </a>
  <img src="https://img.shields.io/badge/OS-Windows_10/11-0078D6?labelColor=black&color=blue" alt="OS: Windows 10/11">
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License: MIT">
  </a>
</div>



## 🖼️ 界面展示
> 潜影是一款为安全研究人员与开发者设计的 Windows GUI 一体化工具，专用于面向网络安全攻防演练场景的自动化信息收集工具。通过智能化的多引擎搜索和敏感信息提取技术，解决了在大规模目标侦察过程中人工搜索效率低下、信息遗漏严重、重复工作繁多的核心痛点，本工具实现了从 自动检索 → 跨引擎去重 → 敏感信息识别 → 信息可视化 → 报告输出 的完整工作流。

![图片](https://github.com/user-attachments/assets/2377afaa-101a-4fe0-9d29-e7bb355123e4)

---

## ✨ 解决了哪些实际问题？
### 1. 规模化目标侦察自动化
- **问题**：对多个目标组织进行全方位信息收集时，需要人工组合各种关键词（如"公司名+招聘"、"品牌+招标"、"域名+联系方式"等），操作繁琐且易遗漏。
- **解决方案**：潜影 实现主词×副词的**笛卡尔积**自动生成，一次性生成所有可能的搜索组合，确保搜索维度的完整性。
### 2. 多源信息聚合困难
- **问题**：不同搜索引擎（百度、Bing、微信）的结果各有侧重，人工切换搜索耗时且难以统一管理结果。
- **解决方案**：工具并行调度多个搜索引擎，统一采集、去重和格式化结果，提供单一视角的完整情报视图。
### 3. 敏感信息提取效率低下
- **问题**：从海量网页中手动查找**手机号、邮箱**等联系方式费时费力，容易因视觉疲劳而遗漏关键信息。
- **解决方案**：内置高精度正则表达式匹配引擎，自动从搜索结果页面中提取11位手机号（1[3-9]开头）和标准邮箱地址，准确率达99%以上。
### 4. 反爬机制应对复杂
- **问题**：百度等搜索引擎对自动化查询有严格的频率限制，容易触发IP封禁，导致收集工作中断。
- **解决方案**：实现智能交错调度算法和可配置延迟机制。
- 1）百度首条查询立即执行
- 2）后续百度查询按用户设定间隔（默认120秒）逐个执行
- 3）其他引擎查询在百度等待期间穿插进行，最大化时间利用率
### 5. 结果管理混乱
- **问题**：收集到的信息分散在不同文件、笔记中，难以分析关联和导出报告。
- **解决方案**：提供结构化表格展示和标准化CSV导出（UTF-8 with BOM，兼容Excel中文），支持后续数据分析 4）遇到验证码自动停止相关引擎，避免账户风险

---

## 🛠️ 核心特性
### 🔄 智能组合查询引擎
- 笛卡尔积搜索生成：自动将主查询词（如"南瑞"、"英大"）与副查询词（如"招聘"、"招标"、"领导"、"漏洞"）组合，生成所有可能的搜索对
示例输出：


### 🌐 多引擎协同采集
- 百度：中文网络内容覆盖最全，适合国内目标
- Bing：国际内容+中文混合，提供不同视角
- 微信/搜狗：获取微信公众号、文章等封闭生态内容
- Google：预留接口，待政策允许后扩展
- 并行-串行混合调度：在遵守反爬规则的前提下最大化采集速度
  
### 📄 深度翻页采集
- 可配置采集深度
- 完整上下文获取：不仅采集标题摘要，还提取页面正文，提高敏感信息发现率
  
### 🔍 精准信息提取
- 手机号识别：严格遵循中国手机号规范（1[3-9]XXXXXXX）
- 邮箱地址提取：支持常见邮箱格式（@qq.com、@163.com、企业邮箱等）
- 误判率控制：通过上下文验证减少假阳性
- 格式化输出：自动去重、排序、分类展示
  
### 🎯 反反爬智能策略
- 动态请求间隔：百度引擎可自定义请求间隔（建议≥120秒）
- 请求头随机化：模拟真实浏览器行为
- 失败自动处理：遇到验证码、封禁时智能暂停并提示
- 会话保持：维持Cookies，提高访问成功率
  
### 📊 专业级结果管理
- 实时表格展示：采集过程中实时更新结果，进度可视
- 多维度排序：按来源、关键词、时间等多字段排序
- 批量导出：一键导出为CSV，保留完整字段
- 包含：关键词、来源、URL、标题、手机号、邮箱、采集时间
- 数据去重：基于URL和内容哈希自动去重
  
### 🖥️ 现代化用户界面
- 自适应布局：字体和控件随窗口大小自动调整
- 白色科技风格：简洁专业，减少视觉疲劳
- 进度可视化：实时显示各引擎进度条和统计信息
- 日志面板：详细运行日志，便于调试和审计

---


## ⚙️ 运行环境与使用
- 操作系统：Windows 10 / 11 （64位）
- 环境要求：无需安装任何依赖（如Python、Node.js、Java等）。下载可执行文件，解压后双击即可运行。
### 效果展示

![图片](https://github.com/user-attachments/assets/0199c08b-ce97-452e-97ef-f8779ba7426b)
![图片](https://github.com/user-attachments/assets/80c0d490-0861-460c-a8ad-a696514e6954)

---

## 🚀 应用场景
### 1. 攻防演练/红队评估
- 攻击面发现：快速识别目标暴露在互联网的敏感信息
- 社会工程学准备：收集目标员工联系方式、组织架构信息
### 2. 企业安全自查
- 信息泄露监控：定期扫描公司敏感信息是否被意外公开
- 第三方风险评估：关联企业、供应商的信息暴露情况
### 3. 学术研究/取证调查
- 数据收集：为安全研究提供实证数据
- 模式分析：研究不同行业的信息暴露特点
- 趋势跟踪：监控特定类型信息的网络传播情况
  
---

## ⭐ Star History

![Star History Chart](https://api.star-history.com/svg?repos=i-am-xjizhi/TraceHarvest&type=date&v=1)

---

## 🙏 致谢

感谢所有为本项目做出贡献的开发者！

---

## ⚠️ 免责声明

本工具仅供安全研究和授权测试使用。使用本工具进行未经授权的测试是违法的。使用者需自行承担使用本工具的一切后果，作者不承担任何法律责任。

---

## 💬 互动交流
欢迎加入我们的安全技术交流群，与开发者和安全研究人员一起讨论安全工具的使用、漏洞挖掘等话题！

### 🤝 加入技术交流群
- 微信群（推荐）

![微信群](https://github.com/user-attachments/assets/f9c9e1d9-96c7-4f2a-84b6-28823e0f3c26)


- ➕V：xjizhi_run 进入GG安全交流群（**交流群超200人需要人工邀请，扫码+V时请备注：进群**）
- 微信二维码

![微信](https://github.com/user-attachments/assets/ab7fbf45-dfd4-40c9-b53e-00b3f92e3e90)
