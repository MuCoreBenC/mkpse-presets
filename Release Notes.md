# Release Notes

## v0.0.4 (2026-07-29) — 五层架构解耦与预设生命周期 V2

v0.0.4 是 mkpse-next 平台化深化阶段版本。本版本完成五层架构解耦（Adapter 层 + Repository 模式 + ESLint 架构守护），重构预设生命周期 V2（Preset Lifecycle 平台包 + hasUpdate 单源派生），建立统一内容/资源/排序管线，并修复下载应用流程静默失败等关键 Bug。

### 核心功能
1. 五层架构解耦：前端 Adapter 层 + 后端 Repository 模式 + ESLint no-direct-wailsjs 架构守护
2. 通知系统 V2：Content 化 + Selection Coordinator 工作流 + Notification Inspector + @mkp/diagnostics 平台包
3. 预设生命周期 V2：Preset Lifecycle 平台包 + hasUpdate 单源派生 + ListLocalPresets 诊断增强
4. 统一内容管线 (Unified Content Pipeline)：useContent 单一入口 + 远程 Provider 架构 + ContentLab
5. 统一资源管线 (Unified Resource Pipeline)：6 套状态枚举统一为 ResourceStatus
6. 统一排序引擎：@mkp/order 平台包 + onMove 拖拽语义 + 6 个页面列表排序统一迁移
7. 平台包抽取：@mkp/preset-components + @mkp/preset-update + @mkp/preset-ui + @mkp/diagnostics + @mkp/text-selection
8. selection-behavior 平台包：resolvePrimaryButton 主按钮决策 + SelectionSession 状态模型
9. 后处理引擎 V2：四层架构 SSOT 统一，三套 ProcessGcode 收敛为单一 Engine 内核
10. 策略驱动设置重构：Baseline 隐藏目录 + Content Top Accesses
11. 树编辑器体验升级：递归 depth + 三区域布局 + TreeRow/useTreeExpansion/useTreeSearch 平台包
12. Layout 纯 Presentation：Tab/Section 一等实体 + SchemaRenderer 按 schema 驱动渲染
13. mkp-prototype 视觉对齐旧版 + enhanced 组件与 design-notes
14. MKP DevTools Console + M036 Runtime Lock

### 架构优化
15. Adapter 层：前端 UI 组件与 Wails 后端完全解耦，统一通过 Adapter 访问后端能力
16. Repository 模式：后端 internal/repository 封装数据访问，分离业务逻辑与路径处理
17. ESLint 架构守护：no-direct-wailsjs 规则 + audit-five-layer.sh + generate-harness-report.mjs
18. Registry as Definition SSOT：Tab/Section 一等实体 + Layout 纯 Presentation 全栈落地
19. 统一 React 单实例：18.2 → 18.3.1 + Rule M026 + CI 审计脚本
20. 删除两套 MCP server：收敛为 source/*.toml 单一编辑入口
21. Notification Renderer 拆分 panel/supporte 双轨 + BaselineSHA 双比较修复
22. NotificationCard 共享组件提取，Panel/Supporte Toast 收敛为薄壳
23. 参数顺序 SSOT 落地 + subfieldsOrder 所有权澄清
24. preset-update 重构：statusMapper → presetState，状态派生统一

### 修复
25. 下载应用流程静默失败修复：applyPreset 锁阻塞改为抛错 + isVersionDownloaded 文件级判断 + 移除 done 后台下载
26. DeviceSelection 主卡片计数与文案解耦 + 版本范围过滤防 pendingBar 计数污染
27. Preset Lifecycle 状态源统一：FileRegistry key 规范化 + pending* helper 家族
28. Preset Lifecycle 状态模型修复：区分 applied/imported/pending_import，消除"已下载仍提示更新"真值错误
29. 通知 SSOT + 多重 Bug 修复（复制/Alt框选/启动请求/FAQ图片/保存自动Build/彩蛋面板/涂胶画布）
30. 深度审查与修复：SSOT 默认值不一致 + 启动 42 次请求 + 静默吞错
31. DeviceSelection hasUpdate 误报修复 + 初始化状态循环 + preferences override 无变化也回写
32. CloudPresetCard/MergeModal/ConflictModal/EditParamsModal 系列修复
33. 云端预设列表只显示 1 个预设的回归修复

### 体验优化
34. 通知 CopyTemplate + 统一调试能力（Copy JSON/Timeline/Logs/Inspector/Download Session）
35. Theme Studio Live Sandbox + 预设生命周期平台包 + Pipeline Lab + Playback Mode + 回退三连击
36. mkp-platform-lab Lab 中文化 + 三级测试报告系统 + Scenario Suite 升级为 4 类场景套件
37. Host 语义化 + Stepper 选择器 + Keepalive 优化
38. Theme Engine + Publish Flow + Param Layout 平台包
39. Interaction Studio + Notification Inspector + V2 Lifecycle 审计

## v0.0.3 (2026-07-16) — 平台能力抽取与设计令牌 SSOT

v0.0.3 是 mkpse-next 平台化阶段的第一版。本版本将设计令牌、UI 组件、Layout Schema、Draft/Focus/Asset 等平台能力抽取为独立包，建立 mkp-platform-lab 作为平台能力演练场，并通过 M018-M020 规则防止过度平台化。

### 核心功能
1. mkp-platform-lab 演练场：TypingSessionManager + CompositeCommand + Timeline 事件流 + Playground 调试 UX
2. foundation 设计令牌 SSOT 包：tokens/variants/themes/icons/motions/recipes + theme-engine（ThemeProvider/TokenRuntime/ThemeLoader）
3. design-lab 独立工具项目：Shadow/Tokens Design Lab + Scene 模式 + layoutDemos + 视觉快照回归
4. Layout Schema 作为 UI SSOT：SchemaRenderer + registry 按 schema 驱动渲染 + param-layout 包
5. UI 组件库统一：mkppanel/mkpsupporte 删除 25+ 本地组件，统一从 mkp-ui 消费
6. preset_registry SSOT + Canonical/Alias mismatch 修复 + audit-registry 校验
7. application_defaults Entity：appearance/update/ambientIntensity 段，双端统一默认值 SSOT
8. Sprint-1 平台能力抽取：Focus/Asset/DesignLab 平台包独立
9. Draft 平台包抽取：draftHistoryStore + mutationEventBus 平台化
10. 后处理器路径范围检测：擦料塔/热床预涂胶路径超范围检测

### 架构优化
11. 阴影配置 SSOT 统一：shadow_config 扩展 8 个 variant + ShadowLab + spatial shadow engine + ambientIntensity
12. 机型元数据硬编码清理：走 catalog SSOT + Orphan 预设诊断
13. M018-M020 架构规则扩展：preset_registry Canonical ID 校验 / YAGNI 禁止过早抽象 / layout_schema 禁止扩展为完整 UI Schema
14. BBS 卡 95% 运行时模型 + StuckDetector：诊断下载卡死

### 修复
15. 后处理流水线修复 + Design Studio 雏形 + 机型 mismatch 防呆
16. BBS 下载卡 95% + StuckDetector 诊断
17. Mismatch CLI GUI 弹模态框 + 终端窗口复用 + 参数保存 flush
18. 斜肋包围盒保守正方形简化 + brim/sheath 加 2mm 安全余量
19. 参数侧边栏点击导航修复

### 体验优化
20. visual regression demo 包：Gallery + KitchenSink + 视觉快照测试基线
21. 主题环境光渐变渲染：useAmbientGradient + useSpatialShadowEngine + ambientIntensity stepper
22. 测试执行策略文档化 + evolve-as-debugger spec
