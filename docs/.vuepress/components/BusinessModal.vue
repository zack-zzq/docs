<template>
  <div v-if="visible" class="modal-overlay">
    <div class="modal-content">
      <div class="modal-header">
        <h3>Alist商业计划书</h3>
        <button class="close-button" @click="handleClose">×</button>
      </div>
      <div class="modal-body">
        <div class="warning-text"><i class="fa-solid fa-light-emergency-on"></i> 请仔细查看弹窗提示内容</div>
        <div class="modal-text">
          <h4>一、项目背景</h4>
          <p>随着数据存储与共享需求的持续增长，传统的云存储方案正面临隐私安全、成本控制以及数据访问效率等诸多挑战。Alist 网盘应运而生，致力于提供以用户为中心的安全、高效、可控的数据存储方案，并引入人工智能技术实现智能文件管理与检索，在确保用户隐私的前提下，提升用户体验。</p>
          <p><span class="text-red">为了更好地服务用户，满足企业对网盘的战略部署需求以及布局后续的网盘本地化，公司决定进行对开源 Alist 项目进行收购。</span>此次收购紧密贴合企业的长期发展战略，旨在增强公司在企业网盘市场的竞争力，抢占关键的市场份额与战略资源，同时为企业网盘服务奠定坚实基础。</p>
          <p><span class="text-red">收购后，我们将强化数据安全与合规性管控，保障数据主权，确保用户的数据安全与隐私保护。</span>还将整合关键技术能力，提升性能与效率，优化长期运营成本，布局未来技术演进。在这一过程中，我们严格遵循现行法律法规要求，在实现战略价值与保护用户权益之间建立平衡机制。</p>
          <p><span class="text-red-bold">为了精准适配本地 AI 模型，收购后需要统计社区版用户的硬件信息 (CPU、内存、磁盘容量等)，明确主流用户群体的设备配置水平。这一数据收集举措旨在精准优化 AI 模型参数，确保本地 AI 部署的流畅性与高效性，为用户提供更加优质的使用体验。在收集网盘处理用户数据时，我们将严格遵循匿名化处理、数据存储加密、用户同意与透明度三大核心原则。</span>此外，本次收购的另一重要目的是为了整合本地网盘私有化部署的环境。我们注意到当前市面上部分产品利用开源项目进行闭源开发，这不仅存在一定的客户使用风险，也不利于开源社区的健康发展。通过此次收购，我们希望打造一个公开、透明的环境。同时，<span class="text-red">我们致力于开创开源项目商业化后反哺社区的案例先河。在商业化的过程中，我们将积极回馈开源社区，分享技术成果与经验，促进开源社区的持续繁荣，实现开源与商业化的良性互动，</span>为客户和社区创造更大的价值。</p>
          
          <h4>二、产品定位</h4>
          <h5>（一）社区版</h5>
          <p class="list-item"><span class="text-bold">1.免费开放：</span>确保基础功能稳定运营，吸引广泛用户建立口碑，积累大量用户基础。</p>
          <p class="list-item"><span class="text-bold">2.开源协作：</span><span class="text-red">代码完全开源，</span>鼓励开发者社区参与改进与创新，形成良好的开源生态，共同推动产品发展。</p>
          <p class="list-item"><span class="text-bold">3.持续激活开发热情：</span>商业版本将为社区版提供持续的"输血"，<span class="text-red-bold">通过合理分配商业版的部分收益，设立开源贡献奖励基金，对开发者社区中积极贡献代码、优化功能、修复漏洞、积极宣传、整理文档、测试完善的开发者和贡献值给予物质奖励和精神激励。</span>同时，建立开发者荣誉体系，为优秀开发者颁发荣誉徽章、提供展示平台，进一步激发开发者的参与热情，确保社区版的持续更新与优化，让开源社区保持活力，为产品的长期发展提供源源不断的动力。</p>
          
          <h5>（二）企业版</h5>
          <p class="list-item"><span class="text-bold">1.独立部署：</span>支持企业本地服务器或私有云部署，使数据本地化存储与信息主权要求得到满足。</p>
          <p class="list-item"><span class="text-bold">2.付费增值：</span>提供高级权限控制、AI 本地部署（支持多种部署架构与硬件适配）、全文智能搜索、数据安全审计、团队协作功能等。</p>
          <p class="list-item"><span class="text-bold">3.网盘硬件服务：</span>为企业客户提供定制化的网盘硬件解决方案，包括高性能存储服务器、数据中心级存储设备等，确保企业数据的高效存储与快速访问。同时，提供硬件的安装、调试、维护等一站式服务，降低企业 IT 运维负担，保障网盘服务的稳定可靠运行。</p>
          <p class="list-item"><span class="text-bold">4.在线 SaaS 服务：</span>除了本地部署选项外，还提供在线 SaaS 服务模式，企业无需自行搭建服务器和维护硬件设施，即可快速开通使用 Alist 网盘的企业版功能。SaaS 服务模式具备按需付费、弹性扩展的特点，能够根据企业的用户数量、存储空间使用情况等进行灵活计费，帮助企业降低初始投资成本，同时享受专业的产品运维与安全保障服务，确保网盘服务的高可用性和数据的安全性。</p>

          <h4>三、商业模式</h4>
          <h5>（一）社区版运营</h5>
          <p class="list-item"><span class="text-bold">1.免费使用：</span>功能完善，社区驱动更新，保持生态活跃。</p>
          <p class="list-item"><span class="text-bold">2.生态拓展：</span>通过插件系统和开放 API，允许第三方开发者扩展功能，丰富应用场景。</p>

          <h5>（二）企业版销售</h5>
          <p class="list-item"><span class="text-bold">1.基于高级功能订阅模式，</span>提供企业专属的<span class="text-bold">本地化部署</span>方案，可根据企业规模、功能需求定制套餐。</p>
          <p class="list-item"><span class="text-bold">2.对于有特殊需求的企业客户，</span>提供一次性买断选项，同时附带长期技术支持与版本更新服务套餐。</p>

          <h5>（三）增值服务</h5>
          <p class="list-item"><span class="text-bold">1.专属支持：</span>企业客户专属技术支持，包括 7x24 小时在线响应、现场技术支持（根据服务等级协议）、定制化故障排除与系统优化方案。</p>
          <p class="list-item"><span class="text-bold">2.功能定制：</span>依据企业特定业务流程与数据管理需求，提供个性化功能定制开发服务，如定制文件审批流程、数据分类分级管理策略集成等。</p>
          <p class="list-item"><span class="text-bold">3.安全与合规：提供数据安全咨询服务，协助企业构建符合行业标准（如等保二级、三级，GDPR 等）</span>的数据存储与管理体系，包括安全策略制定、合规审计支持等。</p>
          
          <h4>四、核心竞争力</h4>
          <h5>（一）本地 AI 模型部署</h5>
          <p class="list-item"><span class="text-bold">1.完全本地运行：</span>AI 模型在用户本地设备或企业内部服务器运行，无需上传数据至云端，确保数据安全与隐私保护。在企业环境中，支持与内部数据中心的无缝集成，实现数据处理的闭环管理。</p>
          <p class="list-item"><span class="text-bold">2.硬件适配优化：</span>针对不同硬件配置（从个人电脑到企业级服务器）进行深度优化，确保 AI 模型在各类设备上均能高效流畅运行，充分利用现有硬件资源，降低额外硬件投资成本。</p>

          <h5>（二）智能标签化管理</h5>
          <p class="list-item"><span class="text-bold">1.AI 自动标记：</span><span class="text-red">通过先进的 AI 算法自动识别文件类型、内容主题、关联标签等关键信息，提升数据管理效率。支持自定义标签体系，满足企业个性化数据分类需求，方便团队协作与知识共享。</span></p>
          <p class="list-item"><span class="text-bold">2.语义理解增强：</span>基于自然语言处理技术，深入理解文件语义，实现更精准的标签关联与推荐，提升文件检索的相关性和准确性。</p>

          <h5>（三）全文智能搜索</h5>
          <p class="list-item"><span class="text-bold">1.高效精准搜索：</span><span class="text-red">在文档全文内容本地化搜索基础上，结合语义搜索技术，实现模糊搜索、关联搜索、相似文档推荐等功能，帮助用户快速定位所需信息，即使面对海量数据也能游刃有余。</span></p>
          <p class="list-item"><span class="text-bold">2.搜索结果可视化：</span>提供直观的搜索结果可视化展示，如关键词高亮、文档片段预览、搜索结果分类聚合等，提升用户搜索体验与效率。</p>

          <h5>（四）安全与隐私强化</h5>
          <p class="list-item"><span class="text-bold">1.端到端加密：</span><span class="text-red">采用先进的端到端加密技术，确保用户数据在上传、存储和下载过程中始终保持加密状态，只有用户自身掌握解密密钥。</span></p>
          <p class="list-item"><span class="text-bold">2.零知识证明：</span><span class="text-red">引入零知识证明技术，在用户身份验证和数据访问授权过程中，无需向服务商提供任何敏感信息，即可证明用户身份的合法性。</span></p>

          <h5>（五）协作与共享功能优化</h5>
          <p class="list-item"><span class="text-bold">1.实时在线协作：</span>支持用户对同一文件进行实时<span class="text-bold">在线协作编辑</span>，团队成员可以在不同设备上同时查看和编辑文档、表格、图片等文件，所有更改实时同步，方便远程团队协作和项目推进。</p>
          <p class="list-item"><span class="text-bold">2.共享文件夹权限精细化管理：在共享文件夹功能基础上，提供更加精细化的权限管理选项</span>，如可设置不同用户或用户组对文件夹内不同类型文件的只读、写入、修改、删除等权限，以及是否允许下载、分享等操作，满足企业复杂团队协作场景下的权限管控需求。</p>
          <p class="list-item"><span class="text-bold">3.外部协作邀请与访问控制：允许用户邀请外部人员（非本网盘注册用户）参与特定文件或项目的协作</span>，通过设置临时访问链接和访问密码，以及限定访问时限和操作权限，方便与合作伙伴、客户等进行安全高效的合作，无需繁琐的账号注册和权限审批流程。</p>
          
          <h5>（六）用户体验优化与便捷性提升</h5>
          <p class="list-item"><span class="text-bold">1.跨平台同步与无缝切换：</span>确保用户在不同设备（电脑、手机、平板等）和操作系统（Windows、macOS、iOS、Android 等）上使用网盘时，能够实现数据的实时同步和无缝切换。<span class="text-red">用户在一台设备上对文件进行的任何操作，如上传、下载、编辑、删除等，都会立即反映到其他设备上，提供更好的一致性体验。</span></p>
          <p class="list-item"><span class="text-bold">2.离线访问与自动同步：</span>支持用户将常用文件标记为离线可用，在无网络连接的情况下也能正常查看和编辑文件。<span class="text-bold">当设备重新连接网络后，系统会自动检测并同步离线期间的文件更改，确保数据的最新性和一致性，满足用户在移动办公、出差等场景下的使用需求。</span></p>
          <p class="list-item"><span class="text-bold">3.个性化界面与设置：</span>允许用户根据自己的喜好和使用习惯，对网盘界面进行个性化定制，如调整主题颜色、布局风格、文件列表显示方式等。同时，提供灵活的设置选项，用户可以自由配置文件自动备份路径、同步频率、通知方式等参数，使产品更贴合用户的个人使用偏好，提升用户满意度。</p>

          <h4>五、硬件数据收集说明</h4>
          <p>为了精准适配本地 AI 模型，我们需要统计社区版用户的硬件信息 (CPU、内存、磁盘容量等)，明确主流用户群体的设备配置水平，以便精准优化 AI 模型参数，确保本地 AI 部署的流畅性与高效性。</p>

          <h5>（一）收集范围与目的</h5>
          <p class="list-item"><span class="text-bold">1.收集内容：</span><span class="text-red-bold">CPU、GPU 型号，内存大小，操作系统类型与版本，存储设备类型与容量。</span></p>
          <p class="list-item"><span class="text-bold">2.收集目的：</span>优化 AI 模型在不同硬件配置下的性能表现，确保在低配置设备上也能实现基本的 AI 功能，在高性能设备上充分发挥 AI 潜力，提升用户体验。</p>

          <h5>（二）数据收集与保护机制</h5>
          <p class="list-item"><span class="text-bold">1.匿名化处理：所有收集的硬件数据将进行严格匿名化处理</span>，去除任何可直接或间接识别用户身份的信息，确保用户隐私安全。</p>
          <p class="list-item"><span class="text-bold">2.数据存储与加密：收集的数据采用加密存储，限制内部访问权限</span>，仅授权的技术研发人员在必要时可访问，且访问行为将被严格记录与审计。</p>
          <p class="list-item"><span class="text-bold">3.用户同意与透明度：</span><span class="text-red-bold">在首次收集数据前，明确向用户展示数据收集的目的、范围、使用方式及保护措施，获取用户的明确同意。用户可随时在设置中查看、修改或撤回数据收集授权。</span></p>

          <h4>六、发展路线图</h4>
          <h5>（一）短期 (1年内)</h5>
          <p class="list-item"><span class="text-bold">1.功能完善：</span>优化社区版基础功能，提升稳定性与易用性，确保在多平台（桌面端、移动端、Web 端）提供一致的优质体验。</p>
          <p class="list-item"><span class="text-bold">2.企业版开发：</span>启动企业版开发工作，完成核心企业功能的原型设计与初步开发，建立企业客户测试团队，收集反馈并优化迭代。</p>
          <p class="list-item"><span class="text-bold">3.基础 AI 能力部署：</span>在社区版中部署基础 AI 标签功能，初步实现文件自动分类与简单检索优化；同步在企业版中构建支持本地部署的 AI 模型框架，完成与企业内部系统的基本集成。</p>

          <h5>（二）中期 (2-3 年)</h5>
          <p class="list-item"><span class="text-bold">1.企业版推广：</span>加大企业版市场推广力度，与国内系统集成商、行业软件开发商建立合作伙伴关系，拓展销售渠道，覆盖金融、政府、教育、医疗等重点行业领域。</p>
          <p class="list-item"><span class="text-bold">2.AI 功能升级：</span>在企业版中推出高级 AI 全文搜索功能，支持复杂语义查询、多语言搜索、搜索结果智能排序等；强化智能标签化管理功能，实现自动标签更新、标签关联分析等高级特性，提升企业数据治理能力。</p>
          <p class="list-item"><span class="text-bold">3.增值服务拓展：</span>丰富增值服务内容，建立完善的技术支持服务体系，培养专业的客户服务团队，提升客户满意度与忠诚度。</p>

          <h5>（三）长期 (3 年及以上)</h5>
          <p class="list-item"><span class="text-bold">1.行业垂直应用：</span>针对不同行业特点与需求，开发行业垂直解决方案，如金融行业的数据加密与合规存储方案、教育行业的教学资源共享平台、医疗行业的影像数据管理与智能分析系统等，深耕细分市场，树立行业标杆。</p>
          <p class="list-item"><span class="text-bold">2.AI 模型持续迭代：</span>持续投入 AI 研发，跟踪国际前沿技术，结合用户反馈与实际应用场景，不断优化 AI 模型性能，探索新的 AI 应用场景，如智能文档摘要、内容创作辅助、数据智能分析与预测等。</p>
          <p class="list-item"><span class="text-bold">3.生态构建：</span>构建完善的 Alist 网盘生态系统，包括开发者社区、插件市场、行业解决方案合作伙伴网络等，形成互利共赢的产业生态，推动产品持续发展与市场扩张，打造国内领先的智能化、安全性极高的存储解决方案品牌。</p>

          <h4>七、市场策略</h4>
          <h5>（一）社区运营与用户增长</h5>
          <p class="list-item"><span class="text-bold">1.开源社区建设：</span>积极参与开源社区活动，定期发布技术博客、教程文档，举办线上技术分享会与线下开发者沙龙，吸引全球开发者参与项目贡献，提升项目知名度与影响力。</p>
          <p class="list-item"><span class="text-bold">2.用户口碑传播：</span>通过提供优质的产品体验与服务，鼓励用户在社交媒体、技术论坛、行业社区等平台分享使用心得与推荐产品，建立用户口碑传播机制，实现用户自然增长。</p>
          <p class="list-item"><span class="text-bold">3.高校与科研机构合作：</span>与国内高校计算机相关专业、科研机构建立合作关系，开展技术研究、人才培养、实习就业等项目，提前布局人才培养，同时借助学术资源提升技术实力与行业声誉。</p>
          <p class="list-item"><span class="text-bold">4.商业盈利回馈社区成长：</span><span class="text-red-bold">商业版 alist 确保盈利透明化，其税后盈利的 20%用于设立社区版本激励基金，以推动社区的持续成长。</span></p>

          <h5>（二）企业市场拓展</h5>
          <p class="list-item"><span class="text-bold">1.行业标杆打造：</span>优先突破金融、政府、教育、医疗等对数据安全与隐私保护要求较高的行业，为头部企业提供定制化解决方案，打造行业标杆案例，借助标杆效应带动同行业企业客户拓展。</p>
          <p class="list-item"><span class="text-bold">2.合作伙伴计划：</span>制定有吸引力的合作伙伴计划，与系统集成商、软件开发商、云服务提供商等建立紧密的合作关系，共同开拓市场，实现互利共赢。为合作伙伴提供培训支持、技术支持、市场推广支持等，帮助合作伙伴提升产品销售与服务能力。</p>
          <p class="list-item"><span class="text-bold">3.定制化解决方案销售：</span>深入了解企业客户业务需求，提供从需求分析、方案设计、产品实施到售后支持的全流程定制化解决方案销售服务，满足企业差异化需求，提升客户满意度与合作粘性。</p>

          <h5>（三）品牌与技术影响力塑造</h5>
          <p class="list-item"><span class="text-bold">1.技术标准参与：</span>积极参与国内数据存储、隐私保护、AI 应用等相关技术标准的制定工作，树立行业技术领导者形象，提升产品在市场中的话语权与竞争力。</p>
          <p class="list-item"><span class="text-bold">2.行业研究与白皮书发布：</span>定期开展行业调研、发布数据存储与 AI 应用趋势白皮书、行业解决方案白皮书等，分享行业洞察与实践经验，吸引潜在客户与合作伙伴关注，树立专业权威品牌形象。</p>
          <p class="list-item"><span class="text-bold">3.开源项目孵化：</span>在 Alist 网盘技术基础上，孵化相关开源项目，如轻量级本地 AI 框架、分布式存储优化组件等，回馈开源社区，进一步提升技术影响力与品牌知名度。</p>

          <h4>八、风险与应对</h4>
          <h5>（一）数据安全与合规风险</h5>
          <p class="list-item"><span class="text-bold">1.隐私政策强化：</span><span class="text-red">制定清晰、透明、全面的隐私政策，明确告知用户数据收集、使用、存储、共享的具体方式与目的，获取用户明确同意，并定期向用户汇报数据保护情况，接受用户监督。</span></p>
          <p class="list-item"><span class="text-bold">2.合规体系建设：</span><span class="text-red">建立完善的数据安全与合规管理体系，依据《中华人民共和国网络安全法》《中华人民共和国数据安全法》《中华人民共和国个人信息保护法》以及行业相关法规标准，定期进行合规审计与评估，及时发现并整改合规风险点。</span></p>
          <p class="list-item"><span class="text-bold">3.安全技术升级：</span><span class="text-red">采用先进的数据加密技术</span>（如 AES-256、RSA-2048 等）对数据存储与传输进行加密保护；建立完善的访问控制机制，实施最小权限原则，确保只有授权人员在必要时可访问敏感数据；部署安全监测与防御系统，实时监测并防范数据泄露、恶意攻击等安全威胁。</p>

          <h5>（二）技术开发风险</h5>
          <p class="list-item"><span class="text-bold">1.研发团队建设：</span>建立稳固、高效、专业的研发团队，制定合理的人才激励机制与职业发展规划，吸引并留住优秀技术人才。加强团队内部沟通协作，定期组织技术交流与培训活动，提升团队整体技术水平与创新能力。</p>
          <p class="list-item"><span class="text-bold">2.技术选型评估：</span>在技术选型过程中，充分考虑技术的成熟度、稳定性、可扩展性、社区活跃度等因素，避免采用不成熟或存在潜在风险的技术方案。对于新技术的应用，先进行小范围试点与验证，评估其对现有系统的兼容性与影响后再全面推广。</p>
          <p class="list-item"><span class="text-bold">3.敏捷开发与迭代：</span>采用敏捷开发，将产品开发分解为多个迭代周期，每个周期内完成特定功能模块的开发、测试与优化，并及时收集用户反馈，将其融入到下一个迭代计划中，实现快速响应市场变化与用户需求，降低开发风险。</p>

          <h5>（三）市场竞争风险</h5>
          <p class="list-item"><span class="text-bold">1.市场监测与分析：</span>建立专业的市场监测团队，定期对竞争对手产品功能、价格策略、市场份额、用户评价等进行深入调研与分析，及时掌握市场竞争动态，为产品优化与市场策略调整提供决策依据。</p>
          <p class="list-item"><span class="text-bold">2.差异化竞争策略：</span>强化 Alist 网盘的核心竞争力，如本地 AI 部署优势、数据安全保障、智能文件管理功能等，在产品宣传与销售过程中突出差异化特点，满足目标客户群体的特定需求，避免与竞争对手在同质化功能上进行价格战。</p>
          <p class="list-item"><span class="text-bold">3.客户关系管理：</span>加强客户关系管理体系建设，通过提供优质的产品与服务、个性化的解决方案、及时的技术支持与售后服务、提升客户满意度与忠诚度，建立长期稳定的合作关系，增强客户粘性，降低客户流失风险。</p>
        </div>
      </div>
      <div class="modal-footer">
        <button class="cancel-button" @click="handleClose">取消</button>
        <button class="confirm-button" @click="handleConfirm">确认</button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, onUnmounted } from 'vue'

