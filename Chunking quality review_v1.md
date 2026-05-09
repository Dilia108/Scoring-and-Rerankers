# Chunking quality review:

**Podcast transcript:** good quality overall.
* The chunks keep conversational context well.
paragraph_first_900_120 is better here because the transcript is narrative and benefits from larger context windows.
* A few chunks begin mid-thought, which is normal with recursive splitting, but the overlap helps recover context.

**EU AI Act PDF:** mixed quality.
* The chunks are structurally okay, but the extracted text has clear OCR artifacts like REGUL A TION, har monised, and Ar tif icial.
That means the main issue is not only chunking, but also source text quality.
* token_smaller_350_50 is better for more precise legal retrieval, but it may over-fragment the text if one cares about broader legal context.

**Conclusion:** For the EU AI Act, the current smaller chunks are more retrieval-friendly, but the PDF text should ideally be cleaned before final vector indexing.
================================================================================
Preview for podcast_transcript

podcast_transcript | paragraph_first_900_120
Total chunks: 5

Sample chunk 1
{'source_type': 'podcast_transcript', 'source_file': 'The_Blueprint_For_Trustworthy_AI.txt', 'section': 'full_transcript', 'chunk_id': 'podcast_transcript_00000', 'chunk_index': 0, 'chunking_strategy': 'paragraph_first_900_120', 'chunk_char_count': 4106}
So imagine for a second you're driving across, I don't know, a massive suspension bridge. Okay. You don't pull over halfway across, get out, and demand to see the blueprints, right? You don't interview the welding crew. No. You just, you trust it. You just drive. You trust the bridge. You trust the engineering standards, the inspections, the laws that say this thing won't fail. Right. It's trust in the infrastructure. It's invisible, but it's the...

Sample chunk 2
{'source_type': 'podcast_transcript', 'source_file': 'The_Blueprint_For_Trustworthy_AI.txt', 'section': 'full_transcript', 'chunk_id': 'podcast_transcript_00001', 'chunk_index': 1, 'chunking_strategy': 'paragraph_first_900_120', 'chunk_char_count': 4219}
. Fundamental rights. Yes. The EU Charter, specifically. This is so crucial because it changes the framing. AI isn't an end in itself. It's a tool for human flourishing. I highlighted that phrase in my notes. Human flourishing. It's such a distinct shift from, you know, optimizing efficiency or maximizing engagement. It is. It sounds nice, but it feels hard to measure. It is hard to measure. But to make it concrete, the experts derive four ethica...

podcast_transcript | token_balanced_512_64
Total chunks: 8

Sample chunk 1
{'source_type': 'podcast_transcript', 'source_file': 'The_Blueprint_For_Trustworthy_AI.txt', 'section': 'full_transcript', 'chunk_id': 'podcast_transcript_00000', 'chunk_index': 0, 'chunking_strategy': 'token_balanced_512_64', 'chunk_char_count': 2346}
So imagine for a second you're driving across, I don't know, a massive suspension bridge. Okay. You don't pull over halfway across, get out, and demand to see the blueprints, right? You don't interview the welding crew. No. You just, you trust it. You just drive. You trust the bridge. You trust the engineering standards, the inspections, the laws that say this thing won't fail. Right. It's trust in the infrastructure. It's invisible, but it's the...

Sample chunk 2
{'source_type': 'podcast_transcript', 'source_file': 'The_Blueprint_For_Trustworthy_AI.txt', 'section': 'full_transcript', 'chunk_id': 'podcast_transcript_00001', 'chunk_index': 1, 'chunking_strategy': 'token_balanced_512_64', 'chunk_char_count': 2345}
. And a checklist that every developer should probably have tattooed on their arm. Okay, let's start with the big picture. The source material defines trustworthy AI as having three components. Right. And they have to exist through the entire lifecycle of the system. Not just at launch. Not just at launch. From design to retirement. Think of it like a three-legged stool. The first leg is lawful. The AI has to comply with all the regulations. Whic...

================================================================================
Preview for eu_ai_act

eu_ai_act | token_balanced_512_64
Total chunks: 430

Sample chunk 1
{'source_type': 'eu_ai_act', 'source_file': 'eu_ai_act.pdf', 'section': 'page_1', 'chunk_id': 'eu_ai_act_00000', 'chunk_index': 0, 'chunking_strategy': 'token_balanced_512_64', 'chunk_char_count': 1637}
REGUL A TION (EU) 2024/1689 OF THE EUR OPEAN P ARLIAMENT AND OF THE CO UNCIL of 13 June 2024 laying do wn har monised r ules on ar tif icial intelligence and amending Regulations (EC) No 300/2008, (EU) No 167/2013, (EU) No 168/2013, (EU) 2018/858, (EU) 2018/1139 and (EU) 2019/2144 and Directiv es 2014/90/EU, (EU) 2016/797 and (EU) 2020/1828 (Ar tif icial Intelligence A ct) (T ext with EEA relevance) THE EUR OPEAN P ARLIAMENT AND THE COUNCIL OF TH...

Sample chunk 2
{'source_type': 'eu_ai_act', 'source_file': 'eu_ai_act.pdf', 'section': 'page_1', 'chunk_id': 'eu_ai_act_00001', 'chunk_index': 1, 'chunking_strategy': 'token_balanced_512_64', 'chunk_char_count': 1925}
fundamental r ights as enshr ined in the Char te r of Fundamental Rights of the European Union (the ‘Char te r ’), including democracy , the r ule of law and environmental prot ection, to protect against the har mful effe cts of AI syste ms in the Uni on, and to suppor t inno vation. This Regulation ensures the free moveme nt, cross-border , of AI-based goods and ser vices, thus preventing Member Stat es from imp osing restr ictions on the develo...

eu_ai_act | token_smaller_350_50
Total chunks: 598

Sample chunk 1
{'source_type': 'eu_ai_act', 'source_file': 'eu_ai_act.pdf', 'section': 'page_1', 'chunk_id': 'eu_ai_act_00000', 'chunk_index': 0, 'chunking_strategy': 'token_smaller_350_50', 'chunk_char_count': 1024}
REGUL A TION (EU) 2024/1689 OF THE EUR OPEAN P ARLIAMENT AND OF THE CO UNCIL of 13 June 2024 laying do wn har monised r ules on ar tif icial intelligence and amending Regulations (EC) No 300/2008, (EU) No 167/2013, (EU) No 168/2013, (EU) 2018/858, (EU) 2018/1139 and (EU) 2019/2144 and Directiv es 2014/90/EU, (EU) 2016/797 and (EU) 2020/1828 (Ar tif icial Intelligence A ct) (T ext with EEA relevance) THE EUR OPEAN P ARLIAMENT AND THE COUNCIL OF TH...

Sample chunk 2
{'source_type': 'eu_ai_act', 'source_file': 'eu_ai_act.pdf', 'section': 'page_1', 'chunk_id': 'eu_ai_act_00001', 'chunk_index': 1, 'chunking_strategy': 'token_smaller_350_50', 'chunk_char_count': 1194}
2 ), Having regard to the opinion of the Committee of the Regions ( 3 ), A cting in accordance with the ordinar y legislative procedure ( 4 ), Whereas: (1) The pur pose of this Regulation is to imp rove the functioning of the internal marke t by la ying do wn a unif or m leg al framew ork in par ticular f or the development, the placing on the market, the putting into ser vice and the use of ar tificial inte lligence syste ms (AI systems) in the ...
