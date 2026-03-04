# AWS Certified AI Practitioner (AIF-C01) 备考知识点总结

---

## Domain 1: AI和ML基础 (20%)

### Task 1.1: 基本AI概念和术语

#### 核心术语定义

| 术语 | 定义 |
|------|------|
| **AI (人工智能)** | 计算机科学领域，致力于解决通常需要人类智能的问题（感知、推理、学习、问题解决、决策） |
| **ML (机器学习)** | AI的子集，通过数据让机器学习，无需显式编程规则，基于数据进行预测 |
| **Deep Learning (深度学习)** | ML的子集，使用神经网络处理比传统ML更复杂的数据模式，需要GPU和大量数据 |
| **Neural Networks (神经网络)** | 模拟人脑的节点和突触，节点组织成层，通过识别模式来改变节点间的连接 |
| **GenAI (生成式AI)** | 深度学习的子集，用于生成与训练数据相似的新数据（文本、图像、音频、代码、视频） |
| **LLM (大语言模型)** | 设计用于生成连贯类人文本的AI，训练于大量文本数据（书籍、文章、网站），拥有数十亿参数 |
| **Foundation Model (基础模型)** | 在广泛多样的输入数据上训练的模型，训练成本可能达数千万美元 |
| **Computer Vision** | AI处理和理解视觉信息（图像分类、对象检测、图像分割） |
| **NLP (自然语言处理)** | AI处理和理解人类语言（文本分类、情感分析、机器翻译、语言生成） |
| **Algorithm (算法)** | 解决问题或执行任务的步骤序列 |
| **Training (训练)** | 使用数据教模型识别模式的过程 |
| **Inferencing (推理)** | 模型对新数据进行预测的过程 |
| **Bias (偏差)** | 预测值与实际值之间的差异或错误 |
| **Fairness (公平性)** | 确保AI系统不会歧视特定群体 |
| **Fit (拟合)** | 模型与数据匹配的程度（过拟合、欠拟合、平衡） |

#### AI、ML、Deep Learning、GenAI的关系

```
Artificial Intelligence (最广泛)
    └── Machine Learning
           └── Deep Learning
                  └── Generative AI (最具体)
```

**关键区别：**
- **AI**: 有时我们知道"如果这样则那样"的规则
- **ML**: 我们见过很多类似的东西，可以分类
- **Deep Learning**: 没见过某事物，但学习了很多类似概念，可以做决策
- **GenAI**: 基于学到的内容，可以创造性地生成新内容

#### 推理类型

| 类型 | 特点 | 用例 |
|------|------|------|
| **Real-time (实时)** | 数据到达时快速做决策，速度优先于完美准确性 | 聊天机器人 |
| **Batch (批处理)** | 大量数据一次性分析，准确性优先，速度通常不是关注点 | 数据分析 |
| **Edge Inferencing** | 在边缘设备上运行小型语言模型(SLM)，低延迟，可离线工作 | IoT设备 |

#### 数据类型

**按标签分类：**
- **Labeled Data (标记数据)**: 包含输入特征和对应输出标签，用于监督学习
- **Unlabeled Data (未标记数据)**: 仅包含输入特征，用于无监督学习

**按结构分类：**

| 类型 | 描述 | 示例 |
|------|------|------|
| **Structured (结构化)** | 组织在行列中 | 表格数据、时间序列 |
| **Unstructured (非结构化)** | 无特定结构 | 文本、图像 |
| **Tabular (表格)** | 行代表记录，列代表特征 | 客户数据库 |
| **Time-series (时间序列)** | 按时间顺序收集的数据点 | 股票价格 |
| **Image (图像)** | 视觉数据 | 对象识别图像 |
| **Text (文本)** | 非结构化文本 | 客户评论 |

#### 学习类型

**1. Supervised Learning (监督学习)**
- 需要标记数据
- 学习映射函数来预测新数据的输出
- 类型：
  - **Regression (回归)**: 预测连续数值（房价预测、股票价格、天气预报）
  - **Classification (分类)**: 预测离散类别（垃圾邮件检测、动物分类）