const visible = ref(true)

watch(visible, (newValue) => {
  if (typeof document === 'undefined') return
  if (newValue) {
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = ''
  }
})

onUnmounted(() => {
  if (typeof document === 'undefined') return
  document.body.style.overflow = ''
})

const handleClose = () => {
  visible.value = false
}

const handleConfirm = () => {
  visible.value = false
  // 这里可以添加确认后的逻辑
}

// 暴露方法给父组件
defineExpose({
  show: () => {
    visible.value = true
  }
})
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  border-radius: 8px;
  width: 90%;
  max-width: 600px;
  padding: 20px;
  transition: background-color 0.3s, color 0.3s;
}

html[data-theme="dark"] .modal-content {
  background: #282c34;
  color: #d0d0d0;
}

.modal-header {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  margin-bottom: 15px;
  padding-bottom: 15px;
  border-bottom: 1px solid #eaeaea;
  transition: border-color 0.3s;
}

html[data-theme="dark"] .modal-header {
  border-bottom-color: #3a3f4b;
}

.modal-header h3 {
  margin: 0;
  font-size: 18px;
  font-weight: 700;
  color: #333;
}

html[data-theme="dark"] .modal-header h3 {
  color: #10b981;
}

.close-button {
  position: absolute;
  right: 0;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #666;
}

