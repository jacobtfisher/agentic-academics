---
title: "Honest Caveats"
order: 0
category: foundations
prerequisites: []
---

# Honest Caveats

This project is a practical guide to using agentic AI tools in academic research. It is not an argument that academics *should* adopt these tools uncritically, and it is not a dismissal of the substantial concerns that surround them. Before proceeding, we think it is worth being direct about what those concerns are and how we situate ourselves in relation to them.

## The Environmental Costs Are Real

Large language models are computationally expensive to both train and operate. Training a single large transformer model can produce carbon emissions comparable to the lifetime emissions of multiple automobiles (Strubell et al., 2019), and while inference costs per query are lower, they scale rapidly: the International Energy Agency projects that data center electricity consumption could exceed 1,000 TWh by 2026, with AI-specific demand quadrupling by 2030. Water consumption is similarly consequential. A typical large data center uses roughly five million gallons of water per day for cooling, and indirect water costs from electricity generation can exceed direct cooling costs by an order of magnitude.

These are not hypothetical externalities. They are ongoing, measurable, and disproportionately borne by communities near data center infrastructure. Researchers who use these tools are participating in that demand, and we think it is important to acknowledge that participation honestly rather than wave it away with efficiency comparisons to other technologies.

## The Labor and Deskilling Concerns Are Serious

A growing body of work has begun to examine what happens to skill development when AI tools automate the tasks through which practitioners historically learned their craft. The pattern is consistent across domains: AI augments experienced workers while substituting for entry-level ones, eroding the apprenticeship pipeline through which expertise has traditionally been developed (see, e.g., the American Enterprise Institute's analysis of knowledge economy deskilling). In academia specifically, the tasks most amenable to automation (literature review, data cleaning, preliminary coding, initial drafting) are precisely the tasks through which graduate students and research assistants develop the judgment and domain knowledge that make them effective researchers.

We engage with this concern directly in the [Teach Me, Don't Do It For Me](teach-me-mindset.md) guide, and it is threaded throughout the project. As such, we want to be clear about the position we take: adopting these tools does not require accepting the displacement of human mentorship and training. It does, however, require being intentional about preserving the productive struggle that builds expertise. The risk of deskilling is a reason to use these tools in ways that augment the intellectual work rather than bypass it. Rosenfeld's (2026) honest admission in *Science* that he might not recruit his younger self today is a warning worth heeding, not a future worth accepting.

## Corporate Control of Knowledge Infrastructure Is a Legitimate Worry

As of this writing, a small number of companies (Anthropic, OpenAI, Google, Meta, Microsoft) control the frontier models, the compute infrastructure, and the API access through which agentic AI tools operate. When academics build research workflows around these tools, we create dependencies on systems whose pricing, terms of service, and continued availability are determined by corporate actors with interests that do not necessarily align with those of the research community (Muldoon & Gallo, 2022).

This is not a new problem. Academic research has long depended on commercial infrastructure: proprietary databases, publisher paywalls, licensed statistical software. But the concentration of AI capability in a handful of firms, and the velocity at which these tools are becoming embedded in research practice, makes the dependency particularly acute. We do not have a satisfying resolution to this tension. We note it here because we think any honest guide to using these tools must acknowledge that the infrastructure is not neutral, and that the convenience of the present arrangement does not guarantee its stability or fairness.

## The Harms to Creators Are Documented and Ongoing

The training data that undergirds large language models was, in many cases, sourced from copyrighted work without the consent or compensation of the original creators. As of late 2025, the number of AI copyright infringement cases in U.S. federal courts had more than doubled in a single year, with major litigation pending from news organizations, book authors, visual artists, and musicians. The legal landscape is unsettled, but the ethical question is not: creators whose work was used to build these systems have legitimate grievances, and the eventual resolution (legal or otherwise) will shape the future of AI development in ways that matter to researchers who depend on these tools.

We raise this not to adjudicate the copyright debate but to acknowledge that using AI tools implicates us in it. Researchers who build workflows around language models are downstream beneficiaries of training processes whose ethics are contested. Being aware of that position is, we think, a minimum standard for responsible use.

## Bias, Hallucination, and Epistemic Risk

Language models hallucinate. Studies examining citation accuracy across multiple LLMs have found fabrication rates ranging from approximately 14% to over 90% depending on the model and domain (see, e.g., Xu et al., 2026), and even GPT-4 (one of the better-performing models) has been shown to fabricate roughly one in five citations in simulated literature reviews. Systematic biases in model outputs are similarly well-documented, with persistent gender, racial, and cultural biases appearing across tasks ranging from resume evaluation to news content generation (see, e.g., UNESCO, 2024).

For researchers, these are failure modes that directly threaten the integrity of published work. A hallucinated citation that survives peer review becomes part of the scientific record. A biased model output that informs an analytical decision propagates that bias into findings. The guides in this project repeatedly emphasize the need to verify AI outputs, and we want to be explicit about why: these tools are useful precisely to the extent that you do not trust them blindly.

There is also a subtler epistemic concern. Emerging evidence suggests that widespread use of LLMs produces a homogenizing effect on creative and intellectual output. AI-assisted content is measurably less diverse than content produced through traditional means, and this convergence appears to persist even after AI assistance is removed (Doshi & Hauser, 2024). In academic research, where intellectual diversity and methodological pluralism are essential to the self-correcting function of science, the prospect of AI-driven monoculture warrants serious attention. A recent commentary in *Nature Communications Psychology* (2026) frames this as a risk of "flattening scientific imagination and crowding out the pluralism needed to keep research adaptive, resilient, and intellectually generative." We share that concern.

## Where This Leaves Us

We are not AI optimists in the uncritical sense. We are researchers who have found these tools genuinely useful for specific aspects of our work: managing complexity, surfacing connections, encoding workflows, scaffolding the mechanical parts of research so that more time can be directed toward the intellectual parts. We think it is possible to use these tools thoughtfully while remaining clear-eyed about the costs, risks, and structural inequities they carry.

This guide is written for people who have already decided to engage with agentic AI tools, or who are seriously considering doing so, and who want practical advice grounded in actual use. It is not an argument that everyone should adopt them, and it is not a dismissal of the reasons some colleagues choose not to. The concerns outlined above are not resolved by individual practice — they require collective action at the level of institutions, professional organizations, and policy. What we can do as individual researchers is use these tools in ways that are transparent, critical, and attentive to the harms they may cause.

That is the spirit in which this project is offered.

## References

- Doshi, A. R., & Hauser, O. P. (2024). Homogenization effects of large language models on human creative ideation. *Proceedings of the ACM Conference on Creativity & Cognition*.
- Muldoon, J., & Gallo, M. (2022). Dismantling AI capitalism: The commons as an alternative to the power concentration of Big Tech. *AI & Society*.
- Rosenfeld, A. (2026). Why I may "hire" AI instead of a graduate student. *Science, 391*(6790).
- Strubell, E., Ganesh, A., & McCallum, A. (2019). Energy and policy considerations for deep learning in NLP. *Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics*.
- UNESCO. (2024). *Generative AI: UNESCO study reveals alarming evidence of regressive gender stereotypes*.
- Xu, Z., Qiu, Y., Sun, L., Miao, F., Wu, F., Wang, X., ... & Liu, J. (2026). GhostCite: A Large-Scale Analysis of Citation Validity in the Age of Large Language Models. arXiv preprint arXiv:2602.06718.
