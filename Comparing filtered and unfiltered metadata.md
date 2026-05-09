# Comparing filtered and unfiltered


* The unfiltered run searches across both sources, so Pinecone can return chunks from the podcast and the EU AI Act if both are semantically relevant to the question.
* The filtered runs for both cases separatedly: {"source_type": {"$eq": "podcast_transcript"}}, so it is limited to the podcast only and {"source_type": {"$eq": "eu_ai_act"}} so taht it's limited to the pdf only.
* Unfiltered RAG shows what the system retrieves when it can search the full corpus.
* Filtered RAG shows how metadata constraints narrow the search space.

**Why this is a good comparison:**

* It isolates the effect of metadata filtering.
* It helps check whether filtering improves precision or removes useful evidence.
* It mirrors a real RAG decision: sometimes one wants all sources, and sometimes one wants to restrict retrieval to one document type.

-----
Baseline RAG
Filter: None
Retrieved candidates: 6
Used after rerank: 3

Chosen chunk 1
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
{'rerank_score': 95, 'rerank_reason': 'Directly discusses the requirements for trustworthy AI, emphasizing the socio-technical system and the need for transparency.'}
. If you think you're confiding in a sympathetic human, but it's actually a bot program to extract data or sell you something. That's a huge violation of trust. It is. We shouldn't be building emotional attachments to software. So bringing this all together, we started with a bridge. We trust the bridge because of physics and laws. Can we ever get ...

Chosen chunk 2
{'source_type': 'eu_ai_act', 'section': 'page_8', 'chunk_id': 'eu_ai_act_00036', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 90, 'rerank_reason': 'Cites the 2019 Ethics guidelines for trustworthy AI, outlining key principles that contribute to ethical AI development.'}
(27) While the r isk -based approac h is the basis f or a propor tionate and effe ctive set of binding r ules, it is imp or tant to recall the 2019 Ethics guidelines f or tr ustwo r th y AI developed by the independent AI HLEG appoint ed by the Commission. In those guidelines, the AI HLEG developed seven non-binding ethical pr inciples f or AI whic...

Chosen chunk 3
{'source_type': 'eu_ai_act', 'section': 'page_8', 'chunk_id': 'eu_ai_act_00037', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 85, 'rerank_reason': 'Details specific principles related to technical robustness, safety, and transparency, which are essential for trustworthy AI.'}
. T ec hnical robustness and saf ety means that AI syste ms are developed and used in a wa y that allows robustness in the case of problems and resilience ag ainst atte mp ts to alter the use or perform ance of the AI syste m so as to allow unla wful use by third par ties, and minimise uninte nded har m. Pr ivacy and data gove r nance means that AI...

Answer:
Trustworthy AI requires several key principles, as outlined in the 2019 Ethics guidelines for trustworthy AI developed by the independent AI HLEG. These principles include:

1. **Human agency and oversight**: AI systems should serve people, respect human dignity, and be controllable by humans.
2. **Technical robustness and safety**: AI systems must be resilient to problems and attempts at unlawful use, minimizing unintended harm.
3. **Privacy and data governance**: AI systems should comply with privacy and data protection rules, ensuring high standards of data quality and integrity.
4. **Transparency**: AI systems must allow for traceability and explainability, ensuring users are aware they are interacting with AI and understand its capabilities and limitations.
5. **Diversity, non-discrimination, and fairness**: AI systems should promote equal access and avoid discriminatory impacts.
6. **Societal and environmental well-being**: AI systems should be developed sustainably and benefit all human beings.
7. **Accountability**: There should be mechanisms in place to hold developers and deployers accountable for the AI systems they create and use.

These principles contribute to the design of coherent, trustworthy, and human-centric AI (chunks 2 and 3). Additionally, the context emphasizes the importance of transparency and the integrity of the people behind AI systems (chunk 1).

Podcast-only RAG
Filter: {'source_type': {'$eq': 'podcast_transcript'}}
Retrieved candidates: 6
Used after rerank: 3

Chosen chunk 1
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
{'rerank_score': 95, 'rerank_reason': 'Directly discusses the components of trustworthy AI and the need for a socio-technical approach.'}
. If you think you're confiding in a sympathetic human, but it's actually a bot program to extract data or sell you something. That's a huge violation of trust. It is. We shouldn't be building emotional attachments to software. So bringing this all together, we started with a bridge. We trust the bridge because of physics and laws. Can we ever get ...