html[data-theme="dark"] .close-button {
  color: #aaa;
}

.warning-text {
  color: #ff4d4f;
  margin-bottom: 15px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.modal-text {
  color: #666;
  line-height: 1.8;
  margin-bottom: 15px;
}

.modal-text h4 {
  font-size: 16px;
  font-weight: 600;
  color: #333;
  margin-bottom: 10px;
  margin-top: 25px;
}

html[data-theme="dark"] .modal-text h4 {
  color: #e0e0e0;
}

.modal-text p {
  margin-bottom: 15px;
  text-indent: 2em;
}

.modal-text h5 {
  font-size: 15px;
  font-weight: 600;
  color: #444;
  margin-top: 15px;
  margin-bottom: 10px;
}

html[data-theme="dark"] .modal-text h5 {
  color: #c8c8c8;
}

.modal-text .list-item {
  text-indent: 0;
}

.modal-text .list-item strong {
  font-weight: 600;
}

.modal-text .text-bold {
  font-weight: 600;
}

.modal-text .text-red {
  color: #ff4d4f;
}

.modal-text .text-red-bold {
  color: #ff4d4f;
  font-weight: 600;
}

html[data-theme="dark"] .modal-text {
  color: #d0d0d0;
}

.modal-footer {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
  margin-top: 15px;
  padding-top: 15px;
  border-top: 1px solid #eaeaea;
  transition: border-color 0.3s;
}

html[data-theme="dark"] .modal-footer {
  border-top-color: #3a3f4b;
}

.cancel-button {
  padding: 8px 16px;
  border: 1px solid #ddd;
  background: white;
  border-radius: 4px;
  cursor: pointer;
}

html[data-theme="dark"] .cancel-button {
  background: #3a3f4b;
  border-color: #555;
  color: #d0d0d0;
}

.confirm-button {
  padding: 8px 16px;
  background: #10b981;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.confirm-button:hover {
  background: #059669;
}

html[data-theme="dark"] .confirm-button:hover {
  background: #128a65;
}

.modal-body {
  max-height: 60vh;
  overflow-y: auto;
  padding-right: 5px;
}

.modal-body::-webkit-scrollbar {
  width: 6px;
}

.modal-body::-webkit-scrollbar-track {
  background: transparent;
}

.modal-body::-webkit-scrollbar-thumb {
  background-color: #ddd;
  border-radius: 10px;
}

html[data-theme="dark"] .modal-body::-webkit-scrollbar-thumb {
  background-color: #444;
}
</style> 