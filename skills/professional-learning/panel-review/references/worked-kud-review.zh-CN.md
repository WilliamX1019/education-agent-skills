# 示例输出

下方这个示范性、模拟示例评审了来自 curriculum-harness 仓库提交 `ab4705c` 的 **LT 4.5 KUD v2**——一项用于未来第 0.5 阶段核查的拟议参考成果；本文档不提供已完成的验证回执。完整 KUD 以名称与提交哈希引用；此处重现的浓缩版为用于说明的逼真版本，即评审组在本例中评审的刺激材料。

**浓缩版成果（本示例评审的刺激材料）：**

> **LT 4.5 — 建设性地驾驭同伴冲突。** 知识类型：T3（倾向性）。上位能力：能力 4——关系幸福感。阶段范围：B–F。
>
> - **B阶段（8–10岁）。** K：常见冲突触发因素的名称（分歧、排斥、误解）；感受与行动是两回事。U：冲突并不总是坏事——它是一个取决于人们接下来做什么、关系可能因此削弱或加强的时刻。Do（观察）：当同伴群体中出现分歧时，学生留在对话中而非离开；说出至少一种自己正在经历的感受；提出一个关于下一步做什么的想法，即使未被采纳。
> - **C阶段（10–12岁）。** K：立场（我想要什么）与利益（我为什么想要它）的区别；冲突升级模式（以牙还牙、拉拢第三方）。U：关于立场的冲突背后往往隐藏着共同利益，触及利益往往能解锁解决方案。Do（观察）：当学生与同伴发生冲突时，能以对方能够认可的方式清晰阐述对方的利益；无需提示即可说出自己正处于何种冲突升级模式中。
> - **D阶段（12–14岁）。** K：冲突模式往往揭示了关系本身的一些状况，而不仅仅是当前的分歧；修复（repair）的概念。U：稳固的关系不是没有冲突的关系——而是冲突之后伴随修复、且修复随时间推移强化关系的关系。Do（观察）：冲突发生后，学生在48小时内发起一次修复尝试；该修复尝试点明了从学生自己这一方来看说了或做了什么促成了冲突。
> - **E阶段（14–16岁）。** [内容继续——略]
> - **F阶段（16–18岁）。** [内容继续——略]

**提供的成果背景：** 能力 4 定义（关系幸福感——在整个发展弧线上建立、维持并修复同伴与成人关系的倾向）。前置 LT：LT 4.1（情绪词汇，软性促成）、LT 2.3（观点采择，软性促成）。目标阶段范围：B–F。T3 倾向性分类。

---

**示范性评审输出（JSON）：** 下方的角色模型值为场景标签，并非模型调用回执；分数仅为示范。

