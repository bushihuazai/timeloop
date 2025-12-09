# Timeloop 设计框图

本目录包含 Timeloop 项目的设计框图，使用 PlantUML 格式描述。

## 文件说明

### 1. design-architecture.puml
完整的架构设计图，展示了 Timeloop 的所有主要组件及其关系：
- **Application Layer（应用层）**: Mapper、Model、Metrics 等应用程序
- **Workload Description（工作负载描述）**: 问题规格、张量维度、稀疏性模型
- **Architecture Model（架构模型）**: 硬件拓扑、存储层次、计算单元、互连网络
- **Mapping Representation（映射表示）**: 循环嵌套、时空划分、数据放置
- **Mapping Search（映射搜索）**: 各种搜索算法（穷举、随机、混合等）
- **Analysis and Evaluation（分析与评估）**: 循环分析、性能/能耗模型

### 2. design-architecture-simplified.puml
简化的高层架构图，重点展示：
- **输入规格**: 工作负载、架构规格、约束条件
- **核心引擎**: Mapper（映射器）和 Model Engine（模型引擎）
- **输出结果**: 统计信息、优化映射、代码生成
- 主要数据流和反馈循环

### 3. design-architecture-components.puml
组件和类关系图，详细展示：
- 主要类及其属性和方法
- 类之间的关联、聚合、继承关系
- 包结构和模块划分

### 4. design-execution-flow.puml
执行流程序列图，展示：
- Mapper 应用程序的完整执行流程
- 多线程搜索过程
- 映射评估的详细步骤
- 配置解析、搜索、分析、输出生成的时序关系

## 如何使用

### 在线查看
可以使用以下在线工具查看 PlantUML 图表：
- [PlantUML Online Server](http://www.plantuml.com/plantuml/uml/)
- [PlantText](https://www.planttext.com/)

### 本地渲染
1. 安装 PlantUML:
```bash
# Ubuntu/Debian
sudo apt-get install plantuml

# macOS
brew install plantuml

# 或下载 jar 文件
wget http://sourceforge.net/projects/plantuml/files/plantuml.jar/download -O plantuml.jar
```

2. 生成图表:
```bash
# 生成 PNG 格式
plantuml design-architecture.puml

# 生成 SVG 格式
plantuml -tsvg design-architecture.puml

# 使用 jar 文件
java -jar plantuml.jar design-architecture.puml
```

### 在 VS Code 中查看
安装 PlantUML 扩展:
1. 打开 VS Code
2. 安装 "PlantUML" 扩展
3. 打开 .puml 文件
4. 按 `Alt+D` 预览图表

## Timeloop 架构概述

### 主要工作流程
1. **定义工作负载**: 指定张量代数问题（如卷积层、矩阵乘法）
2. **指定架构**: 定义硬件模型（存储层次、计算单元、互连网络）
3. **搜索最优映射**: 使用 Mapper 探索映射空间
4. **分析和评估**: 计算性能和能耗指标
5. **生成输出**: 统计信息、配置文件或代码

### 核心组件

#### 1. Mapper（映射器）
- 搜索算法：穷举、随机、混合等
- 多线程并行搜索
- 优化目标：能耗、延迟、EDP（能耗-延迟积）

#### 2. Model Engine（模型引擎）
- 循环嵌套分析
- 性能模型（周期数、利用率）
- 能耗模型（存储、计算、网络）
- 面积估算

#### 3. Workload（工作负载）
- 问题维度定义
- 数据空间规格
- 稀疏性支持（密度模型、元数据格式）

#### 4. Architecture（架构）
- 多级存储层次（DRAM、SRAM、寄存器文件）
- 计算单元（MAC 阵列）
- 互连网络（多播、归约树等）

### 关键特性
- ✅ 密集和稀疏张量代数支持
- ✅ 多级存储层次建模
- ✅ 灵活的互连网络模型
- ✅ 多种搜索启发式算法
- ✅ 能耗和性能协同优化
- ✅ 基于 ISL 的多面体分析
- ✅ Accelergy 能耗模型集成

## 参考文献
- ISPASS 2019: [Timeloop 原始论文](https://parashar.org/ispass19.pdf)
- MICRO 2022: [Sparseloop (v2.0)](https://www.computer.org/csdl/proceedings-article/micro/2022/627200b377/1HMSE23T13a)
- ISPASS 2022: Ruby (v3.0) 不完全因子化映射

## 相关链接
- 官方文档: https://timeloop.csail.mit.edu/
- GitHub 仓库: https://github.com/NVlabs/timeloop
- 教程练习: https://github.com/Accelergy-Project/timeloop-accelergy-exercises/