**2. Unsupervised Learning (无监督学习)**
- 使用未标记数据
- 发现数据中的模式、结构或关系
- 技术：
  - **Clustering (聚类)**: 基于特征将相似数据点分组（客户细分）
  - **Association Rule Learning**: 发现产品关联（购物篮分析）
  - **Anomaly Detection (异常检测)**: 识别异常数据点（欺诈检测）

**3. Reinforcement Learning (强化学习)**
- Agent通过在环境中执行动作来学习
- 关键概念：Agent、Environment、Action、Reward、State、Policy
- 目标：最大化累积奖励
- 应用：游戏、机器人、金融、医疗、自动驾驶

**4. Semi-supervised Learning (半监督学习)**
- 使用少量标记数据和大量未标记数据
- 伪标记：算法自己标记未标记数据

**5. Self-supervised Learning (自监督学习)**
- 模型为自己的数据生成伪标签
- 使用预文本任务学习数据表示
- 用于NLP（BERT、GPT）和图像识别

**6. RLHF (基于人类反馈的强化学习)**
- 使用人类反馈帮助ML模型更高效地自学习
- 将人类反馈纳入奖励函数
- 用于GenAI应用和LLM模型

---

### Task 1.2: AI的实际用例

#### AI/ML能提供价值的应用场景

- 辅助人类决策
- 解决方案可扩展性
- 自动化
- 医疗诊断
- 欺诈检测
- 语音识别和生成
- 自动驾驶
- 业务流程自动化
- 代码建议
- 智能文档处理（IDP）

#### 何时AI/ML不适合

- **成本效益分析不划算时**
- **需要特定结果而非预测时**（确定性问题）
- **问题可以用简单规则解决时**
- 例：计算抽到蓝牌的概率 - 这是确定性问题，简单代码比ML更准确

#### ML技术选择

| 用例 | 技术 |
|------|------|
| 预测数值（房价、股票） | Regression |
| 分类（垃圾邮件、图像分类） | Classification |
| 客户细分、市场分析 | Clustering |
| 推荐系统 | Personalize |
| 欺诈检测 | Anomaly Detection |

#### 真实AI应用示例

| 领域 | 应用 |
|------|------|
| **Computer Vision** | 面部识别、图像分类 |
| **NLP** | 情感分析、文本分类 |
| **Speech Recognition** | 语音转文字 |
| **Recommendation Systems** | 产品推荐 |
| **Fraud Detection** | 信用卡欺诈检测 |
| **Forecasting** | 需求预测、天气预报 |

#### AWS托管AI/ML服务

| 服务 | 功能 |
|------|------|
| **Amazon SageMaker AI** | 完整ML平台 - 构建、训练、部署模型 |
| **Amazon Transcribe** | 语音转文字 |
| **Amazon Translate** | 机器翻译 |
| **Amazon Comprehend** | NLP服务 - 情感分析、实体提取、主题建模 |
| **Amazon Lex** | 构建对话式聊天机器人 |
| **Amazon Polly** | 文字转语音 |
| **Amazon Rekognition** | 图像和视频分析 |
| **Amazon Textract** | 从文档提取文本和数据 |
| **Amazon Personalize** | 个性化推荐 |
| **Amazon Kendra** | 智能搜索 |
| **Amazon Fraud Detector** | 欺诈检测 |

---

### Task 1.3: ML开发生命周期

#### ML Pipeline组件

```
业务问题 → ML问题框架 → 数据收集&准备 → 特征工程 → 模型训练&参数调优 → 模型评估 → 部署 → 监控 → 迭代
```

**详细步骤：**

1. **Define Business Goals (定义业务目标)**
   - 利益相关者定义价值、预算和成功标准
   - 定义KPI至关重要

2. **ML Problem Framing (ML问题框架)**
   - 将业务问题转换为ML问题
   - 确定ML是否合适
   - 数据科学家、数据工程师、ML架构师和SME协作

3. **Data Processing (数据处理)**
   - 数据收集和集成
   - 数据预处理和可视化
   - **Feature Engineering (特征工程)**:
     - Feature Extraction: 从原始数据提取有用信息
     - Feature Selection: 选择相关特征子集
     - Feature Transformation: 转换数据以提高模型性能

4. **Model Development (模型开发)**
   - 模型训练、调优和评估
   - 迭代过程

5. **Exploratory Data Analysis (EDA)**
   - 用图表可视化数据
   - 相关矩阵：查看变量之间的关联

