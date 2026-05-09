# Performance evaluation with and without reranking

Reviews the following:
* retrieval_precision
* context_focus
* answer_quality

This allows to:
* Isolate the effect of reranking while keeping the query and filters the same.
* Make it easier to see whether reranking is actually improving the top chunks, not just changing the source mix.

To make the comparison more clear, also the top 6 candidate pools before reranking are displayed.

Note: With use_rerank=False, the pipeline takes the top k similarity results from Pinecone and then keeps the first top_n chunks in that order. The label 'Used after rerank', in this context refers to the number of chunks kept at the end.

**Conclusion:**
* No rerank can stay podcast-heavy: the podcast chunks happened to rank higher in the raw vector similarity step, so the final context stayed podcast-heavy.
* Rerank can promote a mix of podcast + EU AI Act chunks (how the LLM reorders the pool): after the model the top 3 chunks are indeed a mixed of podcast and the EU AI Act chunk which produces a better response. 

**Manual rerank comparison:** - output from the last cell

No Reranking
{'retrieval_precision': 3, 'context_focus': 3, 'answer_quality': 3}
Retrieves relevant material, but the top chunks can be a bit mixed across sources.

With Reranking
{'retrieval_precision': 4, 'context_focus': 4, 'answer_quality': 4}
Reranking pushes the most on-topic chunks to the top, making the answer tighter.


------
Candidate pool before reranking:
[1] source_type=podcast_transcript; section=full_transcript; chunk_id=None; chunking_strategy=None
So imagine for a second you're driving across, I don't know, a massive suspension bridge. Okay. You don't pull over halfway across, get out, and demand to see the blueprints, right? You don't interview the welding crew. ...
[2] source_type=podcast_transcript; section=full_transcript; chunk_id=None; chunking_strategy=None
. If you think you're confiding in a sympathetic human, but it's actually a bot program to extract data or sell you something. That's a huge violation of trust. It is. We shouldn't be building emotional attachments to so...
[3] source_type=podcast_transcript; section=full_transcript; chunk_id=podcast_transcript_00004; chunking_strategy=paragraph_first_900_120
. It says rating humans on their behavior to deny them services or rights endangers human autonomy. It's fundamentally anti-democratic. Another major red flag is law WS lethal autonomous weapon systems. Killer robots, ef...
[4] source_type=eu_ai_act; section=page_8; chunk_id=eu_ai_act_00036; chunking_strategy=token_smaller_350_50
(27) While the r isk -based approac h is the basis f or a propor tionate and effe ctive set of binding r ules, it is imp or tant to recall the 2019 Ethics guidelines f or tr ustwo r th y AI developed by the independent A...
[5] source_type=eu_ai_act; section=page_8; chunk_id=eu_ai_act_00037; chunking_strategy=token_smaller_350_50
. T ec hnical robustness and saf ety means that AI syste ms are developed and used in a wa y that allows robustness in the case of problems and resilience ag ainst atte mp ts to alter the use or perform ance of the AI sy...
[6] source_type=podcast_transcript; section=full_transcript; chunk_id=podcast_transcript_00000; chunking_strategy=paragraph_first_900_120
So imagine for a second you're driving across, I don't know, a massive suspension bridge. Okay. You don't pull over halfway across, get out, and demand to see the blueprints, right? You don't interview the welding crew. ...

No Reranking
Filter: None
Retrieved candidates: 6
Used after rerank: 3

Chosen chunk 1
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
So imagine for a second you're driving across, I don't know, a massive suspension bridge. Okay. You don't pull over halfway across, get out, and demand to see the blueprints, right? You don't interview the welding crew. No. You just, you trust it. You just drive. You trust the bridge. You trust the engineering standards, the inspections, the laws t...

Chosen chunk 2
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
. If you think you're confiding in a sympathetic human, but it's actually a bot program to extract data or sell you something. That's a huge violation of trust. It is. We shouldn't be building emotional attachments to software. So bringing this all together, we started with a bridge. We trust the bridge because of physics and laws. Can we ever get ...