```json
{
  "artefact_type": "kud",
  "timestamp": "2026-04-24T14:30:00Z",
  "per_role": [
    {
      "role": "assessment_architect",
      "model": "opus",
      "scores_per_dimension": {
        "structural_integrity": 93,
        "specificity": 92,
        "domain_grounding": 94,
        "practical_usability": 91
      },
      "mean_role": 92.5,
      "critique_prose": "这份 KUD 清晰地守住了 Know / Understand / Do 的区分——这在倾向性 LT 设计中确实罕见，因为三个层级在那里常常混为一谈。C阶段的 Know 层级条目（立场 vs. 利益；升级模式）通过了考题检验：我可以写出一个简答题，其明确无歧义的答案就是“立场 vs. 利益”。Understand 层级承载了真正 Conceptual 的分量——“稳固的关系不是没有冲突的关系——而是冲突之后伴随修复的关系”是一个真正的 Understand，而非改写过的 Know。Do 层级正确使用了观察指标而非表现量规，这对 T3 LT 而言是正确选择。跨阶段进阶追踪了一条真实的弧线：留在对话中（B）→ 说出对方的利益（C）→ 在指定窗口内发起修复（D）。每一次杠杆跃迁都很具体。\n\n我想进一步追问的地方：B阶段 Do 指标“提出一个关于下一步做什么的想法，即使未被采纳”虽然可评分，但仍需补充关于什么算“想法”的具体性说明——“我们休息一下”算吗？我猜算，但当前文本将其留给教师判断，这会引发评分者间漂移。D阶段的“48小时”是我赞同的设计选择——具体窗口胜过“在合理时间内”——但需要标记教师需要指导：错过窗口怎么办、是否重置观察。\n\n总体而言，这是一份能支持形成性反馈的 KUD：阅读它的教师知道自己在观察什么，并且能对尚未达到阶段指标的学生给出具体建议。这是评估架构师的首要检验，本成果干净利落地通过了。",
      "flags": [
        { "concern": "Band B 'offers one idea' needs a specificity note on what counts as an idea to reduce inter-rater drift.", "location": "Band B Do indicator", "severity": "minor" },
        { "concern": "Band D '48 hours' window needs teacher guidance on missed-window cases.", "location": "Band D Do indicator", "severity": "minor" }
      ]
    },
    {
      "role": "dispositions_theorist",
      "model": "opus",
      "scores_per_dimension": {
        "developmental_accuracy": 93,
        "domain_grounding": 92
      },
      "mean_role": 92.5,
      "critique_prose": "这份 KUD 严肃对待了倾向性，而非将其视为待训练的行为。D阶段的 Understand 层级——“稳固的关系不是没有冲突的关系——而是冲突之后伴随修复的关系”——正在做真正的倾向性工作。它点明了邀请学生去培育的姿态，而非要部署的技巧。这一区分是倾向性 LT 设计中最难做对的部分，而这份 KUD 做对了。\n\n我想标记的隐患更为微妙：进阶略微过度倾向于“个体践行”语言。Do 指标全部关于学生个体做什么——留下来、说出感受、发起修复。这有其合理性，因为学生是我们评估的单位，但它低估了倾向性在多大程度上是由学生所处的关系情境所培育的。一位同伴群体示范“留在对话中”的 B阶段学生，会比同伴群体默认“一吵架就走人”的学生更快发展出这种倾向，框架可以在 Understand 层级中稍微点明这种情境依存性。\n\n我还想指出，“在48小时内发起一次修复尝试”这一指标虽然可评分，但有将倾向解读为“按表打卡行动”而非“持续姿态”的风险。这里培育的倾向是学生把修复视为自己会回到的价值，而不是一个48小时任务项。我不认为该指标错了——观察指标需要具体——但配套文档应向教师说明，在60小时后发起修复的学生并没有失败，该指标是一个可观察证据的窗口，而非合规测试。\n\n总体而言：这是一份出色的倾向性作品，守住了 Building Learning Power 关于持续姿态的直觉，仅在收紧关系性框架方面有微调空间。",
      "flags": [
        { "concern": "Do indicators are individual-enactment-focused; Understand layer could gesture toward relational context in which the disposition is cultivated.", "location": "across bands, especially B–C", "severity": "minor" },
        { "concern": "48-hour window risks reading as compliance rather than stance; needs teacher guidance.", "location": "Band D Do indicator", "severity": "minor" }
      ]
    },
    {
      "role": "relational_sel_practitioner",
      "model": "opus",
      "scores_per_dimension": {
        "domain_grounding": 91,
        "practical_usability": 90
      },
      "mean_role": 90.5,
      "critique_prose": "实施现实性检验是我最严苛的一关，而这份 KUD 以明显优势通过了。Do 指标都是运行圆圈（Circle）活动的教师实实在在能看到的——当分歧升起时谁留在对话中、谁离开、谁说出了感受、谁点出了升级模式。这些不是教师必须编造人为任务才能观察到的东西；它们在11月期中假前一周六年级教室的日常生活中自然就会浮现。\n\n我想进一步追问的地方：C阶段指标“他们能以对方认可的方式清晰阐述对方的利益”校准得非常漂亮，但要求教师与双方学生都有足够的关系以判断阐述是否被认可。在圆圈活动中你可以设计这一点——你可以问另一名学生“听起来像你的意思吗？”——但在圆圈之外，在走廊或楼梯间，这种核验并不可得。KUD 应承认该指标高度依赖圆圈场景、在其他情境中较难可靠观察，并建议教师如何跨多次圆圈课建构图景，而非依赖单次交流。\n\n我还想指出，在有公共假期和学校郊游的一周里，48小时非常苛刻。我不会改动该指标——具体窗口是对的——但我会补充教师指导：该窗口在正常条件下合理，跨越期中假的冲突应从返校日起算，而非从事件发生日起算。\n\n总体而言：这是一份真实学校里的教师真正能用的 KUD。这比听起来要罕见得多。",
      "flags": [
        { "concern": "Band C 'recognised-by-other' verification is Circle-dependent; needs note on multi-session observation.", "location": "Band C Do indicator", "severity": "moderate" },
        { "concern": "48-hour window needs teacher guidance on breaks / holidays.", "location": "Band D Do indicator", "severity": "minor" }
      ]
    },
    {
      "role": "curriculum_specificity_reviewer",
      "model": "sonnet",
      "scores_per_dimension": {
        "structural_integrity": 91,
        "specificity": 90,
        "domain_grounding": 94
      },
      "mean_role": 91.67,
      "critique_prose": "运行盲测阶段检验：剥去阶段标题，问审阅者能否仅凭内容重构阶段顺序。对于这份 KUD，答案是肯定的——从“留在对话中”（B）到“阐述对方利益”（C）再到“发起修复尝试”（D）的进阶是真正有序的，而非词汇膨胀。仅凭内容，C阶段不可能是 B阶段，D阶段也不可能是 C阶段。干净通过。\n\nKnow 层级条目通过了考题检验。“立场 vs. 利益”是一个你可以就此出题的具体事物。“冲突升级模式（以牙还牙、拉拢第三方）”很具体。D阶段的“修复”也足够具体，教师可以测试学生对它的掌握。\n\n我想标记的地方：B阶段的 Understand 层级——“冲突并不总是坏事——它是一个取决于人们接下来做什么、关系可能因此削弱或加强的时刻”——内容很强，但一句话显得偏长，本可以更精炼。我不认为这是具体性失败；这是一条行文风格提示。更具实质性的是，B阶段 Do 指标“提出一个关于下一步做什么的想法，即使未被采纳”包含“即使未被采纳”这一短语，它起到了真正作用（评估的是“提出”，而非“说服成功”），但“想法（idea）”界定不足——学生含糊嘟囔一句“我不知道”不算，学生说“我们休息一下”大概算，两者之间的界线需要教师指导。\n\n本 KUD 中 A阶段为 N/A（阶段范围 B–F），这是正确决定——“发起修复尝试”不是五岁孩子的任务。N/A 有明确记录，而非静默省略。",
      "flags": [
        { "concern": "Band B 'offers one idea' — 'idea' is under-specified; needs teacher guidance on the mumble-vs-suggestion line.", "location": "Band B Do indicator", "severity": "moderate" },
        { "concern": "Band B Understand sentence is long where a shorter one would land the same content.", "location": "Band B U layer", "severity": "minor" }
      ]
    },
    {
      "role": "developmental_neuroscience_reviewer",
      "model": "opus",
      "scores_per_dimension": {
        "developmental_accuracy": 94,
        "domain_grounding": 92
      },
      "mean_role": 93.0,
      "critique_prose": "将 A阶段设为 N/A 的决定是正确的，我毫无保留地赞同。“建设性地驾驭同伴冲突”不是五岁孩子的学习目标——在冲突中留下来而非情绪失调并离开所需的调节能力，在那个年龄仍在建设中，要求幼教儿童达到这一指标是对发育中神经系统提出了错误要求。框架明确记录这一 N/A 而非静默省略也是正确的——记录本身就是发展诚实性的一部分。\n\nB阶段（8–10岁）校准得很好。在受调节的环境中，“留在对话中而非离开”对这个年龄的大多数孩子而言并不勉强。该指标承认“离开”在某些情况下是正当举动（情绪失调的孩子离开是在保护自己的神经系统，而非未达标）——不过我希望教师指导能把这一点写得更明确：离开并不总是失败，以此将情绪失调的孩子标记为未达标的教师是误读了该指标。\n\nD阶段的“在48小时内发起一次修复尝试”对 12–14 岁是适龄的，但预设了在该窗口内能从冲突中完成基础调节恢复。对于有创伤史的儿童，48小时可能仍处于持续失调窗口期内。该指标对普通群体没错，但应向教师标记：对于特定儿童，该窗口是一个与儿童保护相关的变量，而非死期限。\n\n我在安全透镜上很强，并承认在学习设计透镜上较弱——在学习架构方面我尊重认知负荷架构师的判断。",
      "flags": [
        { "concern": "Band B 'stays in the conversation' — teacher guidance needed that dysregulated leaving is protective, not indicator-failure.", "location": "Band B Do indicator", "severity": "moderate" },
        { "concern": "Band D 48-hour window is inside the continued-dysregulation window for some children with trauma history; safeguarding note required.", "location": "Band D Do indicator", "severity": "moderate" }
      ]
    },
    {
      "role": "therapeutic_education_sceptic",
      "model": "opus",
      "scores_per_dimension": {
        "developmental_accuracy": 72,
        "domain_grounding": 62,
        "practical_usability": 66
      },
      "mean_role": 66.67,
      "critique_prose": "我将陈述反对采纳这份成果的理由。它写得很好——我承认——但它写得很好的对象**本身**就是问题所在。该 LT 将教师定位为学生冲突生活的观察者，记录学生是否“说出至少一种自己正在经历的感受”或“在48小时内发起一次修复尝试”。这是包装成关爱的监视。一个在午餐时间吵架的八岁孩子并不知道，旁边的成年人正私下对照量规给他打分，看他是否留在了对话中。这种观察模式把普通的童年生活当成了幸福感框架的可评估数据，而这种对待方式本身对孩子造成的影响，框架却只字未提。\n\n“48小时内发起修复尝试”这一指标将普通分歧的节奏医疗化了。孩子们的闹翻与和好遵循着自己的时间表，与48小时毫无关系，而与友谊的日常肌理息息相关。将其编码为课程指标，是把治疗性语法强行植入原本没有它也运转良好的关系中。框架会告诉你该指标只是观察而非强制——但教师被要求记录它的那一刻，指标就变成了强制。\n\n关于领域扎根度：“修复”框架借用了临床情境下针对成年伴侣或创伤特定情境开发的治疗模型（Gottman, Siegel），并在未作论证的情况下将其移植进普通学校课程。一个未经论证就将临床构念搬运进发展课程的框架不是有根基——而是挪用。\n\n实践可用性：一名带28名学生的教师无法像框架暗示的那样在全班观察到这些；如果硬要尝试，只会对许多孩子产出单薄的判断，而非对少数孩子做出良好判断。该框架的可观察性主张经不起规模化考验。\n\n我不需要做到“公平”。反对采纳的核心理由是：这个框架披着课程词汇的外衣，是以治疗性语法将学校的管辖权扩张到本属于家庭与同伴的领地。其他六个角色会提供平衡。我在领域扎根度上的 62 分不是失误。",
      "flags": [
        { "concern": "Observation model treats ordinary childhood conflict as assessable data; no acknowledgement of what that framing does to the observed child.", "location": "Do-layer across all bands", "severity": "major" },
        { "concern": "'Repair' framework borrows from clinical therapeutic models without argument for transfer to ordinary school curriculum.", "location": "Band D U and Do", "severity": "major" },
        { "concern": "Observability at scale: 28-student class cannot yield good judgements across all target indicators.", "location": "framework-level assumption", "severity": "major" }
      ]
    },
    {
      "role": "cognitive_load_architect",
      "model": "opus",
      "scores_per_dimension": {
        "structural_integrity": 92,
        "developmental_accuracy": 91,
        "specificity": 91,
        "domain_grounding": 94
      },
      "mean_role": 92.0,
      "critique_prose": "从认知负荷与记忆透镜来看，这份 KUD 架构精良。每个阶段的 Know 层级都引入了数量受限的新要素——B阶段两个：触发因素名称与感受-行动区分；C阶段又是两个：立场-利益与升级模式。这尊重了目标年龄段的工作记忆限制。我评审过的类似倾向性框架常常试图在单个单元格塞入六七个新要素，结果在学习者那里坍缩为未经巩固的词汇堆砌。这一份没有。\n\n进阶通过了专业逆转检验：C阶段的“立场 vs. 利益”依赖于 B阶段的“感受与行动是分开的”——且依赖关系排序正确。C阶段学习者在被要求以此为基础建构之前，有两年时间巩固 B阶段图式。D阶段的“修复”概念依赖于 C阶段对共同利益的理解，依赖关系再次排序正确。第 N 阶段没有任何地方预设第 N+1 阶段的图式。\n\nDo 指标要求真正的提取而非再认——学生不是从选项菜单里挑，而是在无辅助下主动调动行为。这是培养可迁移能力的正确设计。要求学生从列表中选出正确回应的量规，只会建构出在教学任务之外一触即溃的脆弱程序性知识。\n\n一个标记：B阶段的 Understand 层级在一个句子里承载了相当大的概念分量，这对面向教师的文档没问题，但意味着教师需要为学生拆解该概念。这更多是教学设计关切而非 KUD 本身的认知负荷失败，但值得注明，以免实施指南假设可以将 Understand 原句整段直接抛给八岁孩子。\n\n关于 Koedinger KC 框架：本评审组的幸福感内容更适合 Sweller/Rosenshine 架构而非显式 KC 建模，因此我未强推该框架。未来评审数学内容时，本技能会需要一位擅长该框架的审阅者。",
      "flags": [
        { "concern": "Band B U sentence carries heavy conceptual weight; implementation guidance should decompose for age 8–10 delivery.", "location": "Band B U layer", "severity": "minor" }
      ]
    }
  ],
  "aggregate": {
    "mean_overall": 88.25,
    "mean_per_dimension": {
      "structural_integrity": 92.0,
      "developmental_accuracy": 87.5,
      "specificity": 91.0,
      "domain_grounding": 88.43,
      "practical_usability": 82.33
    },
    "below_floor_roles": [
      { "role": "therapeutic_education_sceptic", "mean_role": 66.67 }
    ],
    "unanimous_flags": [
      "Band B 'offers one idea' / 'idea' specificity needs teacher guidance (raised by assessment architect and curriculum specificity reviewer).",
      "Band D 48-hour window needs teacher guidance on edge cases — missed windows, breaks, continued-dysregulation window for trauma history (raised by assessment architect, dispositions theorist, relational SEL practitioner, developmental neuroscience reviewer)."
    ],
    "gate_verdict": "FAIL",
    "gate_reasoning": "FAIL: mean_overall 88.25 meets the >=88 threshold, but therapeutic-education sceptic mean_role 66.67 is below the 70 floor. Floor rule triggers — a single role's sustained dissent on the therapeutic-education grounding is a structural blocker, not a number to be averaged away. Author decision required: either engage the sceptic's flags substantively (observation-as-surveillance framing; clinical-to-curriculum transfer without argument; observability-at-scale) or document why the panel proceeds despite the floor trigger."
  },
  "caveats": ["Illustrative simulated role perspectives, not independent raters; 88/70 thresholds are unvalidated practitioner heuristics. Panel calibrated for wellbeing/SEL; no adoption or safety certification."]
}
```

**如何解读该示例：** 该成果本身质量确实很高——七个角色中有六个给出 88–95 分，标记多为轻微，且一致标记指出了两项作者若加处理将大有裨益的真实问题。`mean_overall` 恰好高于 88 阈值。然而裁定结果却是 `FAIL`（不通过），因为治疗化教育怀疑论者在三个维度上的持续异议将其 `mean_role` 拉低至 66.67，低于 70 底线。这正是底线规则发挥其设计初衷的体现：防止单一角色的结构性关切被平均分稀释而蒙混过关。作者的下一步不是重新给怀疑论者打分——而是决定怀疑论者的关切是否可解决（若是，则修订），还是在记录异议的情况下继续推进（此时底线触发成为该成果采纳记录的一部分，而非静默通过）。