6. **Hyperparameter Tuning (超参数调优)**
   - Learning Rate: 更新权重的步长大小
   - Batch Size: 一次迭代中使用的训练样本数
   - Number of Epochs: 模型迭代整个数据集的次数
   - Regularization: 调整简单和复杂模型之间的平衡

7. **Deployment (部署)**
   - 选择部署模式（实时、无服务器、异步、批处理、本地）

8. **Monitoring (监控)**
   - 检查期望的性能水平
   - 早期检测和缓解
   - 调试问题

#### 数据集划分

| 集合 | 用途 | 比例 |
|------|------|------|
| **Training Set** | 训练模型 | 60-80% |
| **Validation Set** | 调优参数、验证性能 | 10-20% |
| **Test Set** | 评估最终模型性能 | 10-20% |

#### ML模型来源

- **开源预训练模型**: Meta Llama、Google BERT
- **商业许可模型**: OpenAI GPT、Anthropic Claude
- **自定义训练模型**: 使用SageMaker训练

#### 生产中使用模型的方法

- **Managed API Service**: 托管API服务（如Bedrock）
- **Self-hosted API**: 自托管API（如SageMaker端点）

#### AWS服务对应ML Pipeline阶段

| 阶段 | AWS服务 |
|------|---------|
| 数据准备 | SageMaker Data Wrangler, AWS Glue, AWS Glue DataBrew |
| 特征存储 | SageMaker Feature Store |
| 模型训练 | SageMaker Training Jobs |
| 模型评估 | SageMaker Model Evaluation |
| 部署 | SageMaker Endpoints |
| 监控 | SageMaker Model Monitor |

#### MLOps基础概念

- **Experimentation (实验)**: 尝试不同模型和参数
- **Repeatable Processes (可重复流程)**: 标准化的工作流程
- **Scalable Systems (可扩展系统)**: 能处理增长的负载
- **Managing Technical Debt (管理技术债务)**
- **Achieving Production Readiness (实现生产就绪)**
- **Model Monitoring (模型监控)**
- **Model Re-training (模型重训练)**

#### 模型性能指标

**分类指标（Confusion Matrix）：**
- **Precision (精确率)**: TP / (TP + FP) - 假阳性代价高时使用
- **Recall (召回率)**: TP / (TP + FN) - 假阴性代价高时使用
- **F1 Score**: 2 × (Precision × Recall) / (Precision + Recall) - 平衡精确率和召回率
- **Accuracy (准确率)**: (TP + TN) / (TP + TN + FP + FN) - 平衡数据集使用
- **AUC-ROC**: 曲线下面积，0-1范围，1为完美

**回归指标：**
- **MAE (平均绝对误差)**: 预测值与实际值之差的平均
- **MAPE (平均绝对百分比误差)**
- **RMSE (均方根误差)**
- **R² (R Squared)**: 解释模型中的方差，接近1表示预测良好

**业务指标：**
- Cost per User (每用户成本)
- Development Costs (开发成本)
- Customer Feedback (客户反馈)
- ROI (投资回报率)

#### Bias和Variance

| 概念 | 定义 | 影响 |
|------|------|------|
| **High Bias** | 模型不能紧密匹配训练数据 | Underfitting (欠拟合) |
| **High Variance** | 模型对训练数据变化非常敏感 | Overfitting (过拟合) |
| **Balanced** | 低偏差低方差 | 最佳状态 |

**解决过拟合：**
- 增加训练数据量
- 早停
- 数据增强
- 调整超参数
- 集成学习

---

## Domain 2: GenAI基础 (24%)

### Task 2.1: GenAI基本概念

#### 核心GenAI概念

| 概念 | 定义 |
|------|------|
| **Tokens** | 文本被分割的基本单位（单词或子词） |
| **Tokenization** | 将原始文本转换为token序列的过程 |
| **Context Window** | LLM生成文本时能考虑的token数量 |
| **Chunking** | 将大文本分割成小块以便处理 |
| **Embeddings** | 将文本/图像/音频转换为向量（数值数组） |
| **Vectors** | 高维数值数组，捕获语义含义、句法角色、情感等特征 |
| **Prompt Engineering** | 开发、设计和优化提示以增强FM输出 |
| **Transformer-based LLM** | 能够整体处理句子而非逐词处理的强大模型 |
| **Foundation Models (FMs)** | 在广泛数据上训练的基础模型 |
| **Multimodal Models** | 不依赖单一类型输入/输出的模型（如GPT-4o） |
| **Diffusion Models** | 用于从文本生成图像的模型（如Stable Diffusion） |