Chosen chunk 3
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': 'podcast_transcript_00004', 'chunking_strategy': 'paragraph_first_900_120'}
. It says rating humans on their behavior to deny them services or rights endangers human autonomy. It's fundamentally anti-democratic. Another major red flag is law WS lethal autonomous weapon systems. Killer robots, effectively. The source cites the European Parliament calling for a ban on weapons that select and engage targets without a human sa...

Answer:
Trustworthy AI requires transparency, accountability, and a socio-technical approach that includes the code, the humans involved, the laws, and the environment. It emphasizes the need for understanding the decision-making processes of AI systems and ensuring that the people behind the technology have demonstrated integrity and competence. Key questions to consider include whether the system is transparent, if there is a human in the loop, and understanding the rationale behind its decisions (chunks [1], [2]).

With Reranking
Filter: None
Retrieved candidates: 6
Used after rerank: 3

Chosen chunk 1
{'source_type': 'podcast_transcript', 'section': 'full_transcript', 'chunk_id': None, 'chunking_strategy': None}
{'rerank_score': 95, 'rerank_reason': 'Directly discusses the requirements for trustworthy AI, emphasizing the socio-technical system and the need for transparency.'}
. If you think you're confiding in a sympathetic human, but it's actually a bot program to extract data or sell you something. That's a huge violation of trust. It is. We shouldn't be building emotional attachments to software. So bringing this all together, we started with a bridge. We trust the bridge because of physics and laws. Can we ever get ...

Chosen chunk 2
{'source_type': 'eu_ai_act', 'section': 'page_8', 'chunk_id': 'eu_ai_act_00036', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 90, 'rerank_reason': 'Cites ethical principles for trustworthy AI, providing a structured approach to ensuring AI is ethically sound.'}
(27) While the r isk -based approac h is the basis f or a propor tionate and effe ctive set of binding r ules, it is imp or tant to recall the 2019 Ethics guidelines f or tr ustwo r th y AI developed by the independent AI HLEG appoint ed by the Commission. In those guidelines, the AI HLEG developed seven non-binding ethical pr inciples f or AI whic...

Chosen chunk 3
{'source_type': 'eu_ai_act', 'section': 'page_8', 'chunk_id': 'eu_ai_act_00037', 'chunking_strategy': 'token_smaller_350_50'}
{'rerank_score': 85, 'rerank_reason': 'Details specific principles related to technical robustness, safety, and transparency, which are essential for trustworthy AI.'}
. T ec hnical robustness and saf ety means that AI syste ms are developed and used in a wa y that allows robustness in the case of problems and resilience ag ainst atte mp ts to alter the use or perform ance of the AI syste m so as to allow unla wful use by third par ties, and minimise uninte nded har m. Pr ivacy and data gove r nance means that AI...

Answer:
Trustworthy AI requires several key principles, as outlined in the context. These include:

1. **Human agency and oversight**: AI systems should serve people and respect human dignity, allowing for appropriate human control and oversight (chunk 2).
2. **Technical robustness and safety**: AI systems must be developed to ensure robustness and resilience against misuse, minimizing unintended harm (chunk 3).
3. **Privacy and data governance**: AI systems should comply with privacy and data protection rules, ensuring high standards of data quality and integrity (chunk 3).
4. **Transparency**: AI systems need to be traceable and explainable, making users aware that they are interacting with AI and informing them about the system's capabilities and limitations (chunk 3).
5. **Diversity, non-discrimination, and fairness**: AI should promote equal access and avoid discriminatory impacts (chunk 3).
6. **Societal and environmental well-being**: AI systems should be developed sustainably and in a way that benefits all humans (chunk 3).
7. **Accountability**: There should be mechanisms in place to hold developers and deployers accountable for the AI systems they create (chunk 2).

These principles contribute to the design of coherent, trustworthy, and human-centric AI.

Manual rerank comparison:

No Reranking
{'retrieval_precision': 3, 'context_focus': 3, 'answer_quality': 3}
Retrieves relevant material, but the top chunks can be a bit mixed across sources.

With Reranking
{'retrieval_precision': 4, 'context_focus': 4, 'answer_quality': 4}
Reranking pushes the most on-topic chunks to the top, making the answer tighter.