Chosen chunk 2
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
{'rerank_score': 90, 'rerank_reason': 'Defines trustworthy AI and outlines its three essential components, emphasizing compliance and lifecycle.'}
. And a checklist that every developer should probably have tattooed on their arm. Okay, let's start with the big picture. The source material defines trustworthy AI as having three components. Right. And they have to exist through the entire lifecycle of the system. Not just at launch. Not just at launch. From design to retirement. Think of it lik...

Chosen chunk 3
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
{'rerank_score': 85, 'rerank_reason': 'Explores the concept of trust in AI through relatable analogies, raising critical questions about trustworthiness.'}
So imagine for a second you're driving across, I don't know, a massive suspension bridge. Okay. You don't pull over halfway across, get out, and demand to see the blueprints, right? You don't interview the welding crew. No. You just, you trust it. You just drive. You trust the bridge. You trust the engineering standards, the inspections, the laws t...

Answer:
Trustworthy AI requires three key components that must exist throughout the entire lifecycle of the system: lawful, ethical, and robust. 

1. **Lawful**: The AI must comply with all regulations.
2. **Ethical**: It should adhere to ethical principles, even when laws have not yet caught up.
3. **Robust**: The AI must be technically and socially robust to prevent harm.

These components ensure that AI systems are not only legal but also morally sound and reliable (Context: [2]). Additionally, trust in AI is fundamentally about the integrity of the people behind it, as true trust cannot be established if the AI operates as a black box (Context: [1]). 

For a deeper understanding, consider the importance of transparency and accountability in AI interactions (Context: [1]).

EU AI Act RAG
Filter: {'source_type': {'$eq': 'eu_ai_act'}}
Retrieved candidates: 6
Used after rerank: 3

Chosen chunk 1
{'source_type': 'eu_ai_act', 'section': 'page_8', 'chunk_id': 'eu_ai_act_00036', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 95, 'rerank_reason': 'Directly discusses the ethical principles required for trustworthy AI, including human agency, technical robustness, and transparency.'}
(27) While the r isk -based approac h is the basis f or a propor tionate and effe ctive set of binding r ules, it is imp or tant to recall the 2019 Ethics guidelines f or tr ustwo r th y AI developed by the independent AI HLEG appoint ed by the Commission. In those guidelines, the AI HLEG developed seven non-binding ethical pr inciples f or AI whic...

Chosen chunk 2
{'source_type': 'eu_ai_act', 'section': 'page_8', 'chunk_id': 'eu_ai_act_00037', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 90, 'rerank_reason': 'Expands on the principles of technical robustness and safety, privacy, and transparency, which are essential for trustworthy AI.'}
. T ec hnical robustness and saf ety means that AI syste ms are developed and used in a wa y that allows robustness in the case of problems and resilience ag ainst atte mp ts to alter the use or perform ance of the AI syste m so as to allow unla wful use by third par ties, and minimise uninte nded har m. Pr ivacy and data gove r nance means that AI...

Chosen chunk 3
{'source_type': 'eu_ai_act', 'section': 'page_22', 'chunk_id': 'eu_ai_act_00110', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 85, 'rerank_reason': 'Focuses on technical robustness as a key requirement for high-risk AI systems, detailing measures to ensure resilience and safety.'}
(75) T ec hnical robustness is a ke y requirement f or high-r isk AI systems. They should be resilient in relation to har mful or other wise undesirable behavi our that ma y result from limitations within the syste ms or the envir onment in which the systems operate (e.g. er rors, faults, inconsiste ncies, unexpected situations). Theref ore, tec hn...

Answer:
Trustworthy AI requires adherence to seven non-binding ethical principles developed by the AI HLEG, which include:

1. **Human agency and oversight**: AI systems should serve people, respect human dignity, and be controllable by humans.
2. **Technical robustness and safety**: AI systems must be resilient to problems and attempts at unlawful use, minimizing unintended harm.
3. **Privacy and data governance**: AI systems should comply with privacy and data protection rules, ensuring high standards of data quality and integrity.
4. **Transparency**: AI systems must allow for traceability and explainability, informing users about their interaction with AI and the system's capabilities and limitations.
5. **Diversity, non-discrimination, and fairness**: AI systems should promote equal access and avoid discriminatory impacts.
6. **Societal and environmental well-being**: AI systems should be developed sustainably and benefit all human beings.
7. **Accountability**: There should be mechanisms in place to ensure accountability in the use of AI systems.

These principles contribute to the design of coherent, trustworthy, and human-centric AI (chunks 1 and 2).