#### GenAI潜在用例

- 图像、视频、音频生成
- 文本摘要
- AI助手
- 翻译
- 代码生成
- 客服代理
- 搜索
- 推荐引擎

#### Foundation Model生命周期

```
数据选择 → 模型选择 → 预训练 → 微调 → 评估 → 部署 → 反馈
```

**关键阶段：**

1. **Pre-training (预训练)**: 在大规模数据上训练基础能力
2. **Fine-tuning (微调)**: 在特定领域数据上调整模型
3. **Continuous Pre-training (持续预训练)**: 用新数据持续更新模型
4. **Distillation (蒸馏)**: 将大模型知识转移到小模型，降低成本75%

---

### Task 2.2: GenAI能力和局限性

#### GenAI优势

- **Adaptability (适应性)**: 可适应各种任务
- **Responsiveness (响应性)**: 快速响应
- **Simplicity (简单性)**: 易于使用

#### GenAI劣势

| 问题 | 描述 |
|------|------|
| **Hallucinations (幻觉)** | 生成不准确或虚假的信息 |
| **Interpretability (可解释性)** | 难以解释模型决策 |
| **Inaccuracy (不准确性)** | 输出可能包含错误 |
| **Nondeterminism (非确定性)** | 相同输入可能产生不同输出 |

#### 选择GenAI模型的考虑因素

- Model Types (模型类型)
- Performance Requirements (性能要求)
- Capabilities (能力)
- Constraints (约束)
- Compliance (合规性)
- Model Size (模型大小)
- Context Window (上下文窗口)
- Latency (延迟)
- Multimodal (多模态能力)
- Licensing (许可协议)

#### GenAI业务价值指标

| 指标 | 描述 |
|------|------|
| **Cross-domain Performance** | 跨不同领域执行任务的能力 |
| **Efficiency** | 计算效率、资源利用率 |
| **Conversion Rate** | 生成期望结果（如购买）的比率 |
| **ARPU** | 每用户平均收入 |
| **Accuracy** | 预测准确性 |
| **Customer Lifetime Value** | 客户终身价值 |
| **User Satisfaction** | 用户满意度 |

---

### Task 2.3: AWS GenAI基础设施和技术

#### AWS GenAI服务

| 服务 | 功能 |
|------|------|
| **Amazon Bedrock** | 构建GenAI应用的全托管服务，提供多种FM访问 |
| **Amazon SageMaker JumpStart** | 预训练模型和解决方案模板 |
| **PartyRock** | GenAI应用构建playground（无需AWS账户） |
| **Amazon Q Business** | 企业员工的GenAI助手 |
| **Amazon Q Developer** | 开发者AI代码助手 |
| **Amazon Nova** | AWS自研的FM系列 |

#### Amazon Bedrock核心功能

- **Foundation Models**: 访问多种FM（Claude、Llama、Titan、Stable Diffusion等）
- **Knowledge Bases (RAG)**: 检索增强生成
- **Fine-tuning**: 微调模型
- **Guardrails**: 控制和过滤内容
- **Agents**: 执行多步骤任务
- **Model Evaluation**: 模型评估

#### Amazon Nova模型家族

**理解类：**
- **Nova Premier**: 最强大的多模态模型，用于复杂推理和蒸馏
- **Nova Pro**: 准确性、速度和成本的最佳组合
- **Nova Lite**: 低成本多模态模型，处理图像、视频、文本
- **Nova Micro**: 仅文本模型，最低延迟和成本

**创意类：**
- **Nova Canvas**: 图像生成
- **Nova Reel**: 视频生成

**语音类：**
- **Nova Sonic**: 多语言对话语音理解和生成

#### AWS GenAI服务优势

- **Accessibility (可访问性)**: 易于访问
- **Lower Barrier to Entry (低门槛)**
- **Efficiency (效率)**
- **Cost-effectiveness (成本效益)**
- **Speed to Market (上市速度)**
- **Security & Compliance (安全与合规)**

