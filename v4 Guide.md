# Taxonomy guide: noslegal v 4

7 May 2026

In this guide,[^1] we 

* indicate who we are and why we’ve created the noslegal taxonomy  
* explain why it is designed as it is  
* introduce what’s in it  
* outline how to adopt it in practice. 

We’ve written this for a broad audience \- we hope it’s helpful to you whether you are evaluating it, implementing it in your organisation, building technology that uses it, or interested in contributing to its development. You don’t need any prior knowledge of taxonomy design or data architecture.

# Contents

1. **Introduction** \- Who we are, why noslegal exists, and the problems it addresses. Includes a plain-language explanation of what a taxonomy is and why a monohierarchical design is right for this context.  
2. **Context** \- The three types of organisation the taxonomy serves — legal services providers, in-house teams, and legal technology companies — and the four areas of need: delivery, knowledge, pipeline and people.  
3. **Design** \- Five principles behind the taxonomy's design: monohierarchy, faceting, modest size and extensibility, stability, and the three-tier structure of Work types and Areas of law. Why each choice was made and what it enables.  
4. **Coverage** \- A systematic introduction to all eight facets — scope, content, key distinctions, implementation notes and development plans. Read this to understand what the taxonomy contains and how facets interrelate.  
5. **Implementation** \- How to adopt the taxonomy in practice: data governance, data structures and fields, classification process and software design, migration from existing systems, and the organisational factors that determine whether implementation succeeds.  
6. **Across the four needs** \- Good taxonomy implementation across delivery, knowledge, pipeline and people. Specific guidance on how each facet applies in each area, and how value compounds when concepts are used consistently across all four.

