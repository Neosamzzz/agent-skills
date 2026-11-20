# React Bits 组件收藏

按界面需求挑选候选，先看本页的用途和限制，再打开官方演示或读取单组件源码。

## 快速选型

- **工具页**。优先看 AnimatedContent 的短淡入、GradualBlur 的滚动边缘、LatticeLoader 的等待反馈。三者的常用效果都能用现有 HTML、CSS、JavaScript 实现。
- **控件和导航**。短筛选看 GlideSelect，提醒开关看 BellToggle，分步引导看 Stepper，分组导航看 CardNav。先核对当前页面已有的交互路径。
- **展示页**。Galaxy、Strands、HoloCard、ModelViewer 适合少量有明确作用的展示区。WebGL、Canvas、3D 模型和持续动画都需要在目标设备上看实际表现，依赖列表为空的组件也可能使用这些能力。

需要看具体实现时，读取官方单组件 JSON，先看 `dependencies`、`registryDependencies` 和 `files`。名称格式为 `<组件名>-TS-CSS.json`，也可以选择官方列出的 JS 或 Tailwind 变体。[GradualBlur 源码示例](https://www.reactbits.dev/r/GradualBlur-TS-CSS.json) · [React Bits 官方目录](https://www.reactbits.dev/get-started/index)

下面的取舍基于官方介绍和 21 项 TS-CSS 源码。部署前按实际环境验证触控、焦点、软键盘、减弱动态效果和滚动表现。

## 背景 · Backgrounds

- **Galaxy**。持续运动的 WebGL2 星场，适合主题封面。移动端优先限定展示面积，给不支持 WebGL2 或选择减弱动态效果的用户准备静态背景。 [Galaxy 官方演示](https://www.reactbits.dev/backgrounds/galaxy)

## 动画 · Animations

- **GradualBlur**。用多层遮罩叠加背景模糊，适合吸顶栏、横向滚动区和轮播边缘。普通工具页可以用单层渐变，只有确需看清背景层次时才加模糊。检查滚动区边缘的文字对比度。 [GradualBlur 官方演示](https://www.reactbits.dev/animations/gradual-blur)
- **OrbitImages**。图片沿 SVG 路径排列，支持拖动、键盘、点击和减弱动态效果。适合少量重点媒体展示。移动端要确认纵向滚动顺畅，并给每张可操作的图片写有意义的替代文本。 [OrbitImages 官方演示](https://www.reactbits.dev/animations/orbit-images)
- **AnimatedContent**。GSAP ScrollTrigger 控制滚动入场，适合展示页的段落或图组。工具页的数据首次出现时，用短淡入就够。把关键数据和按钮保留为默认可见，避免脚本延后时首屏空白。 [AnimatedContent 官方演示](https://www.reactbits.dev/animations/animated-content)
- **Strands**。用 WebGL2 渲染丝束，有屏外暂停和可调像素密度。适合品牌展示或视觉焦点，移动端先缩小画布并检查实机帧率。 [Strands 官方演示](https://www.reactbits.dev/animations/strands)
- **Magnet**。用弹簧让元素随指针偏移，源码主动忽略触屏指针。适合桌面的次要按钮或宣传入口，移动端用按压反馈表达状态。 [Magnet 官方演示](https://www.reactbits.dev/animations/magnet)

## 组件 · Components

- **HoloCard**。WebGL2 全息箔面加倾斜和可选翻面，适合收藏品、角色卡或展品。采用翻面时要确认点击和键盘均可触发，关键信息在静态状态也能读取。 [HoloCard 官方演示](https://www.reactbits.dev/components/holo-card)
- **AccordionGallery**。GSAP 驱动图板展开，支持悬停、焦点、点击和方向键。适合少量图片导览。手机上要实测首次点按展开、再次点按打开链接的节奏，以及横向排列是否需要改为纵向。 [AccordionGallery 官方演示](https://www.reactbits.dev/components/accordion-gallery)
- **ReflectiveCard**。WebGL 金属反光卡，可用循环视频或选配摄像头，图标依赖 Hugeicons。一般展示优先用静态素材或视频。使用摄像头时提供明确入口和拒绝授权后的展示状态。 [ReflectiveCard 官方演示](https://www.reactbits.dev/components/reflective-card)
- **CardNav**。把导航链接按组展开到卡片面板，支持紧凑布局和 Escape 关闭，图标依赖 Hugeicons。适合栏目多、需要分组的站点。移动端检查展开高度、关闭后焦点和底栏安全区。 [CardNav 官方演示](https://www.reactbits.dev/components/card-nav)
- **GlassSurface**。有 SVG 折射、WebGL 渲染和磨砂回退，实际路径取决于浏览器、渲染配置和背景。工具栏或浮层优先借鉴材质和边框，用半透明底色维持对比，并在目标 WebView 检查回退。 [GlassSurface 官方演示](https://www.reactbits.dev/components/glass-surface)
- **Folder**。可展开文件夹或书册，内容可点击，支持选配拖拽。适合少量可视素材的分组入口。手机先保证点按路径，开启拖拽时检查会不会截断页面滚动。 [Folder 官方演示](https://www.reactbits.dev/components/folder)
- **ModelViewer**。基于 Three.js、React Three Fiber 和 Drei，适合确实需要旋转或放大模型的产品展示。准备静态封面，按需加载模型，检查手势与页面滚动是否冲突。 [ModelViewer 官方演示](https://www.reactbits.dev/components/model-viewer)
- **Dock**。桌面式图标放大、徽标和上下文菜单，菜单使用 React DOM portal。适合桌面工具栏。手机要检查长按、图标标签和浮层安全区，靠固定触控区域保持命中稳定。 [Dock 官方演示](https://www.reactbits.dev/components/dock)
- **GooeyNav**。选中胶囊用 WebGL2 做流体过渡，自带普通高亮回退和当前页语义。适合有明确风格的导航。工具页通常只需让选中高亮滑过去，并让切页即时生效。 [GooeyNav 官方演示](https://www.reactbits.dev/components/gooey-nav)
- **PixelCard**。用 2D Canvas 处理像素扩散，源码包含触控和焦点反馈。适合像素风主题的少量卡片。列表里大量重复前，先检查每张画布的总成本，关键状态用文字或图标标明。 [PixelCard 官方演示](https://www.reactbits.dev/components/pixel-card)
- **SpotlightCard**。光斑跟随指针，也有按压和焦点处理。适合突出一两张功能卡。触屏版可借鉴局部光斑或边框亮起，保持辅助文字在默认状态清晰可见。 [SpotlightCard 官方演示](https://www.reactbits.dev/components/spotlight-card)
- **Stepper**。带步骤切换和当前位置标记，可横排或竖排，图标依赖 Hugeicons。适合真实多步流程。表单校验、保存和返回后的数据还原由业务处理，手机上要测键盘弹起时的操作区。 [Stepper 官方演示](https://www.reactbits.dev/components/stepper)

## 微交互 · Micro

- **GlideSelect**。支持方向键、Escape 和列表高亮，图标依赖 Hugeicons。适合占空间的几项筛选或模式切换。只有月付、年付两项时，直接可点的分段控件路径更短。放进滚动弹层要检查列表裁切和触控。 [GlideSelect 官方演示](https://www.reactbits.dev/micro/glide-select)
- **LatticeLoader**。有加载、完成、错误三种状态以及可选计时，状态用读屏可识别的文字传达。适合有明显等待的任务。普通短请求可延迟显示，简化为点阵加状态文字，减弱动态效果时使用静态点阵。 [LatticeLoader 官方演示](https://www.reactbits.dev/micro/lattice-loader)
- **BellToggle**。用 Motion 和 Hugeicons 给二元提醒开关做振铃反馈，状态由按钮语义表达。适合真正的开关。接入异步保存时，要处理待确认与失败后的状态回退。 [BellToggle 官方演示](https://www.reactbits.dev/micro/bell-toggle)