#### 成本权衡

| 定价模式 | 特点 |
|----------|------|
| **On-Demand** | 按使用付费，无承诺，适合不可预测的工作负载 |
| **Batch** | 批量处理，可享受高达50%折扣 |
| **Provisioned Throughput** | 预留容量，按月计费，适合可预测的工作负载 |
| **Token-based Pricing** | 按输入/输出token计费 |

**成本优化技术（从低到高）：**
1. Prompt Engineering（无额外成本）
2. RAG（无FM变更）
3. Instruction-based Fine-tuning（需额外计算）
4. Domain Adaptation Fine-tuning（需密集计算）

---

## Domain 3: Foundation Models应用 (28%)

### Task 3.1: FM应用设计考虑

#### 预训练模型选择标准

- Cost (成本)
- Modality (模态)
- Latency (延迟)
- Multi-lingual (多语言支持)
- Model Size (模型大小)
- Model Complexity (模型复杂度)
- Customization (定制化能力)
- Input/Output Length (输入/输出长度)
- Prompt Caching (提示缓存)
- Context Window (上下文窗口)

#### 推理参数对模型响应的影响

| 参数 | 作用 | 低值效果 | 高值效果 |
|------|------|----------|----------|
| **Temperature** | 控制输出创造性 (0-1) | 保守、重复、聚焦最可能响应 | 多样、创意、不可预测 |
| **Top P** | 考虑的词汇概率范围 (0-1) | 更连贯的响应 | 更创意多样的输出 |
| **Top K** | 限制可能词汇数量 | 更连贯，较少可能词 | 更多可能词，更多样化 |
| **Length** | 最大答案长度 | - | - |
| **Stop Sequences** | 停止生成的标记 | - | - |

**注意：** Temperature、Top P、Top K不影响定价，影响延迟的因素是：模型大小、模型类型、输入token数、输出token数

#### RAG (检索增强生成)

**定义：** 允许FM引用训练数据之外的数据源

**工作流程：**
```
用户查询 → 搜索知识库 → 检索相关信息 → 增强提示 → FM生成响应
```

**业务应用：**
- 客服聊天机器人（产品、FAQ）
- 法律研究和分析
- 医疗问答

**AWS RAG向量数据库：**
- Amazon OpenSearch Service
- Amazon Aurora PostgreSQL
- Amazon Neptune Analytics
- Amazon S3 Vectors
- Amazon RDS for PostgreSQL

**数据源：**
- Amazon S3
- Confluence
- Microsoft SharePoint
- Salesforce
- Web pages

#### FM定制成本权衡

| 方法 | 成本 | 说明 |
|------|------|------|
| **Prompt Engineering** | 最低 | 无模型训练 |
| **RAG** | 低 | 使用外部知识，无FM变更 |
| **Instruction-based Fine-tuning** | 中等 | 需额外计算 |
| **Domain Adaptation Fine-tuning** | 高 | 需密集计算 |
| **Pre-training** | 最高 | 从头训练 |

#### Agents在多步骤任务中的角色

**Amazon Bedrock Agents功能：**
- 任务协调：按正确顺序执行任务
- 与其他系统、服务、数据库、API集成
- 利用RAG检索信息
- 配置预定义的action groups

**组成：**
- Action Groups（API定义或Lambda函数）
- Knowledge Bases
- Chain of Thought推理

---

### Task 3.2: 有效的Prompt Engineering技术

#### Prompt Engineering概念和构造

| 组件 | 说明 |
|------|------|
| **Instructions** | 模型要执行的任务描述 |
| **Context** | 指导模型的外部信息 |
| **Input Data** | 需要响应的输入 |
| **Output Indicator** | 输出类型或格式 |
| **Negative Prompts** | 明确指示模型不要包含的内容 |
| **System Prompts** | 模型行为和回复方式 |

#### Prompt Engineering技术