This guide and related materials are available via [our website](https://www.noslegal.org/taxonomy/).

# 1\. Introduction *\- the who, why and what of noslegal*

## 1.1 Who we are

We are an open source community of lawyers, software and data specialists, legal business and knowledge professionals founded in 2020.[^2] Our largest project so far has been the taxonomy addressed in this guide.

Our ethos is "open source legal for all of us", reflected in five principles: 

* **open source** (free to use, study, modify and redistribute for any purpose);[^3]   
    
* **community-based**, but with contribution governed for quality;   
    
* **useful** in practice, not just theoretically interesting;   
    
* **simple and modular**, so outputs can be combined, remixed and extended;   
    
* **broadly relevant** to work types, areas of law and internationally. Not based on a single legal culture and with local and specialist needs addressed through extensions bearing in mind the risks of overloading the core.

## 1.2 Our taxonomy and the problems it helps with

Since we released v1 of our taxonomy in 2022, substantial elements have been adopted or used as a starting point by a growing number of law firms, legal departments, and technology providers around the world. 

The reason is a structural problem familiar to most legal organisations. Legal work generates enormous amounts of data across matters, knowledge, people and business development. But it typically sits in silos, organised inconsistently if at all. The practical costs are significant: time wasted searching for information that exists but cannot be found; decisions made without access to relevant experience; pricing and planning based on personal experience and intuition rather than historical data; missed opportunities to identify patterns, anticipate demand or demonstrate credentials.

Private taxonomies have mostly failed to solve this. Huge numbers have been created over the years, but they tend to be over-fitted to particular contexts, fragmented by function or geography. They deteriorate over time as design stagnates or accumulates inconsistencies. They’re often poorly implemented. And their diversity makes it impractical to map them one-to-one between organisations (e.g. law firm to client).

Modern technology (such as search, graphs, machine learning and language models) holds out the promise of helping significantly, but only when built on an appropriate data foundation. With that foundation in place, the practical benefits compound quickly: better search, better analysis, better knowledge reuse, and the conditions for AI to operate effectively across and between organisations. These improvements in turn open up better outcomes across quality, pricing, service, accessibility and sustainable business models. Our taxonomy provides an important part of that foundation.

## 1.3 What is a taxonomy anyway?

A taxonomy is a tree of concepts addressing a particular topic. Ours is monohierarchical: every child concept has a single parent. The diagram below illustrates the structure and standard terminology.

We believe a monohierarchical taxonomy is the right choice for the practical purposes addressed in this guide. Its tree structure is more powerful than a flat list of words, definitions and synonyms for most relevant purposes. But it is more accessible to more people and organisations than a full ontology (i.e. flexible relationships, not just monohierarchical ones). See section 3.1 for further discussion of this.

# 2\. Context \- *who the taxonomy is for, and where it helps*

## 2.1 Three types of organisation

The noslegal taxonomy is designed to support three types of organisation:

* **Legal services providers** \- lawyers and others who practise law and provide related services. This includes traditional professional organisations such as law firms and barristers' chambers, not-for-profit providers such as law centres, and alternative legal services providers (ALSPs).

* **In-house legal services** \- the legal departments of businesses and larger public bodies. These do some legal work directly and manage the sourcing of other work from legal service providers. They operate under particular pressure to demonstrate value, control spend and manage an ever-broadening range of legal risk, often with tight resources.

* **Legal technology companies** provide software and, in some cases, information used either by the first two groups or directly by end users such as individuals and small businesses.

The taxonomy is **not** specifically designed for legal authorities (courts, regulators, law enforcement), legal research, teaching, or theoretical and academic law. These areas tend to make jurisdiction-specific and legal-conceptual demands that would undermine the practical, internationally neutral focus of noslegal. This is not a criticism, it’s just a choice we have made in order to stay focused. If you’re working in these areas, or anything else, you are of course free to use, modify and extend noslegal if you do find it relevant.

## 2.2 Four areas of need

Legal organisations rely on structured information about their work across four broad areas. These areas overlap and interact \- and the value of a shared taxonomy is precisely that data generated in one area becomes useful in the others.

1. **Delivery.** Scoping, planning, pricing, executing and managing the work, including adjustment of plans and pricing as matters evolve.

2. **Knowledge.** Capturing, structuring and making available insights and materials that support legal work, drawing on the organisation’s collective experience as well as external resources.  
     
3. **Pipeline.** Understanding, anticipating and influencing what work is upcoming or available. Within a legal services provider, it includes marketing, business development, credentials and client relationships. For in-house legal teams, it includes forward planning, resourcing, managing the flow of work from the business, and handling legal services provider relationships.  
     
4. **People.** Understanding and communicating what experience and skills an organisation’s people have so that work can be resourced effectively. Also determining what’s missing so that gaps can be filled by recruitment, training, secondments or in other ways.

These four areas overlap and interact in ways that make it desirable for the higher-level concepts used in each to correspond. 

| Examples of how these needs benefit from shared concepts  A law firm will ideally target its marketing and sales activities (Pipeline) on areas which can generate significant amounts of worthwhile work (Delivery), make relevant learnings as to how to do so effectively and profitably (Knowledge) and generate credentials (People) which can support marketing and sales (Pipeline again) and help those doing the work in future (Delivery again and People).    An in-house team delivering legal work (Delivery) generates know-how and financial data (Knowledge) that can inform how similar work is planned, resourced (Pipeline), priced and managed in future (Delivery again), including how it is staffed and how career development is supported (People). |
| :---- |

The core functions in these four areas of need are often handled by separate groups within many legal services providers, each with its own characteristic software applications. The result is that the same underlying work tends to be described differently across functions \- making it difficult to connect insights, identify patterns, or reuse what has been learned. 

Using a shared high-level taxonomy helps to address this. It avoids the constant mapping and remapping exercise that arises when different functions, or different organisations working together, maintain their classifications independently. 

Needs will typically diverge at lower levels of detail. For example, a knowledge management function will typically have more need for more granular legal concepts and sub-concepts than a team focused on financial reporting or business development. But this can be handled by extending the taxonomy to meet such specialist needs without disturbing the shared higher-level concepts on which interoperability depends.

## 2.3 Approaches to information which noslegal enhances

Legal work has always depended on finding and reusing information generated elsewhere. Digital technology has already extended this considerably in recent decades. New varieties of AI are now making new approaches feasible. All of this benefits from a reliable, consistent conceptual skeleton.

Well-established approaches, enhanced with a strong taxonomy, include:

* **Search:** finding something you can describe. Taxonomy improves precision by ensuring that what was classified under a given concept can be found under that concept, not a near-synonym or a different organisational convention.  
* **Alerts and dashboards:** flagging developments and keeping views current based on defined rules. Taxonomy provides the stable categories on which those rules depend.  
* **Rule-based assembly:** producing reports and documents based on predefined rules and selections. Taxonomy supplies the selection criteria.

These are useful but can be limited by the active engagement they require and a tendency to return too much. Newer approaches using non-deterministic technology such as machine learning and language models include:

* **Contextual retrieval:** returning not just what was asked for but what is likely to be helpful. Taxonomy enables pre-filtering of the corpus before a model processes it, improving both relevance and performance (see section 6.2).  
* **Question answering:** addressing queries directly rather than pointing to search results. Taxonomy provides some meaningful structured context to help a model identify authoritative sources and assess coverage gaps.  
* **Generative assembly:** producing reports and other outputs from loosely specified requests. Taxonomy anchors what the model draws on, reducing the risk of plausible but poorly grounded outputs.  
* **Process-linked surfacing:** presenting relevant information at the step the user has reached, or raising something they ought to address. Taxonomy, combined with process elements (section 4.7), is what links the step to the information.  
* **Agentic AI:** taking action without seeking confirmation. Taxonomy can be used to constrain the scope within which an agent operates. It can also provide a classification layer against which its actions can be audited.

Each approach has limits and risks, and in practice they work best in combination. A shared taxonomy is what makes that combination practical. Different approaches can operate over the same classified corpus without each needing its own organisational scheme.

## 2.4 Examples of use cases

Across the four areas of need noslegal is designed for, the approaches just listed can be used in many ways. This table gives just a few examples with a deliberate mix of ones for legal services providers and legal departments.

|  | At matter level | Across a portfolio |
| :---- | :---- | :---- |
| **Delivery** | What should the plan be for this matter \- work, deliverables, assumptions, budget? Where are the high-risk areas? How might fixed pricing work out here, based on previous matters? At this stage, what are the things that need to be covered? | What kinds of work have we handled for this client or business unit? What types generate the greatest cost or risk? Where do we see recurring overruns we could manage more effectively? |
| **Knowledge** | How should I approach this issue? What has our organisation said or decided about this before? How has it worked out in practice? | What context can we share for future work? How proportionate and up to date are our knowledge resources relative to the work we actually do? Where are the gaps? |
| **Pipeline** | (To help with sourcing) Have we faced matters like this before \-  who did them and how did it go? (To help win work) What experience can we point to for this pitch review? | What patterns are we seeing across our work? Where is demand growing or declining? Where are we under- or over-resourced? (Provider) What are our realisation rates across different kinds of work and where can we improve? (In-house) Where is demand from the business increasing and how should we plan for it? |
| **People** | (To help with resourcing) Do any of our lawyers have capacity and experience in this kind of matter? | (To help with people development) Are we spreading experience widely enough to support development? Where should we focus training and in-context help? |

# 

# 3\. Design \- *principles which make the taxonomy effective*

The noslegal taxonomy reflects a set of deliberate design choices. These are not constraints imposed for their own sake. They reflect considered judgements about what makes a taxonomy practically useful across a wide range of legal organisations and contexts. This chapter highlights five key choices.

### 

## 3.1 Monohierarchy

Each concept in the taxonomy has only one direct parent. This makes the taxonomy simpler to understand, implement and maintain than a more flexible ontology. This is an important consideration given the limits on specialist expertise available in many relevant organisations.

The monohierarchical constraint is less limiting than it may intuitively sound. Nuanced characterisation of matters, knowledge items and portfolios is still possible through faceting (section 3.2) and careful field design (section 5.2). A well-designed taxonomy adds substantial value fairly simply. You can extend into something more complex later if truly beneficial compared with other options for addressing relevant needs. Complexity has a way of multiplying, so keeping it simple and taking things in stages is usually best.

## 3.2 Faceting

The taxonomy is organised into distinct facets, each addressing a different dimension of legal work. This allows a relatively small number of concepts in each facet to express nuance when used in combination with others.

Without faceting, a monohierarchical taxonomy trying to capture "energy litigation" would need to choose whether energy or litigation was the parent concept, or duplicate concepts under two parents. A faceted approach resolves this by placing energy and litigation in separate facets, with the combination describing the full picture.

The diagram below shows how a matter involving arbitration in Singapore concerning a trade union dispute in the mining sector in Indonesia can be fully described by combining concepts across the work type, area of law, sector and place facets. This allows powerful reporting and analysis, aggregating by process, sector, legal area or geography, as well as precise search, where someone looking for credentials or knowledge on "Asia labour dispute natural resources" can retrieve a matter classified in exactly those terms.

## 

## 

## 3.3 Modest size, modularity and extensibility  

We have deliberately kept the taxonomy to a modest size for four reasons.

* **Simplicity aids accuracy.** The biggest problem most organisations have with their structured data is incorrect data as opposed to insufficient detail. Over-complication overwhelms people when classifying matters and documents, and greater detail makes boundary questions more frequent. There is a trade-off to manage. Simple classifications are often both sufficiently valuable and more accurate.

* **AI works better with a reliable skeleton.** Search and language model technology work best in a legal context when anchored to concepts which have been chosen for their meaningfulness. As opposed to leaving a language model to decide what is meaningful case by case. A modest, reliable taxonomy makes noslegal more valuable as AI capability grows, not less.

* **International applicability requires restraint.** Commonality between legally relevant concepts across countries breaks down as one goes deeper into detail. Keeping the core relatively simple preserves its usefulness across jurisdictions.

* **Comprehensibility matters.** noslegal is intended to be understandable by a broad range of people, not only taxonomy specialists. The core can be adequately grasped by a human reader in a few hours. This also makes it easier to review, agree and maintain reliably over time.

Where more detail is useful, the design is extensible. Several extension packs have already been published within noslegal, and anyone can produce more privately or publicly. Specialist depth can be added without over-complicating the shared higher-level concepts on which interoperability depends.

## 3.4 Stability and updates

Our goal is to keep the core facets as stable as possible so that organisations can adopt with confidence. We will continue to make incremental improvements, refine and add extension packs, and introduce further facets where genuine need is demonstrated by the community. More significant changes will be highlighted in the relevant release notes together with the reasons.

## 3.5 Limited levels in work types and areas of law

The Work types and Areas of law facets are the most conceptually contestable in the taxonomy, because their subject matter can be, and in practice is, organised in different ways across legal cultures internationally. Both are structured in three tiers: category, type and topic.

**Category (first tier)** provides broad groupings useful for high-level reporting. Some room for debate about allocation is inevitable, for example, where the boundary lies between Finance and Transaction. Some departure from the recommended structure at this level is acceptable if your organisation has a good reason for it or even if organisational politics make it pragmatically necessary.

**Type (second tier)** is the critical one for interoperability. Concepts at this level \- Arbitration within Dispute resolution, M\&A within Transaction \- represent the core interoperable layer of the taxonomy. Consistency at this level is what makes data exchange meaningful when mapping between systems or organisations. Organisations should treat second-tier alignment as close to non-negotiable. Every departure generates a cost to manage downstream.

**Topic (third tier)** is intentionally flexible and illustrative rather than prescriptive. Organisations are encouraged to define their own topics to reflect their specific practice areas, provided they map back to the relevant type above. This is where customisation is expected and appropriate, and where extension packs can add further depth.

This three-tier approach applies specifically to Work types and Areas of law because of their combination of size and inherent subjectivity. The other facets are different in character:

* **Places** and **Sectors** draw on well-established external standards \- ISO country codes and ISIC/NACE respectively \- which provide an independent anchor.

* **Participants** and **Information assets** address topics that are more straightforward to define internationally.

* **Process elements** has different structural needs, but the decision not to break phases into structured tasks is analogous to the distinction between the second and third tiers here.

# 4\. Coverage *\- the scope and content of noslegal*

The noslegal taxonomy is organised into seven[^4] facets, each describing a distinct dimension of legal work: Work types, Areas of law, Participants, Sectors, Places, Process elements and Information assets. This section introduces each facet and explains the relationships between them. For full detail, please refer to the release notes and to the facets themselves.

### **Combinatorial use**

The facets are designed to be used together, and much of their power lies in combination. A matter or knowledge item described across multiple facets can be retrieved and analysed along any of those dimensions individually or in combination. This is what enables the practical capabilities described in section 2 \- from identifying relevant experience for a pitch, to surfacing knowledge at the moment it is needed, to understanding patterns across a portfolio of work. The diagram in section 3.2 illustrates this.

### **The eight facets**

The Work types facet is, for many practical purposes, of central importance. Five others cover dimensions central to legal work characterisation (Areas of law, Participants, Roles, Sectors, Places). The other two address the internal structure of law-related activity and its artifacts (Work elements, Information assets). But the ordering is for presentational purposes \- they are all important, with the precise relevance depending on context.

This table summarises the size and content of each facet. The rest of this chapter summarises the approach taken in each of the seven facets.

## 

| Facet | Indicative size |
| :---- | :---- |
| **Work types** | 8 categories, 42 types, numerous topics within types. 1 extension pack for UK-specific topics. |
| **Areas of law** | 16 general and 17 sectoral categories \- 33 in total. 68 general and 52 sectoral types \- 120 in total. Numerous topics within types. 2 extension packs for UK- and EU-specific topics.  |
| **Participants** | 3 groups (person, property, obligation), each with 3 principal types and a total of 7 sub-types. 2 extension packs \- 1 for person features, 1 for UK law organisation types. |
| **Roles** | 16 groups of roles \- anchored to work types (8 groups, 44 roles), areas of law (6 groups, 26 roles) or more general (2 groups, 4 roles).  |
| **Sectors** | 16 core sectors with 65 sub-sectors. 2 extension packs: 1 with 17 additional financial services sub-sectors, 2 with 11 older NACE sectors. |
| **Places** | 249 core areas. 10 extension packs covering (1) non-English names, (2) UN regions, (3) super-regions, (4) legal systems for core areas, (5) legal systems for selected core areas’ sub-divisions, (6) legal system types, (7) over 5,000 area subdivisions, (8) subdivision types, (9) over 1,700 treaty and international organisation memberships and (10) 55 treaties and international organisations. |
| **Process elements** | Glossary with 4 sections and 44 concepts. 8 process maps.  |
| **Information types** | 4 dimensions \- type, use, status and audience together with a grid illustrating type x use combinations. |

## 

## 4.1 Work types

The **Work type** facet classifies legal activity by its purpose, independent of the law, sector or place engaged. 

Since v3, the categories have been sharpened into eight, each with a distinct purpose.

| Category (alphabetical) | Purpose |
| :---- | :---- |
| **Development** | Creating or building something new or substantially amending or transforming it. |
| **Dispute resolution** | Resolving a dispute over rights, obligations, liabilities and remedies. |
| **Enablement** | Enabling someone to achieve personal, business, policy or other goals with reference to a particular legal context. This is a residual category: if another work type is applicable, it should be used instead |
| **Finance** | Handling the financial aspects of a transaction, development, dispute or other matter. Often used in conjunction with another work type but also independently (for example, a refinancing or fund formation with no underlying transaction) |
| **GRC and policy** | Managing or supporting governance, risk, compliance and law-related policy issues and initiatives |
| **Investigative process** | Finding out or demonstrating what has or has not happened, including through formal inquiries, investigations and prosecutions |
| **Dissolution and restructuring** | Winding up an organisation or relationship. Also restructuring and turning things around after financial or other problems. Also winding up a relationship or estate of an individual. |
| **Transaction** | Changing status, ownership, rights and obligations. Includes contracting and working through the legal consequences of such changes. |

### **Characteristic process types**	

The primary distinction between the above categories is their purpose, as stated above. In practice,  many also have a process with common characteristics, though this varies with context (jurisdiction, sector, organisation and more). The fact that the distinctions drawn are relevant both by way of purpose / type-of-value and by way of the type of process (and thus by way of skill / experience) makes them relevant across delivery, knowledge, pipeline and people.

### **Three levels within Work types**

As described in section 3.5, Work types has a three-level structure. The categories above can be combined differently if useful (for example by introducing super-categories). Types (the second level) are the most important for mapping between organisations and should be used without modification where possible. For the third level, noslegal suggests some examples, but organisations are encouraged to extend these to reflect their own context.

### **Topic extension packs for work types**

We have created an extension pack at topic level for the UK. The coverage is modest in this release \- essentially a proof of concept \- but we may expand it for the UK and to other places if there is demand. When implementing, simply add these topics to the ones in the work types core if these UK topics are relevant to your organisation.

### **Key implementation points**

We recommend giving each matter a single second level work type. Where a matter develops a substantial element of a materially different work type (for example, where a corporate transaction gives rise to significant litigation), a new sub-matter or linked matter should be opened for that work. Mixing materially different work types in a single matter undermines financial reporting, like-for-like comparison and knowledge management. A sensible materiality threshold should be defined. The third level need not be mandatory and may usefully allow more than one tag, with the emphasis on knowledge and experience capture rather than financial reporting.

### **Future development**

We hope not to change the first or second levels of v4 significantly, at least over the next few years, and consider this facet sufficiently mature to prioritise stability. The third level is deliberately looser and likely to expand over time. Extension packs may also be added to cover specialist work types in particular countries, sectors or other contexts (for example, different types of arbitration).

## 4.2 Areas of law

The Areas of law[^5] facet classifies the legal subject matter engaged by the work, independently of the work type, sector or place.

### **Basis of distinctions**

The Areas of law facet classifies legal work by the body of law engaged, rather than by the purpose, process,  industry context or linked places of legal work or materials. 

The facet is organised into two broad groups. 

* **General areas of law** are bodies of law applicable across sectors and contexts: contract law, intellectual property law, tax law and so on.   
* **Sectoral laws** are defined by their close relationship to a particular industry or area of economic activity: financial services law, energy law, healthcare law and so on. They are accordingly placed in a separate tab of the taxonomy spreadsheet with cross-references to the **Sectors** facet.

The distinction does not need to be reflected in your implementation unless it is useful, and both groups can be treated as parts of a single facet. We have made it nonetheless because separating sector-specific from general areas reduces complexity in the general categories, allows organisations to disregard sectoral laws of no relevance to their practice, and \- for law firms in particular \- provides a second route to identifying sector context where that has not been captured directly in the Sectors facet.

The distinction between work type, general area of law and sectoral law \- and why separating them matters \- is well illustrated by financing activity. Finance is a work type: it classifies the kind of activity being undertaken. Financial law is a general area of law: it classifies the body of private law doctrine governing the obligations between lenders, borrowers and counterparties \- the law of credit, security and financial market contracts. Financial services law is a sectoral area of law: it classifies the regulatory framework applicable to authorised firms in the financial services industry. A syndicated loan to a corporate borrower involves Finance as the work type, financial law as the primary general area of law, and may or may not engage financial services law depending on whether regulatory issues arise. A regulatory investigation of a bank involves a different work type entirely \- GRC and policy, or investigative process \- with financial services law as the primary area of law. Each combination accurately describes the matter without forcing any one concept to carry more than it should.

### **General areas of law**

There are 17 categories in the general areas of law. Full definitions are provided in the taxonomy itself, but some short notes here are intended to help grasp the structure and the cross-facet relationships of some categories. 

Brackets give the number of types in each category.

| Category (alphabetical) | Notes |
| :---- | :---- |
| **Corporate law (5)** | This has been reworked since v3 as five types covering important dimensions of the topic |
| **Cross-border laws (4)** | The private international law type will likely be used together with other areas of law to describe a matter. |
| **Evidence and procedural law (2)** | This is new in v4 and addresses the legal issues (e.g. the procedural and evidential law on disclosure of documents) as opposed to the purpose and process of related work.  |
| **Family law (4)** |  |
| **Financial law (6)** | Finance is pervasive in much legal work. Our taxonomy  now handles it in three ways. Substantive law relating to financial matters is here in Areas of law. This is contrasted with work done for a financial purpose (see Work types) or financial services-sector-specific law and regulation (see Sectoral laws) |
| **Information law (5)** | This covers some areas of law of great and growing significance, divided into five major types. It has been clarified and slightly reworked since v3. |
| **Insolvency and restructuring law (3)** | Substantive law relating to insolvency as opposed to insolvency process (see Work types). Public insolvency has been added since v3. |
| **Intellectual property law (8)** | Indication of origin has been added since v3 |
| **Labour law (3)** | Modestly restructured by v3 by merging employee benefits and private pensions law. |
| **Land law (3)** | In v4, law relating to land, including environmental law, is now separated out from real estate sector-specific law for similar reasons as for finance (above) \- reflecting the pervasiveness of the topic. The precise distinction is defined via the types. Note that the Development type within Work types will often be relevant in connection with Land law but is not confined to land-related contexts. |
| **Obligations law (4)** | This is law of obligations in the civilian law sense of contract, delict / tort and restitution / unjust enrichment. In v4, we have separated out agency as a separate topic in view of its importance, and its distinctiveness from the law of contract. Equity is not separated out, though, as this is rather system-specific. |
| **Personal affairs (3)** | Capacity and care in v3 have been narrowed to Personal capacity in order to eliminate an overlap with Care in Sectoral laws. |
| **Personal property law (2)** | Goods and intangible property (including digital assets, but not intellectual property) have now been split out from Obligations law. |
| **Public law (2)** | This covers constitutional / administrative law in its institutional and process aspects with a separate types for rights. Note that aspects of this are covered in Information law instead (notably, freedom of expression and privacy)  |
| **Regulatory (7)** | This is somewhat residual, containing major types of regulation (e.g. competition law, climate law) which do not fall into other categories. |
| **Tax law (2)** |  |
| **Wrongdoing (5)** | This is a residual category to cover wrongdoing which does not arise in a more specific category. Categorisation of the particular type of law involved in a particular case (e.g. criminal or civil) is achieved by using the relevant work type (e.g. prosecution, litigation or, in the event of no formal process, the enablement \> advice type with a suitable topic tag for criminal, civil etc). |

### **Sectoral laws**

This is a new extension pack within v4. Its categories map one-to-one to those in the Sectors core. In addition, there is a category for professional services law mapping to a Sectors extension pack, as that area is quite significant for some law firms even though not significant at the scale of whole economies.

Sectoral law taxonomies are in some cases broken down in a way which mirrors the sub-sectors. For example, for transportation law the economic breakdown between marine, air etc seemed the best fit for the legal breakdown. Likewise with real estate breaking down by commercial, residential and rural in both contexts. In the case of manufacturing we concluded that a split into product safety, industrial operations and chemicals made most sense as legal subdivisions. Financial services law contains a hybrid of sub-sectoral and sector-level legal types.

At the third level \- topics \- the distinctions are very much legal ones.

### **The three-level structure**

As with Work types, Areas of law uses a three-tier structure of category, type and topic. The general/sectoral split sits at category level. Within each category, types represent the core interoperable layer: concepts such as Contract law within Obligations law, or Banking law within Financial services law. 

We suggest treating first- and second-tier alignment as close to non-negotiable: every departure generates a cost to manage downstream. The third tier (topics) is where highly specific sub-areas naturally live, and can be modified more flexibly.

### **Topic extension packs for areas of law**

We have provided four extension packs for areas of law covering general and sectoral topics for the UK and EU. These are relatively small so far but may be expanded in future if there is demand. Simply add them to the topics in sheets 2.0 and 2.1 when implementing if these UK and EU aspects are relevant to your organisation.

### **Key implementation points**

Unlike Work types, a one-and-only-one requirement at the second tier may be artificial for Areas of law, since multiple areas often apply to a single matter in complex and entangled ways that cannot readily be separated into sub-matters. 

A corporate restructuring, for example, may simultaneously engage corporate law, insolvency law, tax law and financial services regulation in ways that are not unbundleable in the sense of “I am currently working on X not Y.” 

One practical approach for financial reporting purposes may be to seek to capture a single primary area of law \- the one most central to the matter as a whole \- while allowing additional areas \- for knowledge purposes \- to be tagged at any level. This is imperfect, but selecting a primary area at a fairly high level (type or even category) provides a basis for financial reporting and portfolio analysis; the additional tags enrich the knowledge and experience record without the rigidity that a one-to-one rule would impose.

Third-tier topics are best treated as optional for matter- and document-tagging purposes. They are not intended to be taxonomically watertight in the way that the first two levels seek to be. They should be used primarily for knowledge and experience purposes. Where the same topics are used across matter records, knowledge assets and people profiles, the interoperability benefit described in section 3.5 can be obtained.

The sectoral laws categories add a practical point about field design. Where a matter falls within a sectoral laws category, it will often also engage one or more general areas of law (for example, a banking regulation matter will often engage obligations law and perhaps public law as well). The two work together to give a complete picture.

### **Future development**

The general areas of law categories are now sufficiently mature that significant change at category or type level is not anticipated over the next few years.

Sectoral laws are more likely to expand: sector-specific law has in recent decades often developed faster than more general, foundational legal categories. Expansion in sectoral laws will, as elsewhere in the taxonomy, be managed at topic (third) level first, but may lead to creation of additional types (second level) over time. Extension packs may also be added to cover areas of particular local relevance that do not warrant inclusion in the internationally applicable core.

## 4.3 Participants

The Participants facet covers the persons, property and obligations typically involved in legal work. It provides vocabulary for describing who and what is involved in a matter, beyond the type of work being done and the areas of law engaged, allowing important distinctions to be captured without overloading the Work types or Areas of law facets.

### **Further extension packs**

Two extension packs are available. One covers **features** particularly relevant to legal services providers for classifying clients and other entities. The other covers **incorporated and unincorporated bodies recognised under UK law**, illustrating the kind of local extension that can usefully be built out from the core.

### **Future development**

As with Work types and Areas of law, stability is now a priority. Where further conceptual growth is needed, extension packs are the preferred route, to avoid overloading the core and the Roles extension pack.

## 4.4 Roles

The Roles facet classifies the position of persons involved in a legal matter (for example, claimant or defendant in litigation, buyer or seller in a transaction, employer or employee in an employment matter). Implementation guidance for Roles, including how to link role availability to work type or area of law, is available in section 6.1.

## 4.5 Sectors

The Sectors facet classifies the area of economic activity relevant to a matter or client. It is derived from version 2.1 (2022) of the NACE standard (European Union), itself an extension of the ISIC standard (United Nations), structured as two levels and mapped to NACE. We have made several modifications for more convenient use in legal work:

* The core is structured as two levels, with some adjustments to NACE groupings for legal relevance  
* An extension pack contains lower-level concepts often relevant to legal work in financial and professional services  
* A second extension pack contains NACE concepts removed from the core on the ground that they are of less relevance to much modern legal work

The aim is a convenient core that can readily be adopted, with the extension packs available for additional concepts where useful.

### **Implementation guidance**

The Sectors facet should be used to classify both matters and clients, and these are distinct data points. A matter concerning an energy company leasing a new office is more usefully classified in the real estate sector than the energy sector, because the relevant experience and knowledge concerns real estate rather than the client's industry. The client's sector is captured separately on the client record.

For legal services providers, it is worth classifying clients by their sector or sectors of activity. Where conglomerates are active across multiple sectors, client record design should allow for this. Consider applying sector classification not only at client group level but also to the particular entity or department involved in a specific matter.

### **Future development**

We have no current plans for significant development of this facet but welcome suggestions. One possibility would be adding a mapping to the NAICS standard, which is derived from the former US SIC standard and covers the needs of the US-Mexico-Canada trade agreement (USMCA). We chose ISIC and NACE as the primary basis for their broader international relevance, but a NAICS mapping could be a useful addition for organisations operating primarily in North America.

## 4.6 Places

The Places facet classifies the geographic and jurisdictional dimensions of a matter. It is the largest noslegal facet by number of concepts, most of which are derived from the ISO 3166 standard covering countries, their subdivisions and the global regions to which they belong.

We have built on ISO 3166 to meet legal work needs in several respects:

* Distinguishing the 249 ISO "areas" from independent countries with UN membership by linking dependent areas to their UN members.  
* Shortening names where convenient \- for example, "United States of America (the)" to "United States."  
* Defining non-ISO super-regions (EMEA, AMER, APAC) including variants. These may be implemented alongside the standard geographic continents as a polyhierarchy, or as an alternative to them.  
* Identifying legal system types at ISO-area level and, in three cases (US, UK and Canada), at lower level.  
* Adding some additional subdivisions to the UK and UAE.  
* Tracking membership of 55 international organisations and treaties. Where a single country or territory is a member of multiple treaties or organisations, this is modelled by way of membership lists, which in practice are straightforward to work with.

In v4, we have confined ourselves to updating the facet to incorporate ISO 3166 updates and changes in membership of treaties and international organisations already covered in v3.

### **Implementation guidance**

Places is an area where lax guidance frequently produces ambiguous and unreliable data. This is because place can mean several materially different things in a legal context. We suggest distinguishing and capturing separately at least.

* **Governing law.** The legal system whose rules apply to the matter.  
* **Dispute resolution forum.** The legal jurisdiction or place of arbitration in which a dispute is or may be decided.   
* **Asset or event location.** Where relevant assets are situated or key events occurred.  
* **Client location.** Where the client is based.

Conflating these produces data that is not useful for either knowledge or reporting purposes. 

Further nuances within the above broad concepts may be captured in specific contexts if useful e.g. multiple governing laws applying to different issues and nuanced concepts of personal location e.g. registered office, residence and domicile.

## 4.7 Process elements

The Process elements facet (called Work elements in v3) addresses the phases, key steps, work and deliverables commonly involved in particular types of legal work. It has two components.

### **Glossary**

The first component is a core vocabulary of concepts used to describe and manage legal work in practice: matters, phases, objectives, milestones, tasks, assumptions and related financial and process concepts. This provides a shared language for legal project management that connects directly to the taxonomy. With the advance of language models, this will be useful for guiding extraction and translation of process information.

### **Process maps in v4**

The second component is a set of process maps, which are worked examples showing how that vocabulary applies to particular types of legal work. Process maps set out typical phases, objectives, tasks, milestones and assumptions for a given work type, and may be further defined by area of law, participant type, role, sector, place or other context. Where useful, more specific process maps are nested within broader ones, to support comparability across jurisdictions and contexts. Together, the core vocabulary and process maps provide a basis for more consistent planning, pricing and reporting of legal work, and for building the matter data that supports knowledge reuse and process improvement over time.

We released initial process maps in v3, addressing finance, commercial real estate and dispute resolution work. In v4 the format has been updated in several respects: the former "Key steps" column has been reframed as "Phase objectives" to sharpen its focus; "Work commonly includes" has been renamed "Tasks"; a "Matter objectives" field has been added; and each phase now includes columns for milestones, assumptions and phase type. The "Notes" column has been removed as unnecessary given the additional structured columns.

### **Future development**

We anticipate that Process elements will grow significantly in future releases, both in the core vocabulary and in the range of process maps available.

## 4.8 Information types

The **Information types** facet[^6] defines concepts for describing categories of document and other material in which legally relevant information is found. Tab 5.0 of the taxonomy spreadsheet contains the core.

### **Two main dimensions: type and use**

The facet works across two orthogonal dimensions, each captured in a separate extension pack.

* **Type** (the core, nine concepts) describes what a piece of information intrinsically is: a legal document, legal analysis, legal source, process material, administrative material, evidence, organisational record, publication or communication. Type is an inherent property of the material and does not change with context.  
* **Use** (XP5.1, five concepts) describes the role the material plays in a particular organisational context. Unlike type, use is assigned by a person or process, can be multiple, and can change over the material's lifecycle. The five uses divide into two overlapping groups:

  * The **work record** uses apply at matter or remit level, with a distinction between **general** and **key**.

  * The **knowledge** uses reflect a progression of relevance:  
    * **canonical** material represents the organisation's definitive approach to a topic and supersedes other guidance on the same subject;  
    * **good practice** material has been reviewed and endorsed as useful guidance for the organisation generally;  
    * **contextual** knowledge is useful to those dealing with the same client or subject matter, but has not been validated more broadly.

|  |  | Knowledge \- relevant beyond matter level |  |  |
| ----- | :---- | ----- | :---- | :---- |
| Work records \> general | Work records \> key | Knowledge \> contextual | Knowledge \> reusable | Knowledge \> canonical |
| Work records \- relevant at matter / remit level |  |  |  |  |

A document's use classification is not fixed at creation. A final advice letter might be classified initially as work record \> key; if later reviewed and endorsed by a knowledge lawyer, it becomes knowledge \> good practice. This progression is a feature of the design, not an anomaly. The governance notes in XP5.1 address when and how promotion between use levels should be authorised.

### **The grid**

The grid in tab "Grid 5.1 Type x Use" illustrates which type/use combinations are significant, using colour coding to indicate where meaningful examples exist and where a combination is unlikely to arise in practice.

To take one example: a final executed agreement is legal document (inf-1) by type. At matter level it is work record \> key (inf-use-2). If subsequently curated as a useful precedent, it also carries knowledge \> good practice (inf-use-4). The two use classifications coexist; the type does not change.

### **Two more dimensions**

Two further extension packs cover status (draft, final, fluid) and intended audience (internal and external with sub-types of each).

### 

### **Key implementation points**

We suggest enforcing:

* a single information type for a given document or other item  
* one or more information uses  
* a single status  
* one or more audiences

### **Information types, uses and AI**

The type and use classifications have a particular value in AI-assisted retrieval that goes beyond what the other facets provide. Work type, area of law and sector tell a retrieval system what kind of matter a piece of material relates to. Type and use tell it what kind of material it is and how much weight to give it.

This enables more discriminating pre-filtering of the corpus before a model processes it. A query about how to approach a particular transaction type can be directed first at canonical and good practice materials \- the organisation's validated guidance \- rather than across the full document store. A query that is specific to a client relationship or other context (e.g. a product line) can draw on contextual knowledge for that client alongside broader good practice material. Without use classifications, a model has no structured basis for making these distinctions and must either process everything or rely on its own judgement about what is authoritative.

The progression from contextual to good practice to canonical also means that the quality of the AI-accessible corpus improves incrementally as human review accumulates. Each endorsement decision enriches the structured layer from which the model draws. This is one of the more direct ways in which investment in knowledge governance compounds into AI performance over time, without requiring any change to the underlying model.

# 5\. Implementing the taxonomy in practice

Knowing what the noslegal taxonomy contains is one thing; implementing it successfully is another. This chapter addresses the practical and organisational considerations involved. Sections 5.1 to 5.4 cover the technical foundations. Sections 5.5 to 5.8 address the human and organisational factors that determine whether an implementation succeeds or stalls. Chapter 6 then addresses how to apply the taxonomy across the four areas of need.

## 5.1		Data governance

Data governance is the framework of decisions, policies, accountabilities and practices that determine how data is created, classified, maintained and trusted over time. It is the organisational infrastructure that makes the difference between a taxonomy that is applied consistently and supports decision-making, and one that exists only as a conceptual model alongside day-to-day practice.

### **Ownership and accountability** 

A major reason legal organisations struggle with data quality is not that they lack the right software. It is that accountability for data has never been clearly defined. This lack of clarity creates a risk of the data falling between functions and individuals. Challenges with data management or data quality are then addressed reactively  when something goes wrong (often by those with least authority to stop the problem happening again) rather than proactively as a matter of organisational design. For noslegal purposes, the following governance issues deserve particular attention.

Data should be treated as an organisational asset, not the property of a particular team. But within that, clarity is needed on who is accountable for the quality of specific data sets (data owners) and who has day-to-day responsibility for maintaining that accuracy (data stewards). This distinction matters. Data Owners are accountable for outcomes: where the data is trusted and used, and for cross-team collaboration. Data Stewards are responsible for day-to-day mechanics:  how classifications are applied, reviewed, and corrected.

In a legal services provider, data ownership should sit with senior leaders who have the authority to ensure sufficient priority and appropriate resources are devoted to the topic (for example, partners managing each practice group and senior managers within knowledge, business development and human resources). Depending on the organisation, stewardship for matter data might sit with someone in practice management or a specialist business services role.

In an in-house team, ownership should sit with the general counsel or a sufficiently senior director of legal operations. Stewardship will likely sit with someone else in a legal operations role.

In a technology company building on noslegal, ownership and stewardship should be designed into the product team from the outset (for example, with the head of product or head of legal content as owner).

### **Quality standards**

Start by identifying which data points matter most: those that flow between systems, appear in reporting, or are shared with clients or other organisations. For noslegal purposes, the critical data points are the taxonomy classifications themselves (work type, area of law, sector, place and role).

Standards do not need to be complex; they should define what “good enough” looks like for the decisions the data supports, which combinations are implausible, and how errors are detected and corrected. Precision is more valuable than exhaustiveness.

### **Strategic focus** 

A recurring failure mode is treating data governance as a set of operational tasks (fixing individual errors, running periodic clean-up exercises) without any strategic framework to prevent those errors recurring. Effective governance requires decisions at multiple levels: what data do we need and why; how should it be structured and governed; and who does what, when and how. A taxonomy implementation is an opportunity to establish this kind of explicit decision making structure about what data the organisation needs, how it should be structured and governed, and who is responsible at each stage of its lifecycle, not just to classify data.

### **Starting with people, not policy**

The instinct to begin a data governance initiative by drafting a policy document is common but rarely sufficient. Building a community of people who understand and care about data quality across the functions that generate and use it tends to produce more durable results (often called “bottom-up data governance”) This is particularly true in legal organisations, where the individuals with the most influence over data quality are often hard to reach through formal policy alone. Documentation still matters, but it is most effective when it codifies practices people already understand and support, rather than attempting to impose behaviour in isolation.

## 5.2		Data structures and fields

A taxonomy provides a structured vocabulary for describing legal work but does not by itself determine how it is used in practice. That is the role of data structures: the design of the fields, records and schemas that capture information about the things your organisation works with and wants to understand. Important examples in a noslegal context include matters, clients (for legal services providers) and providers (for in-house teams), documents and other knowledge assets, credentials and individual experience records.

### **Different types of field**

Each of these needs a defined set of fields that together describe it adequately. Some fields will draw directly on the noslegal taxonomy (a matter record should include fields for work type, areas of law and roles, for example). Others will have nothing to do with taxonomy (client name, matter number, responsible individuals, fee arrangements, opening and closing dates, financial data). Both are equally important parts of the data structure.

This distinction matters because treating taxonomy adoption as synonymous with data structure design risks overloading the taxonomy with too much detail, while under-designing the data structure by focusing only on classification fields.

### **Fields need a clear purpose**

Before defining fields, be clear about what questions the data structure needs to answer. Fields and their constraints (mandatory or optional, single or multiple values, taxonomy-based or free text) should follow from those purposes rather than from a general instinct to capture as much as possible. A smaller number of accurately populated fields is almost always more valuable than a larger number applied inconsistently.

### **Consistency across structures**

One of the principal benefits of a shared taxonomy is that the same concepts appear in multiple data structures: matter, knowledge and people records can all reference the same work type and area of law concepts, making it possible to connect experience, knowledge and work without extensive manual mapping. This benefit is only realised if the fields drawing on the taxonomy are designed consistently across structures. What matters most is avoiding ambiguity in what is being captured. A field called "jurisdiction", for example, used to mean governing law in one context, dispute resolution forum in another and asset location in a third, will produce data that is unreliable for any purpose.

## 5.3		Process and technology for applying taxonomy to data

Well-designed taxonomy and data structures achieve little if the process and software by which classifications are captured and maintained are ineffective.

### **A common failure mode: matter classification**

Classifying a matter upon opening, and rarely revisiting it, creates several compounding problems. At the moment of opening, relatively little may be known about the matter's nature. The person completing the opening form is frequently not the person with the best knowledge of the matter, and their primary motivation is to open the file quickly so that work can begin. Classifications made in these circumstances are often inaccurate, incomplete or defaulted to whatever has been used before. If classification data is then buried in a finance or matter management system that fee earners cannot easily see, there is no natural prompt to correct it.

### **Better process**

Deliberate process redesign is needed rather than hoping people will classify more carefully. Practical approaches include the following.

* **Defer and revisit.** Design the process so that classification is completed or checked at a later point, building prompts into workflows rather than relying on individuals to take the initiative.

* **Make classification visible.** Classification data should be visible to the people doing the work. If a matter's work type, area of law and sector are displayed in the matter workspace that lawyers actually use, errors become apparent and there is a natural prompt to correct them.

* **Make amendment easy.** The process for correcting a classification should be straightforward, ideally a simple update by the relevant fee earner or supervisor without requiring form-filling, though you may want to incorporate software-based notifications and approval requirements in contexts which benefit from some restrictions: financial reporting, for example, does not have exactly the same needs as knowledge. The important point here is that friction in the amendment process is a direct cause of persistent bad data.

* **Use data stewards actively.** Data stewards should not wait for errors to be reported. Periodic review of classification data (checking for implausible combinations, unused concepts or blank fields) is an important part of the stewardship role. Stewards should have the tools to identify problems, the authority to make some corrections, and support in querying suspected errors with those best placed to confirm them.

* **Anticipate special cases.** Some classification decisions are likely to confuse people unfamiliar with the underlying issues. For example, a matter spanning multiple work types, or a knowledge asset relevant across several areas of law. Produce explicit guidance and, where possible, software prompts to help people navigate these cases consistently.

### **Software design**

Process design and software design are closely linked. Points worth bearing in mind include the following.

* **Expose classification data.** Classification data should appear in the interfaces that lawyers and others closest to the work actually use (matter workspaces, knowledge portals, experience databases), not only in administrative or financial systems. If people don’t see it, it’s less likely to be corrected.

* **Surface definitions and guidance.** When asking people to classify something, present the definitions and other guidance they need within the software flow, in as digestible a form as possible.

* **Use rules to reduce error.** If someone has already identified that work is transactional, the next step in the classification flow should emphasise transaction-related roles (buyer, seller) and suppress litigation-related ones (claimant, defendant).

* **Use rules to raise queries.** Identifying when someone from the litigation department is entering substantial time on a transactional matter, for example, can be used to raise queries with the lawyers involved or to give data stewards clues about what to investigate.

* **Machine learning and AI.** Consider using machine learning and language model technology to classify or test classifications. Questions of cost and proportionality apply, and appropriate human involvement is important. These approaches are likely to become increasingly relevant but should be built on sound process and governance foundations rather than treated as a substitute for them.

* **Human interpretability and consistency.** When AI tools classify something using the noslegal taxonomy, the output is a classification humans can read, query and correct. Without a shared taxonomy including definitions, AI classification outputs tend to take the form of scores, similarity rankings or opaque embeddings that most lawyers and data stewards cannot usefully interrogate. This matters both for data quality and for maintaining meaningful human oversight This interpretability benefit is independent of the network effects that come from wider adoption: it accrues to any organisation that uses a well-designed taxonomy as the basis for its AI classification work.

### **Caveat on software design**

The benefits just described will not arrive automatically from having a well-classified corpus. The taxonomy has to be deliberately incorporated into system design: used as a filter in retrieval pipelines, referenced in the prompts that instruct the model and applied as a framework for evaluating and correcting AI outputs. Treat this as an explicit design requirement.

## 5.4	Migrations and mapping

Most organisations implementing noslegal will not be starting from scratch. They will have existing systems containing classification data of some kind, and existing taxonomies or controlled lists that have been in use for years.

### **You do not need to replace your systems**

The systems themselves can remain in place. One of the things noslegal provides is a semantic layer: a common reference point that allows existing systems to be interpreted against each other, even if they were built and configured independently. That said, organisations implementing new software will find that transition the lowest-friction opportunity to embed noslegal, typically easier than retrofitting it later.

### **noslegal as foundation**

The most effective starting point is to adopt noslegal as the foundation and extend it, adding further levels of detail and additional fields to meet specific needs, rather than designing a private taxonomy from scratch and then attempting to map it to noslegal retrospectively. This approach reduces initial effort significantly, makes it easier and less costly to exchange data with other organisations that have also adopted noslegal, and simplifies the incorporation of future updates as the taxonomy evolves.

### **Where full adoption is not possible**

Some organisations will have factors (existing contractual commitments, legacy systems that cannot easily be reconfigured, or internal constraints) that make rapid full adoption impractical. Partial adoption combined with deliberate mapping is a productive alternative. Mapping documents the relationship between your existing concepts and the corresponding noslegal concepts. It is usually an approximation, but even an imperfect mapping consistently applied allows data created under a private taxonomy to be interpreted against noslegal-classified data. As noted in section 3.5, the most important level to map to is the second level of the Work types and Areas of law facets.

If your existing concepts lack explicit definitions, this is an opportunity to adopt the noslegal definitions where possible. If you have existing definitions, consider honestly how well they are applied in practice and whether they offer any material advantage over the noslegal equivalents. If not, the benefits of alignment suggest adopting the noslegal definitions even if internal labels remain different.

### **Retrospective reclassification**

A full retrospective reclassification of large volumes of historical data is rarely a productive use of time. A mapping approach that translates data, even imperfectly, is typically a better choice. Simple find-and-replace approaches can help in some contexts, and language model tools can assist with reclassification where there is sufficient data to make this meaningful, subject to appropriate human supervision. Bear in mind that older matter data becomes progressively less relevant for most reporting and knowledge purposes: the value of reclassification should be assessed accordingly.

### **(e) 	Interoperability as a longer-term benefit**

Adopting a shared taxonomy creates conditions for inter-organisation interoperability. Where clients, law firms and technology providers describe legal work using a common vocabulary, it becomes easier to exchange information and integrate workflows across organisational boundaries. The benefits are likely to compound over time, and an organisation that invests in alignment now, even partially, will be better positioned to realise them.

## 5.5 Understanding the status quo

Before taking significant decisions, it is important to understand how data currently works across your organisation: how it flows (or should flow) across the four areas of need, what software applications and databases support those areas, and how they can feasibly be joined up. In a large organisation, relevant data is unlikely to be owned or managed by a single team, making a clear picture of the current state essential.

The following questions provide a framework for that diagnostic exercise. The answers will shape both the approach taken and the order in which things are tackled.

* Who are the stakeholders involved, and who owns the various sets of data? Coordinating between them at a suitable level is important so that higher-level concepts are shared, or at least effectively mapped, in ways that are usefully implemented in software.

* How mature and effective are existing taxonomies, processes and software flows for classifying relevant data?

* Which software applications and databases process and store relevant data in each area? Are there upgrade or replacement plans that may provide an opportunity to address data quality issues?

* To what extent is there integration between different data sources? Are there existing attempts to combine data in tools such as Tableau or Power BI, and what lessons can be learned from those efforts?

* What demand or openness exists in each area to do better? For example, is there appetite for better reporting internally or from outside providers?

* Is there evidence of commitment to better data, such as existing manual efforts to clean data?

* What is the quantified business case for improvement, including the benefits of a coordinated approach across different areas? This case is often substantial in terms of both data usefulness and the time and cost of maintenance, and it is worth building concretely, including by identifying problems that outside specialists such as lawyers and senior managers are already experiencing even if they have not connected them to data quality.

## 5.6 Three barriers and how to approach them

There tend to be three main barriers to implementation. Each is real but manageable with the right approach.

### **(a) 	People and organisational realities**

This is usually the hardest barrier and deserves the most attention.

**Building a business case.** Successful change projects in this area need enthusiastic top management support: to make the necessary resources available, to communicate the importance of the work, and to address resistance. The business case is strongest when it connects to problems your organisation has already encountered (time wasted searching for information, pricing decisions made without relevant data, missed opportunities to demonstrate credentials) and expresses these in financial terms with concrete examples.

**Framing the initiative effectively.** Anchoring the taxonomy initiative to goals that already have visible support tends to attract broader backing. Knowledge reuse, financial performance and AI readiness are three areas where the connection is direct and easy to articulate. Framing the initiative in these terms, rather than as a data or classification project in its own right, resonates more widely than leading with the technical case.

**Winning hearts and minds across the organisation.** Helping individuals understand how better data will benefit them personally is often harder than making the case at senior level, but matters just as much. This means holding workshops, circulating clear messaging, and ensuring senior leaders are visibly on board. Having a short, repeatable summary that members of the implementation team can deploy whenever the opportunity arises is practically valuable. Involving enthusiastic stakeholders directly in conversations with senior management tends to be more persuasive than a single specialist function making the case alone.

**Converting sceptics.** Do not underestimate the value of bringing doubters close to early successes. Someone who was initially resistant and came to see the benefits, particularly if respected within the organisation, can be a more compelling advocate than someone who was supportive from the start. In legal organisations, where people engage seriously with abstract concepts, resistance sometimes reflects a deep commitment to an existing way of conceptualising things, or unstated concerns that a taxonomy change signals some unwanted organisational shift. Senior management commitment provides the authority to work through this constructively. Use concrete data to address demands that would increase the risk of bad data through conceptual redundancy or unnecessary complexity.

**Starting in a focused way.** It is rarely necessary or advisable to attempt a full implementation at once. After a reasonable period (say, a year), review classification data and seek permission to remove concepts that are barely used, whether measured in financial terms (for matter classification) or knowledge terms (number of documents classified). Demonstrating the problem objectively in this way tends to be more persuasive than arguing about it in the abstract at the outset. This process can usefully be repeated on a regular cadence, for example every year or two.

### **(b) 	Technology barriers**

Most organisations are not starting from scratch on technology, and constraints arising from existing systems can be real. noslegal has been designed with this in mind: its modest size, clear faceting, limited levels and modularity are intended to make it implementable across a wide range of software environments without requiring specialist infrastructure.

Practical constraints (limitations on field numbers, character limits, restrictions on hierarchy levels) will still arise. Address these by making realistic decisions about how much can be accurately captured within the tools available. Process, communication and training can often compensate for software limitations more than people expect. There is practical experience of navigating these constraints within the noslegal community.

### **(c) 	Resource barriers**

Understanding how to get to grips with your data, and then actually doing it, takes imagination, focus and sustained effort. Smaller organisations are unlikely to have a specialist taxonomist or data officer and will typically need to identify someone who can take on this responsibility alongside other work, or bring in external help. Larger organisations face a different version: additional organisational complexity, entrenched silos and difficulty coordinating across functions that have historically operated independently.

In either case, meaningful investment is required, whether by redirecting existing people, creating a new role or engaging a consultant with relevant experience. The skills most relevant to this work combine legal domain knowledge, an understanding of data structures and the organisational credibility to bring different functions along. These are not always found in the same person, which is worth bearing in mind when assembling a team.

## 5.7 Getting started and maintaining momentum

Waiting for perfect conditions (the ideal software, full stakeholder buy-in, a clean data set, no competing initiatives) means not getting started at all. Some practical guidance on moving forward and sustaining progress:

**Test and iterate.** When rolling out a new taxonomy, pay close attention to the ways it can go wrong: in the concepts themselves, in training, in process or in software. Test data quality regularly, find out how people are feeling about it, and identify weaknesses so they can be addressed. Better process can improve data quality even where the available software is not ideal.

**Investigate informally first.** Exploring relevant topics across different functions informally before committing to major decisions builds a strong foundation and surfaces inconsistencies that are often accidental, resulting from a simple absence of communication rather than any deep disagreement. This may take many months but is time well spent.

**Manage expectations carefully.** Be realistic about what is achievable in the short term. Deliver some fairly quick wins while being clear about what will not be possible immediately and how genuine needs will be addressed in future. People are more willing to invest in a process they see delivering incremental benefits, provided it has a clear plan and direction.

## 5.8 Further support and community

Implementing a taxonomy successfully is not something most organisations need to do entirely on their own. The noslegal community includes lawyers, knowledge and data professionals, technologists and legal business specialists from a range of organisations, many of whom have direct experience of the challenges described in this chapter and are open to sharing it. 

If you are working through implementation questions (whether about taxonomy design, software constraints, change management or mapping from an existing system) engaging with the community is likely to be worthwhile. Community members can be reached via the noslegal website and LinkedIn presence.

# 6\. Applying the taxonomy across the four areas of need

This chapter addresses what good taxonomy implementation looks like across the four areas of need introduced in chapter 2\. The value compounds when the same concepts are used consistently across all four, and the guidance below should be read with that in mind.

## 6.1 Delivery

Delivery covers the scoping, planning, pricing, execution and management of legal work. Accurate matter classification is the foundation on which the other three areas depend: it is what makes knowledge retrievable, credentials credible and experience data meaningful.

The guidance below sets out recommended practice for applying each relevant facet to matter classification. For legal technology companies, it describes the classification model that products supporting delivery should be designed around.

### **Work type**

The implementation points in section 4.1 apply in full. The key delivery-specific point is the treatment of matters with mixed work types. Where a matter develops a substantial element of a materially different second level work type (for example, where a corporate transaction gives rise to significant litigation), a new sub-matter or linked matter should be opened for that work. Mixing materially different work types in a single matter undermines financial reporting, interferes with like-for-like comparison and muddies the classification context available for knowledge management and AI. Compliance will not be perfect, and a sensible materiality threshold should be defined, but a practically useful level of compliance can be achieved with clear guidance and periodic review.

### **Areas of law**

The implementation points in section 4.2 apply in full. Unlike work type, a "one and only one" requirement at the second level may be artificial: multiple areas of law often apply to a single matter in complex and entangled ways that cannot readily be separated into sub-matters. One practical approach is to require a single primary area of law while allowing additional areas to be tagged at any level. Third-level topics are best treated as optional, used for knowledge and experience purposes without the rigour required at the second level.

### **Roles**

The key role to capture in all matters is the one connected with the relevant work type (for example, defendant in litigation, buyer in a transaction, borrower in a financing). A one-and-only-one rule should apply to each matter or sub-matter for this primary role.

It is also worth capturing a role connected with the area of law (for example, employer for employment law matters). This adds a useful dimension for financial analysis, experience profiling and knowledge retrieval.

In implementation, the availability of roles in the software should be linked to the work type or area of law already selected, showing only roles relevant to dispute resolution when the work type is dispute resolution, for example. This reduces the risk of irrelevant roles being selected.

### **Sectors**

The implementation points in section 4.4 apply in full. The key delivery-specific point is the distinction between client sector and matter sector. If a pharmaceuticals company acquires an office building, the matter is more usefully classified in the real estate sector than the pharmaceuticals sector, because the relevant experience and knowledge concerns real estate rather than the client's industry. The client's sector is a separate data point, captured on the client record.

### **Information types**

Information types, uses, status and audience are intended to be used together to classify usefully the things found in legal service provider or legal department messages, document repositories and other records. 

The grid in the taxonomy spreadsheet illustrates how type and use may be combined to provide a rich classification.

We suggest that implementation should enforce

* A single information type for a particular document or other artifact  
* One or more information uses  
* A single status  
* One or more audiences

### **Places**

The implementation points in section 4.5 apply in full, including the guidance on distinguishing governing law, dispute resolution forum and asset or event location. Where the work is being done and where the client is based are typically captured elsewhere in the matter management or financial system and do not need to be duplicated here. A one-or-more approach will often be appropriate given the cross-border complexities that can arise.

### **Process elements**

Process elements are different from the above facets in that they contain process maps rather than concepts for classifying matters. They are most valuable when applied as part of a systematic approach to process improvement, project management and pricing. Even without such a systematic approach, applying process elements to time narrative data can help identify financial and other impacts requiring attention.

## 6.2	Knowledge

Knowledge, as defined by ISO 30401, is a human or organisational asset enabling effective decisions and action in context. In legal work, that context is precisely what the noslegal facets describe: the type of work being done, the area of law involved, the role of the client, the sector and the place. Classifying knowledge against those facets is therefore not a filing exercise. It is what makes knowledge findable at the moment it is actually needed.

The shape of a knowledge base differs between legal services providers and in-house teams. A law firm's knowledge typically organises around practice areas and work types. An in-house team's knowledge tends to cluster around the recurring legal issues of the business it supports, the policies and standards it maintains and the relationships it manages with external providers. The guidance below applies to both, with differences noted where they are significant.

### **Types of legal knowledge and how they arise**

Not all legal knowledge should be treated the same way. Different types arise in different ways and benefit from different approaches to capture, classification and governance.

Much legal knowledge is created in the course of handling matters: advice given, drafts and mark-ups, emails explaining legal reasoning, supporting materials. The most important requirement for this material is that it remains associated with the matter in which it arose. If the matter has been classified using the noslegal facets, the associated work product automatically inherits that context. In practice this means storing documents within the relevant matter workspace, ensuring the matter itself is classified accurately, and avoiding attempts to classify every individual document separately.

Some materials generated during a matter capture particularly important steps or decisions. These can be thought of as key matter records: the curated spine of a matter worth preserving and making findable beyond the immediate context in which it was created.

Over time, some materials prove useful beyond the matter in which they originated and become knowledge assets (precedent clauses, example advice, guidance notes and similar). Knowledge assets may also be created deliberately outside any particular matter: training materials, policy documents, articles and other publications are typical examples.

### **Classifying knowledge assets**

For knowledge assets, deliberate classification becomes more valuable than inherited matter context. Assets can typically be tagged using selected noslegal facets (work type, area of law, place and sector being the most commonly useful) along with any organisation-specific fields such as practice group or business unit. A small number of consistently applied fields is almost always more valuable than a larger number applied inconsistently.

### **High-value knowledge assets**

A small subset of knowledge assets may become particularly important to how an organisation performs legal work: key playbooks, canonical templates, structured guidance on recurring issues. Because of their importance, these assets often benefit from stronger governance, including clear ownership, alignment with authoritative sources such as law or internal policy, and periodic review to ensure they remain current. In an in-house team, this category often includes standard contract templates, approval frameworks and legal policies that the whole organisation relies on, making governance especially important since the consequences of outdated material can be significant.

### **The lifecycle of knowledge**

Legal knowledge often develops through stages: everyday work product created during a matter; important materials recognised as key matter records; selected materials curated as knowledge assets; and a small subset maintained as high-value knowledge assets with stronger governance. Taxonomy plays a different role at each stage. Early stages rely mainly on matter classification, with knowledge inheriting its context from the matter. Later stages benefit from deliberate tagging and active governance. Understanding this lifecycle helps organisations focus classification effort where it adds most value rather than attempting to classify everything equally.

### **Expertise and experience**

The noslegal taxonomy can also be used to describe the experience of individuals within an organisation. When matters are classified consistently, the experience of the lawyers who handled them can be aggregated and analysed. Individuals may be associated with the work types they handle, the areas of law in which they have experience, the sectors in which they work, the jurisdictions in which they operate and the roles they typically perform. Using the same taxonomy across matters, knowledge and people makes it easier to identify relevant experience when new matters arise. This topic is developed further in section 6.4.

### **Knowledge classification and AI**

Effective classification using noslegal has a particularly direct payoff in AI-assisted knowledge retrieval. Where a language model draws on a corpus to answer questions or surface relevant materials, this will perform better if knowledge assets are consistently tagged by work type, area of law and so on. Those classifications can be used to filter the corpus before the model processes it. Without this pre-filtering, the model is working across a larger, noisier set of materials, with implications for performance. An investment in consistent classification is therefore an investment in effective use of AI.

## 6.3 Pipeline

Pipeline covers the activities by which legal organisations understand, anticipate and influence what work is upcoming or available. For legal services providers this includes marketing, business development, credentials and client relationship management. For in-house teams it includes forward planning, resourcing and managing the flow of work from the business.

### **Reliance on delivery data**

The most valuable pipeline data is largely the same data generated for delivery. A well-classified matter record (capturing work type, area of law, sector, place and role) is also the foundation for credentials, experience profiles and portfolio analysis. An organisation that classifies its matters accurately for delivery purposes gets most of the pipeline benefit without any additional classification effort. The primary pipeline requirement is therefore not a separate classification exercise but a commitment to delivery classification quality, combined with the ability to surface and aggregate that data in the formats pipeline activities require (pitch documents, capability statements, client reporting, demand analysis and so on).

### **Separate pipeline data sources**

Where separate pipeline data exists (in CRM software, a credentials database or a business development platform) the key requirement is that it is synchronised with the matter and financial data generated in delivery. A credentials record that describes a matter differently from the way it is classified in the matter management system undermines the credibility of the credential and makes portfolio analysis unreliable. Synchronisation does not necessarily mean identical fields, but it does mean that the core taxonomy classifications applied to a matter in delivery are reflected consistently wherever that matter appears in pipeline systems.

Some pipeline activities generate data with no direct equivalent in delivery (information about prospective clients, pitch outcomes, or the status of business development relationships). Where pipeline records are linked to matters (for example, where a pitch record is linked to the matter that resulted from it) applying consistent taxonomy classifications to both makes it possible to analyse conversion rates, pitch success and demand patterns by work type, sector or geography.

## 6.4 People

The people area covers understanding and communicating what experience and skills an organisation's legal professionals have, identifying gaps, and making good decisions about work allocation, recruitment, training, secondments and career development. For legal services providers it includes the credentials and experience profiling that supports business development. For in-house teams it includes managing the balance between work done internally and work sent to external providers.

As with pipeline, the most valuable source of people-relevant data is that generated in delivery. A lawyer's experience is primarily demonstrated by the matters they have worked on. If those matters are classified consistently and accurately (by work type, area of law, sector, place and role) a meaningful and up-to-date picture of each individual's experience accumulates automatically as a by-product of ordinary matter management. This is both more reliable and more granular than experience data that depends on individuals self-reporting their expertise, updating their profile or completing periodic HR exercises that are easy to neglect.

Separate HR or marketing databases serve important purposes (recording formal qualifications, training history, performance data and curated narrative profiles used in pitches and on websites). But these sources tend to become outdated, to reflect how individuals wish to be seen rather than what they have actually done, and to be maintained inconsistently. Matter-derived experience data provides a more objective and continuously updated foundation that separate systems can draw on and supplement rather than substitute for.

### **Applying the taxonomy to people data**

The noslegal facets most relevant to experience profiling are work type, area of law, sector, place and role. Process elements data can also be relevant in some cases (for example, to identify that someone has a particular focus on ediscovery rather than other aspects of litigation). When matters are classified consistently against these facets and individuals are associated with the matters they have worked on (whether as supervising partner, lead associate or in another defined capacity) it becomes possible to aggregate and analyse experience across the organisation in a structured way.

Useful questions that well-classified matter data can answer include: which lawyers have handled matters of a given work type and area of law in a particular sector or jurisdiction; who has experience of a particular role (acting for defendants in arbitration, or advising borrowers in leveraged finance transactions, for example); how broadly or narrowly experience is distributed across the team; and where gaps exist relative to the work the organisation is doing or anticipates doing. This data has practical value across several contexts: identifying the right person for a new matter, supporting supervision and development conversations, informing recruitment decisions and demonstrating credentials in pitches and capability reviews.

### **Synchronisation with other systems**

Where HR systems, learning management platforms or marketing profile databases exist alongside matter management systems, the same synchronisation principle applies as in pipeline. The core taxonomy classifications from delivery should be reflected consistently wherever individual experience is described. A lawyer's profile on the firm's website or in a pitch document should be grounded in, and consistent with, their matter history as classified in the matter management system, rather than maintained as a separate and potentially divergent record. Achieving this in practice often requires deliberate integration work or periodic reconciliation processes, but the direction of travel should be clear: matter-derived data is the authoritative source for what people have actually done, and other systems should draw on it rather than operate independently of it.

### **Skills and development**

Experience data derived from matter classification tells you what people have done. It does not by itself tell you what they are capable of doing, how well they have done it, or what they need to do next to develop. These questions require additional data (formal skills assessments, supervision feedback, training records, development plans) that sits largely outside the scope of noslegal as currently constituted.

[^1]:  We published the first edition of this guide in March 2025 with v3 of the taxonomy and made some minor updates in July 2025\. This significantly expanded second edition is being published together with v4 of the taxonomy in May 2026\.

[^2]:  We published a first version of our taxonomy in early 2022, a second major version in 2023, with minor updates to the Places facet in 2024\. A third major version followed in 2025 and a fourth in 2026\. We established a company limited by guarantee early on to hold relevant IP and license it out on an open source basis. We have minimal operating expenses which are covered by modest sponsorship sums refreshed periodically \- current sponsor names are published on our website, [https://www.noslegal.org](https://www.noslegal.org) 

[^3]:  Specifically, the taxonomy is released under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) [permissive](https://en.wikipedia.org/wiki/Permissive_software_license) open source licence.

[^4]:  v3 of noslegal released in 2025 had eight facets. We have decided to remove Connectors (i.e. relationship between classified things and noslegal concepts) as a facet and to address the topic by way of implementation guidance instead (see section 4.5).

[^5]:  Renamed from “Laws” in v3.

[^6]:  Renamed from Information assets in v3. XP5.1 (knowledge assets) has been replaced by a new XP5.1 (information uses) with improved guidance on how to use these together including an illustrative grid in the taxonomy spreadsheet.