| 技术 | 描述 | 使用场景 |
|------|------|----------|
| **Zero-shot** | 无示例，完全依赖模型通用知识 | 简单任务，大型FM |
| **One-shot/Single-shot** | 提供一个示例 | 需要少量引导 |
| **Few-shot** | 提供多个示例引导输出 | 需要特定格式或风格 |
| **Chain of Thought** | 将任务分解为推理步骤序列 | 复杂问题解决 |
| **RAG** | 结合外部数据源生成响应 | 需要实时或专有信息 |
| **Prompt Templates** | 标准化提示生成过程 | 一致性和可重用性 |

#### Prompt Engineering最佳实践

- 提高响应质量
- 实验和迭代
- 使用guardrails
- 发现和探索
- 具体和简洁
- 使用多个注释
- 明确输出格式

#### Prompt Engineering风险和限制

| 风险 | 描述 |
|------|------|
| **Exposure (暴露)** | 敏感信息泄露 |
| **Poisoning (投毒)** | 恶意数据注入 |
| **Hijacking (劫持)** | 重定向模型行为 |
| **Jailbreaking (越狱)** | 绕过安全措施 |
| **Prompt Injection (提示注入)** | 恶意输入劫持提示 |

**防护措施：**
- 添加明确指令忽略无关或恶意内容
- 使用Guardrails过滤

---

### Task 3.3: FM训练和微调过程

#### 训练FM的关键元素

| 元素 | 描述 |
|------|------|
| **Pre-training** | 在大规模数据上训练基础能力 |
| **Fine-tuning** | 在特定数据上进一步训练 |
| **Continuous Pre-training** | 持续用新数据更新模型 |
| **Distillation** | 大模型知识转移到小模型，降低成本达75% |

#### 微调方法

**1. Supervised Fine-Tuning (监督微调)**
- 使用标记的输入-输出对
- 提高模型在特定任务上的性能
- 需要格式化数据存储在S3

**2. Reinforcement Fine-Tuning (强化微调)**
- 使用奖励函数评估响应
- 客观任务：使用AWS Lambda
- 主观任务：使用另一个模型作为"法官"
- 模型从奖励函数输出分数中迭代学习

**3. Instruction Tuning (指令调优)**
- 使用指令-响应对训练
- 提高模型遵循指令的能力

**4. Transfer Learning (迁移学习)**
- 将一个领域的知识应用到另一个领域

**5. Domain Adaptation (领域适应)**
- 在特定领域数据集上训练

#### 微调数据准备

- **Data Curation**: 收集和整理相关数据
- **Governance**: 数据治理和合规
- **Size**: 足够的数据量
- **Labeling**: 正确的标注
- **Representativeness**: 数据代表性
- **RLHF**: 人类反馈强化学习

#### 微调用例

- 特定人设或语气的聊天机器人
- 使用更新信息训练
- 使用专有数据训练
- 针对特定用例（分类、准确性评估）

---

### Task 3.4: FM性能评估方法

#### 评估FM性能的方法

**1. Automatic Evaluation (自动评估)**
- 使用基准问题和答案
- 自动计算分数
- 使用统计方法（BERTScore、F1等）

**2. Human Evaluation (人工评估)**
- 选择工作团队（员工、SME）
- 定义评估指标和方法
- 使用thumbs up/down、排名等

**3. Amazon Bedrock Model Evaluation**
- 内置任务类型：文本摘要、问答、文本分类、开放式文本生成
- 自带或使用内置基准数据集

#### FM性能评估指标

| 指标 | 用途 | 描述 |
|------|------|------|
| **ROUGE** | 摘要、翻译 | 评估自动摘要和机器翻译系统 |
| **ROUGE-N** | - | 测量参考和生成文本之间的n-gram匹配数 |
| **ROUGE-L** | - | 最长公共子序列 |
| **BLEU** | 翻译 | 评估生成文本质量，考虑精确度和惩罚过度简洁 |
| **BERTScore** | 语义相似度 | 使用BERT模型比较上下文嵌入的余弦相似度 |
| **Perplexity** | 语言模型 | 模型预测下一个token的能力（越低越好） |

#### 确定FM是否满足业务目标

- Productivity (生产力)
- User Engagement (用户参与度)
- Task Engineering (任务工程)

#### 评估FM应用性能的方法

- **RAG评估**: 检索相关性、答案准确性
- **Agents评估**: 任务完成率、步骤正确性
- **Workflows评估**: 端到端性能

---

## Domain 4: 负责任的AI指南 (14%)

### Task 4.1: 负责任AI系统的开发

#### 负责任AI的特征

| 特征 | 描述 |
|------|------|
| **Bias (偏差)** | 识别和减少模型偏差 |
| **Fairness (公平性)** | 确保对所有群体公平 |
| **Inclusivity (包容性)** | 包含多样化的数据和观点 |
| **Robustness (鲁棒性)** | 系统稳定性和可靠性 |
| **Safety (安全性)** | 防止有害输出 |
| **Veracity (真实性)** | 确保输出准确真实 |

#### 识别负责任AI特征的工具

**Amazon Bedrock Guardrails:**
- 控制用户和FM之间的交互
- 过滤不良和有害内容
- 移除个人身份信息（PII）
- 增强隐私
- 减少幻觉
- 监控和分析违规用户输入

#### 负责任的模型选择实践

- Environmental Considerations (环境考虑)
- Sustainability (可持续性)
- 较小模型通常更环保

#### 使用GenAI的法律风险

- Intellectual Property Infringement Claims (知识产权侵权)
- Biased Model Outputs (有偏见的模型输出)
- Loss of Customer Trust (失去客户信任)
- End User Risk (终端用户风险)
- Hallucinations (幻觉)

#### 数据集特征

- **Inclusivity (包容性)**: 包含多样化群体
- **Diversity (多样性)**: 多样化的数据来源
- **Curated Data Sources (精选数据源)**
- **Balanced Datasets (平衡数据集)**

#### Bias和Variance的影响

- 对特定人群的影响
- 不准确性
- Overfitting (过拟合)
- Underfitting (欠拟合)

#### 检测和监控偏差的工具

| 工具 | 功能 |
|------|------|
| **Amazon SageMaker Clarify** | 分析偏差、特征重要性 |
| **SageMaker Model Monitor** | 监控生产中的模型 |
| **Amazon A2I (Augmented AI)** | 人工审核工作流 |
| **Label Quality Analysis** | 标签质量分析 |
| **Human Audits** | 人工审计 |
| **Subgroup Analysis** | 子群体分析 |

---

### Task 4.2: 透明和可解释模型的重要性

#### 透明vs不透明模型

| 特性 | 透明模型 | 不透明模型 |
|------|----------|------------|
| 可解释性 | 可以解释决策过程 | 难以解释（黑盒） |
| 信任度 | 更容易获得信任 | 可能引起担忧 |
| 调试 | 更容易调试 | 难以识别问题 |
| 合规 | 更容易满足监管要求 | 可能面临合规挑战 |

#### 识别透明可解释模型的工具

- **SageMaker Model Cards**: 记录模型信息
- **Open Source Models**: 开源模型更透明
- **Data Documentation**: 数据来源文档
- **Licensing Information**: 许可信息

#### 模型安全性和透明度的权衡

- 解释性和性能的平衡
- 安全措施可能降低透明度
- 需要根据用例做出选择

#### 可解释AI的人本设计原则

- 用户能理解AI决策
- 提供适当的解释级别
- 考虑不同用户的需求
- 支持用户控制和纠正

---

## Domain 5: AI解决方案的安全、合规和治理 (14%)

### Task 5.1: 保护AI系统的方法

#### 保护AI系统的AWS服务

| 服务 | 功能 |
|------|------|
| **IAM** | 身份和访问管理（角色、策略、权限） |
| **KMS** | 密钥管理服务（加密） |
| **Amazon Macie** | 发现S3中的敏感数据（PII） |
| **AWS PrivateLink** | 私有访问AWS服务 |
| **VPC Endpoints** | VPC内私有访问服务 |
| **Security Groups** | 网络安全控制 |
| **Encryption** | 静态和传输中加密 |

#### AWS共享责任模型

- **AWS责任**: 云的安全（基础设施、硬件、软件）
- **客户责任**: 云中的安全（数据、应用、访问管理）

#### 数据来源引用和文档

- **Data Lineage (数据血缘)**: 跟踪数据来源和变换
- **Data Cataloging (数据编目)**: 组织和发现数据
- **SageMaker Model Cards**: 记录模型信息

#### 安全数据工程最佳实践

- 评估数据质量
- 实施隐私增强技术
- 数据访问控制
- 数据完整性

#### AI系统安全和隐私考虑

- Application Security (应用安全)
- Threat Detection (威胁检测)
- Vulnerability Management (漏洞管理)
- Infrastructure Protection (基础设施保护)
- Prompt Injection Prevention (提示注入防护)
- Encryption at Rest and in Transit (静态和传输加密)

---

### Task 5.2: AI系统治理和合规法规

#### 协助治理和合规的AWS服务

| 服务 | 功能 |
|------|------|
| **AWS Config** | 跟踪配置变更和合规性 |
| **Amazon Inspector** | 查找软件漏洞 |
| **AWS Audit Manager** | 审计和合规报告 |
| **AWS Artifact** | 获取合规报告（PCI、ISO、SOC、HIPAA） |
| **AWS CloudTrail** | 跟踪API调用审计 |
| **AWS Trusted Advisor** | 安全、性能、成本优化建议 |

#### 数据治理策略

- **Data Lifecycles (数据生命周期)**: 管理数据从创建到删除
- **Logging (日志记录)**: 记录所有活动
- **Residency (数据驻留)**: 确保数据存储在适当位置
- **Monitoring (监控)**: 持续监控系统
- **Observation (观察)**: 观察系统行为
- **Retention (保留)**: 数据保留策略

#### 治理协议流程

- **Policies (策略)**: 定义组织政策
- **Review Cadence (审查节奏)**: 定期审查
- **Review Strategies (审查策略)**
- **Governance Frameworks**: 如Generative AI Security Scoping Matrix
- **Transparency Standards (透明度标准)**
- **Team Training Requirements (团队培训要求)**

#### AWS服务与Bedrock集成

| 服务 | 与Bedrock的应用 |
|------|-----------------|
| **IAM** | 实施身份验证和资源级访问控制 |
| **Guardrails** | 限制特定主题，过滤有害内容 |
| **CloudTrail** | 分析对Bedrock的API调用 |
| **Config** | 查看Bedrock配置变更 |
| **PrivateLink** | 保持所有API调用在私有VPC内 |
| **KMS** | 加密数据 |

---

## 考试范围内的AWS服务一览

### Machine Learning服务
- Amazon Augmented AI (A2I)
- Amazon Bedrock
- Amazon Comprehend
- Amazon Fraud Detector
- Amazon Kendra
- Amazon Lex
- Amazon Nova
- Amazon Personalize
- Amazon Polly
- Amazon Q Developer
- Amazon Q Business
- Amazon Rekognition
- Amazon SageMaker AI
- Amazon Textract
- Amazon Transcribe
- Amazon Translate

### Analytics服务
- AWS Data Exchange
- Amazon EMR
- AWS Glue / Glue DataBrew
- AWS Lake Formation
- Amazon OpenSearch Service
- Amazon QuickSight
- Amazon Redshift

### Database服务
- Amazon DocumentDB
- Amazon DynamoDB
- Amazon ElastiCache
- Amazon MemoryDB
- Amazon Neptune
- Amazon RDS

### Security服务
- AWS Artifact
- AWS Audit Manager
- IAM
- Amazon Inspector
- AWS KMS
- Amazon Macie
- AWS Secrets Manager

### Management服务
- AWS CloudTrail
- Amazon CloudWatch
- AWS Config
- AWS Trusted Advisor
- AWS Well-Architected Tool

### Storage服务
- Amazon S3
- Amazon S3 Glacier

### Compute服务
- Amazon EC2
- Amazon ECS
- Amazon EKS

### Networking服务
- Amazon CloudFront
- Amazon VPC

### Cloud Financial Management
- AWS Budgets
- AWS Cost Explorer

---

## 考试技巧

1. **理解服务定义**: 考试问题通常在高层面，了解每个服务的核心功能
2. **关注Domain权重**: Domain 3 (28%) > Domain 2 (24%) > Domain 1 (20%) > Domain 4/5 (各14%)
3. **熟悉AWS服务映射**: 了解哪些服务用于哪些任务
4. **理解成本权衡**: 了解不同方法的成本影响
5. **掌握评估指标**: 知道何时使用哪种指标
6. **负责任AI**: 理解偏差、公平性、透明度的重要性
7. **安全最佳实践**: 了解IAM、加密、VPC端点等
