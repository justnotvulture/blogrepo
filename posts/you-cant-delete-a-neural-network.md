---
title: You Can’t Delete a Neural Network
author: Matthieu
date: 2026-02
lede: The right to be forgotten assumes data can be deleted. Neural networks don’t work that way.
---
# Part I: The Right to Be Forgotten vs. The Historical Record

## Origins and Legal Architecture

The "right to be forgotten" didn't spring fully formed from GDPR. Its intellectual ancestry is older and more philosophically interesting than the legal instrument that now embodies it.

In French law, there has long been a concept called *le droit à l'oubli* — the right to oblivion — which applied primarily to people who had served criminal sentences and wished to reintegrate into society without their past following them. The moral intuition is straightforward: if punishment is meant to be finite, then the social stigma that follows someone indefinitely after they've served their time undermines the entire rehabilitative premise of the justice system. A person convicted of theft at 22 who has lived blamelessly for 30 years has, in some meaningful sense, become a different person. The records that identify them as a thief are technically accurate but practically misleading about who they currently are.

This intuition — that accurate information can become wrongful information through the passage of time — is philosophically non-trivial. It challenges a naive correspondence theory of truth in which a statement is simply true or false independent of context. The claim "X committed theft in 1990" is permanently true in some abstract sense, but its social meaning changes radically depending on when it's stated, to whom, in what context, and for what purpose.

The European Court of Justice's 2014 *Google Spain* ruling brought this into the digital age in a dramatic way. Mario Costeja González, a Spanish lawyer, had old newspaper articles about a debt auction related to his property appearing prominently in Google search results for his name. The debt had long since been resolved. He argued — and the ECJ agreed — that he had a right to request that Google delist those results, even though the underlying newspaper articles remained accessible. This ruling established that search engines are data controllers under EU law, and that individuals have rights to request delisting of results that are "inadequate, irrelevant or no longer relevant, or excessive."

GDPR, which came into force in 2018, formalized and extended this, incorporating the right to erasure in Article 17. The right applies when personal data is no longer necessary for the purpose it was collected, when consent is withdrawn, when data has been unlawfully processed, or when erasure is required to comply with a legal obligation. Crucially, Article 17(3) contains explicit exceptions: the right to erasure does not apply when processing is necessary for exercising the right of freedom of expression and information, for compliance with a legal obligation, for public health purposes, for archiving purposes in the public interest, scientific or historical research purposes, or statistical purposes, or for the establishment, exercise, or defense of legal claims.

So even within GDPR itself, there's a recognized tension, and the archival exception is explicitly carved out. But the devil, as always, is in the details.

## What Does "Archival Purposes in the Public Interest" Actually Mean?

This exception sounds clear but is operationally murky. Who decides what counts as a public interest archive? How do we distinguish a legitimate historical archive from a private company that wants to retain data indefinitely and claims archival purpose as cover? What counts as "scientific or historical research purposes" — does a journalist writing a retrospective count? A true crime podcaster? An academic historian? A private genealogy company?

The European Data Protection Board has issued guidance, but it's necessarily general. National implementations vary. And the practical reality is that most erasure requests don't involve clear-cut cases like archives of major historical events — they involve messy, ambiguous situations where someone wants information about their personal past removed from contexts they find harmful or embarrassing.

Consider some real tension cases:

**The convicted politician.** A person who held elected office, was convicted of corruption, served their sentence, and has since left public life. They request erasure of news articles about their conviction from search indices. Argument for erasure: they've paid their debt to society, they're no longer a public figure, the information serves no current democratic accountability purpose. Argument against: their actions as a public official are part of the historical record of governance, and voters and citizens have a legitimate interest in that record being accessible. This case is hard precisely because *both* interests are genuine. The person isn't just a private individual — they exercised public power — but they're also not *currently* exercising it.

**The ordinary person and a decade-old social media post.** Someone made offensive remarks on a public forum in 2010, at age 19. They request erasure. Argument for: youthful statements don't reflect current character, and the permanent accessibility of such records creates incentives for people to be paralyzed by fear of their pasts in ways that may suppress authentic discourse. Argument against: public statements are public statements; accepting this erasure at scale means the internet becomes selectively curated to make everyone's public record more flattering.

**The victim who is also a perpetrator.** A person who was both a victim of serious crimes and later committed crimes themselves. They might have legitimate claims to erasure on one dimension that conflict with legitimate interests in preservation on another. Their victimhood is part of someone else's criminal record; their perpetration is part of the record of harm they caused.

**The journalist's source.** A person who appeared in investigative journalism about institutional corruption was named as a witness or minor participant, not the central wrongdoer. They want the articles delisted. The journalism documented real events of public interest, but this person's role was peripheral and their ongoing association with a scandal they barely participated in is harming their life.

None of these cases resolve cleanly. What they reveal is that the right to be forgotten isn't really a coherent single right — it's a cluster of different claims that happen to share the same legal vehicle.

## The Deeper Philosophical Argument: Identity, Time, and Narrative

Behind the legal framework is a genuinely interesting philosophical question: what is the relationship between a person and their past actions?

One view — call it the *static record* view — holds that a person's history is simply part of what they are. You cannot meaningfully separate "who someone is" from "what they have done." On this view, the historical record of a person's actions is constitutive of their identity, and claiming a right to have it altered or suppressed is a kind of claim to edit one's own nature — which is philosophically incoherent and practically dangerous.

A contrasting view — call it the *narrative continuity* view — holds that personal identity is constituted by ongoing narrative rather than fixed historical fact. We understand ourselves and others not as static collections of past events but as evolving characters in ongoing stories. On this view, a person who has genuinely changed has a legitimate claim to having their current narrative foregrounded over their past one, because the past record, while factually accurate, tells a misleading story about who they currently are.

The philosopher Paul Ricoeur's distinction between *idem* identity (sameness, numerical identity over time) and *ipse* identity (selfhood, the kind of identity that involves promise-keeping, narrative coherence, and accountability) is useful here. The right to be forgotten is really a claim about *ipse* identity — it's saying that the self that acted badly in the past is not simply identical to the self that exists now, and that treating them as identical wrongs the present self.

This is not an unreasonable claim. We intuitively accept it in many contexts. We don't generally think a person's childhood mistakes should follow them forever. We have statutes of limitations that encode a societal judgment that after sufficient time, even genuine wrongs should not be legally actionable. We rehabilitate, forgive, and offer second chances as social practices that presuppose the separability of present self from past action.

But here's the counter-pressure: the right to be forgotten, at scale, isn't just about individuals managing their personal narratives. It's about who controls the historical record, and whether that record can be selectively revised by the people it describes. And the people most motivated to invoke the right to be forgotten are often people whose pasts are most consequential — not the 19-year-old who made a foolish joke, but the powerful institution, the serial abuser who silenced victims through embarrassment, the corporation that wants to bury evidence of past misconduct.

This is sometimes called the **Streisand effect's darker cousin**: the right to be forgotten, if broadly interpreted, becomes a tool that amplifies existing power asymmetries. Powerful actors can afford the legal effort to pursue erasure; their victims often cannot. Institutions can invoke the right for data about their operations; individuals harmed by those institutions often cannot protect their own accounts of what happened. The GDPR framework is primarily designed around individual rights against large data processors, but the practical exercise of those rights is deeply shaped by resources, legal sophistication, and the specific nature of what one wants forgotten.

## Archival Theory's Response

Professional archivists have thought hard about this, and their frameworks are interesting. The archival concept of *provenance* — the idea that records derive their meaning partly from the context of their creation and custody — implies that records cannot be cleanly separated from the systems that generated them, including the people those systems documented. An individual's right to erasure, exercised against an archive, potentially corrupts the evidentiary integrity of the archive as a whole, not just removing one item.

There's also the concept of *original order* — the principle that archives are more valuable when records are preserved in the arrangement they had when created, because that arrangement itself carries information. If you allow selective removal of items from an archive based on subject-matter requests, you alter the archive's structure in ways that may distort its meaning for future researchers.

Archivists also raise what we might call the **silence problem**: edited records may be more misleading than complete records. An archive that contains most of a person's file but has had certain items removed on GDPR grounds creates a false impression of completeness. A researcher consulting it might not know the gaps exist. At least if a file doesn't exist at all, they know there's no file; if a file exists but is incomplete in invisible ways, they may draw false conclusions from apparent completeness.

Some archivists have proposed that rather than erasure, the appropriate response to legitimate privacy concerns is *restriction with notation* — keeping the record but restricting access and flagging that the record has been restricted and why. This preserves archival integrity (the record exists, its gaps are documented) while protecting the individual (it's not publicly accessible). This is roughly analogous to the sealed archival tier from our earlier discussion.

## The Specifically Digital Problem

What makes this conversation different from pre-digital archival ethics is the nature of digital persistence and the role of search and aggregation.

Before the internet, the right to be forgotten was largely self-executing through practical obscurity. A 30-year-old newspaper article was technically preserved in a library archive, but finding it required knowing to look for it, traveling to the library, and having the patience to search. The information was preserved but practically inaccessible except to determined researchers. This meant that ordinary people's old embarrassments, minor crimes, and youthful mistakes existed in the record but didn't functionally follow them through life.

The internet broke practical obscurity. Not because it created new records — newspapers always published names — but because it made all records simultaneously, instantly, and indefinitely accessible, and crucially, because search engines created aggregation: a single query for someone's name now returns every piece of information ever published about them, in seconds, ranked and presented in a way that makes certain things highly salient.

This is a profound qualitative change, not merely a quantitative one. The right to be forgotten in the digital context is often really a right to *re-establish practical obscurity* — not to destroy records, but to degrade their findability to something closer to what pre-digital existence involved. The *Google Spain* ruling is explicit about this: the underlying newspaper article could remain; only the search engine indexing needed to change. This is a sophisticated recognition that the harm is not the existence of the record but its aggregation and surfacing.

But this creates its own philosophical problem: if practical obscurity is restored by search delisting, and that's sufficient, then the right to be forgotten is really a right to control the architecture of information retrieval rather than a right to destroy information. The information still exists; it's just harder to find. For researchers, journalists, and people who know where to look, it remains accessible. For the person who had a one-night-stand with a dangerous individual and is now trying to understand their history, for the employer doing due diligence, for the historian — the information is still there. So the right to be forgotten is effectively a right to be forgotten by *casual searchers* rather than a right to be forgotten by *determined investigators*. Whether that's philosophically coherent or merely pragmatically useful is an interesting question.

---

# Part II: AI Training Data as a Form of Memory

## Setting Up the Problem

Now we move into territory that's newer, less legally settled, and philosophically even more interesting.

AI language models are trained on vast corpora of text. The largest models have been trained on effectively a significant fraction of all digitized human text — books, web pages, scientific papers, social media posts, legal documents, medical records that found their way online, private messages that were leaked or scraped, forum posts, news articles. This training process involves feeding text to a neural network in ways that cause it to adjust its internal parameters (weights) in response to patterns in the data.

The result is a model that, in a meaningful sense, has "learned from" all that text. It can reproduce styles, recall facts, discuss topics, continue passages — in ways that are clearly influenced by its training data, even if no training document is stored verbatim in the model's weights.

The question of whether this constitutes a form of "memory" with ethical weight requires us to think carefully about what memory is, what makes certain forms of memory ethically consequential, and what the model actually contains.

## What Is the Model Actually Storing?

This is a technical question with ethical implications, and it's worth being precise.

A trained neural network is a mathematical function parameterized by billions of numerical weights. These weights are updated during training in response to the training data, but they don't store the training data directly — they store a kind of compressed, overlapping, entangled statistical summary of patterns across all the training data simultaneously. Unlike a database, you cannot point to a specific weight and say "this weight stores the fact that X person said Y thing in Z forum post." The information is distributed, non-localized, and transformed beyond any simple retrieval mechanism.

However — and this is crucial — models can and do reproduce content from training data. This happens through what researchers call *memorization*, which is distinct from the general pattern-learning that models do. Memorization refers to cases where a model has, effectively, stored a specific sequence of tokens in recoverable form, usually because that sequence appeared frequently in the training data or was in some way distinctive. You can prompt a memorizing model to reproduce verbatim passages from its training data. Studies have demonstrated this with language models reproducing passages from copyrighted books, people's personal information from scraped web data, and other content that was presumably not intended to be reproduced by the model.

So the technical reality is mixed: models primarily store distributed statistical patterns rather than explicit records, but they also exhibit partial memorization of specific content, especially for frequently repeated or distinctive sequences.

This creates an interesting middle state between a database (explicit, addressable storage) and a mind (learning that influences behavior without explicit storage). The ethical implications differ depending on which model you apply.

## The Copyright Dimension

The most legally active dimension of AI training data ethics is copyright. Training a model on copyrighted text requires copying that text during the training process. The model then produces outputs that are influenced by (and in memorization cases, may reproduce) that copyrighted material. Content creators — authors, journalists, musicians, artists — have argued that this constitutes infringement. AI companies have argued that training constitutes fair use or equivalent transformative use in relevant jurisdictions.

This is genuinely legally unsettled, with major cases in progress. But the philosophical question underneath the legal one is interesting: what does it mean to "use" copyrighted material in a way that respects the creator's legitimate interest?

Copyright is commonly justified by several theories. The natural rights theory (Lockean) holds that creators own their work because they mixed their labor with it. The incentive theory holds that copyright is a social bargain: society grants creators temporary monopolies in exchange for the creative output they produce. The personality theory (more prominent in European law) holds that creative works are expressions of the creator's personality and therefore deserve protection as extensions of personal dignity.

AI training sits uncomfortably in relation to all three. Under labor theory: the model's creators did expend labor — but so did the content creators whose work was used without compensation. Under incentive theory: does allowing training on existing work reduce incentives to create future work? This is empirically uncertain, and the answer probably differs by domain — using a novelist's backlist to train a story generator may reduce their income; using scientific papers to train a research assistant probably doesn't reduce scientists' incentive to publish. Under personality theory: if a creator's work embodies their personality and distinctive voice, and a model learns to reproduce that voice, is this a dignity violation even if no specific text is reproduced?

The personality theory dimension is the most philosophically interesting for our purposes because it connects directly to the memory question. If a language model learns a writer's style deeply enough to produce convincing pastiche — not copying specific sentences, but genuinely capturing voice, rhythm, vocabulary, and thematic preoccupations — has it in some sense internalized that person's expressive identity? And if so, does the creator have any claim over that internalization?

This is not a crazy question. We'd generally find it troubling if a person could study another person's private diaries, journals, and correspondence in depth and then commercially exploit what they learned without the subject's consent — even if they didn't reproduce any verbatim passages. The intimate knowledge gained from extensive engagement with someone's expressive output feels like it ought to carry some ethical weight, even when the specific expressions aren't reproduced. AI training may be something like this at scale.

## The Privacy Dimension

Beyond copyright, there's a privacy problem that is in some ways more serious.

Training corpora contain personal information. Much of this information was technically public — posted on forums, in news articles, in court records that are public by legal design. But its inclusion in training data creates new concerns.

First, there's the **aggregation problem** again. A language model trained on vast data has effectively aggregated information about individuals in ways that allow inferences no single source would support. If you include someone's Reddit posts, their professional publications, their public social media, their mentions in news articles, and their court records, the model may effectively "know" things about them that aren't contained in any single source — patterns of behavior, health conditions that can be inferred from forum posts in medical communities, political views, relationship history. A sufficiently comprehensive training corpus combined with a sufficiently capable model creates a system that can, when prompted, reason about individuals in ways that draw on this aggregated knowledge even without explicit retrieval.

Second, there's the **contextual integrity** problem, a concept developed by philosopher Helen Nissenbaum. Nissenbaum argues that privacy is not primarily about secrecy — it's about appropriate information flow. Information flows appropriately when they match the norms of the context in which the information was shared. Medical information shared with a doctor flows appropriately to other treating physicians but not to employers. Personal struggles shared in a support forum flow appropriately among forum members but not to the public at large.

People share information in digital contexts with implicit norms about who will see it and how it will be used. A person who posted in a mental health forum in 2009 did so in a context with specific norms — a semi-public community with an implicit understanding of mutual support and discretion. That post being scraped and included in an AI training corpus violates contextual integrity even if the post was technically public, because the context in which it was shared did not include the norm "this will be used to train commercial AI systems."

This isn't just a theoretical concern. People have found that language models can be prompted to reproduce specific personal details that appeared in their training data — real names, addresses, phone numbers, personal disclosures. In memorization cases, the model effectively becomes a retrieval system for personal information that was collected without meaningful consent for that purpose.

Third — and this is where it gets philosophically deep — there's the question of what it means to have information about you *embedded* in a widely deployed system rather than *stored* in a database.

When your personal information is in a database, there's a kind of localization: it's there, it can be found, it can potentially be deleted. Data subject rights under GDPR are intelligible because you can point to a record and request its erasure. When your personal information has been used to train a model, it's distributed across billions of weights in a way that can't be pointed to, can't be isolated, and can't be erased without retraining the entire model. This is a genuinely new epistemic and ethical situation.

## The Right to Be Forgotten Applied to AI Training

Here's where our two topics collide with particular force.

GDPR's right to erasure, as discussed, includes an exception for archival and research purposes. AI training is claimed by companies to be a research or statistical purpose. Whether this holds up legally is contested — regulators in Italy and elsewhere have challenged it — but the more interesting question is whether it should hold up ethically.

Consider: a person requests that their personal data be deleted from a large AI company's training data. The company says: we cannot comply with this request because the data is not stored in retrievable form; it has been used to train a model whose weights are distributed summaries of all training data, and we cannot selectively "untrain" specific data points. This is technically accurate. It's also a description of a situation where a company has effectively made a person's right to erasure practically unexercisable by design — by using a training process that makes erasure impossible without destroying the entire model.

This is a governance and architecture problem with deep implications. The impossibility of erasure in trained models creates a kind of *de facto* permanent retention of personal data under statistical rather than explicit form. The data protection law's assumption that personal data is stored in addressable, deletable form is broken by this architecture. Companies that train on personal data are making a deliberate architectural choice — to use distributed training rather than database storage — that has the incidental (possibly convenient) effect of making their data retention practices non-compliant with the formal requirements of data protection law while allowing them to claim compliance because they don't "store" the data in the conventional sense.

Researchers have proposed technical solutions: *machine unlearning* algorithms that attempt to retrain or fine-tune a model to reduce the influence of specific training examples. These are real but imperfect — current unlearning techniques can reduce memorization of specific data points but cannot guarantee that all influence of a given training example has been removed, because the influence is distributed and entangled with the influence of other examples. It's a bit like trying to remove the influence of one specific conversation from a person's thinking — you might be able to suppress the explicit memory, but the distributed effects on how they think are much harder to target.

## AI as a New Kind of Cultural Memory

Let me now zoom out to the broader framing: AI training data as a form of collective or cultural memory.

Trained language models are, in an important sense, crystallizations of the textual culture from which they were trained. When you interact with a large language model trained on a broad corpus of human text, you're interacting with something that embodies patterns, values, assumptions, conceptual structures, rhetorical habits, and implicit knowledge from that corpus. It's a compressed, transformed, non-localized encoding of a huge swath of human expressive output.

This is analogous to cultural memory in important ways. Cultural memory refers to the ways in which collective representations of the past — myths, histories, rituals, monuments, institutions — shape a community's present understanding of itself. It's distinct from individual memory (which resides in persons) and archival memory (which resides in explicit records) by being distributed, embodied in practices and artifacts, and influencing behavior without necessarily being consciously retrieved.

Trained AI models do something structurally similar at civilizational scale. They embody patterns from the textual corpus of human civilization in a form that is distributed (across model weights), influences behavior without explicit retrieval (the model's outputs are shaped by training without "looking up" specific documents), and is resistant to targeted revision. If we deployed sufficiently capable AI systems widely enough that they significantly shaped human thought — education, writing, reasoning, creative work — then the biases, assumptions, and knowledge encoded in those training corpora would become a kind of invisible background structure shaping civilization's future thinking.

This is not science fiction. It's a description of something that may already be occurring. The specific corpus used to train widely deployed language models — which disproportionately represents English, Western, elite, and recent text — encodes specific perspectives and forecloses or deprioritizes others. The practical obscurity that historically existed around much of human cultural production is being broken, but selectively: the text that was digitized, the web pages that were crawled, the books that were scanned. The resulting model memory is a distorted mirror of human culture, not a faithful one.

## Who Controls the Memory?

This brings us to governance questions that parallel the archival governance questions from earlier.

When a civilization's cultural memory resided in libraries, archives, and human scholars, it was distributed across many institutions with different governance structures, political affiliations, national contexts, and access policies. No single actor could control what humanity "remembered." The diversity of custodians was itself a kind of protection against totalizing revision.

Large-scale AI training concentrates this in a new way. A small number of organizations are training models on corpora that represent much of digitized human knowledge. The decisions these organizations make about what to include, how to weight different sources, what to filter for safety or legal reasons, and how to handle conflicting representations of controversial events are decisions about what gets encoded in systems that may significantly influence how future humans think.

This is a form of cultural power with few historical precedents. It's not like controlling a library — the model doesn't just make knowledge accessible, it actively transforms it into a form that shapes outputs. It's not like controlling a publisher — the effects are distributed across billions of interactions rather than specific published works. It's closer to controlling the implicit curriculum of a civilization's educational system, except the "curriculum" is statistical patterns in weights that aren't legible even to their creators in any direct way.

The governance questions here are urgent and largely unresolved. Who should have oversight over what gets included in training corpora? Who represents the interests of people whose data is included? How should conflicting representations of contested historical events be handled? Should training corpora be subject to some kind of democratic accountability, or is this an impossible standard to apply to statistical processes? Should there be international standards, and if so, what institutional body has legitimacy to set them?

## The Deepfake of the Past

One final dimension worth exploring: the relationship between AI training and the malleability of historical record.

Language models trained on historical text can generate plausible-sounding historical content — documents, speeches, accounts — that didn't exist but are consistent with what the model has learned about a period. This creates a new kind of threat to historical integrity: the ability to generate convincing historical forgeries at scale.

Historical denialism has always existed, but it required either suppression of records or the fabrication of alternative ones — both of which left traces and required significant effort. AI models lower the cost of generating plausible-sounding alternative histories dramatically. They can produce, on demand, fake "primary sources" — letters, testimonies, official records — that are stylistically consistent with genuine historical documents.

This creates a paradox for the archival/AI memory question: the same systems that might serve as a form of cultural memory are also potential engines of memory corruption. A model trained on historical text can generate convincing historical forgeries; a model deployed widely enough shapes what "sounds right" to people encountering historical claims; a model used in educational contexts influences what future historians consider plausible.

The right to be forgotten, in this context, takes on a different valence. It's not just about individuals managing their personal records — it's about the possibility that AI systems trained on selective, distorted, or deliberately manipulated corpora could effectively "forget" true histories and "remember" false ones, at civilizational scale, in a distributed way that is very difficult to identify or correct.

---

# The Connection Between Both Topics

What unites these two discussions is a set of shared underlying questions about memory, power, identity, and time.

Both the right to be forgotten and AI training data ethics involve disputes about who controls the record of the past and for whose benefit. Both involve the tension between individual interests (in privacy, dignity, narrative control) and collective interests (in accurate historical record, cultural continuity, accountability). Both have been disrupted by digital architecture in ways that make pre-digital ethical frameworks inadequate. Both are being addressed through legal frameworks — GDPR primarily — that were designed for a different conception of how data is stored and used.

The specific challenge that AI training poses for the right to be forgotten is a kind of ultimate test case for the right's coherence: if personal data can be transformed into distributed model weights in a way that makes erasure technically impossible, does the right to erasure become meaningless? Or does it instead generate an obligation on system designers not to use architectures that make rights unexercisable?

I'd argue the latter. If a technology is designed in a way that systematically prevents the exercise of established rights, the ethical and ultimately legal response should be to constrain the technology's design, not to declare the rights void. The right to be forgotten is grounded in interests that don't disappear because a company found an architecture that makes them difficult to honor. The appropriate response is to require, as a condition of using personal data for training, that either the training process be modified to allow selective unlearning, or that consent be obtained in advance that is genuinely informed about how the data will be used and retained, or that the categories of data eligible for training be restricted in ways that protect the most vulnerable cases.

None of this is simple. But the difficulty of the problem is not a reason to conclude that it doesn't need solving — it's a reason to invest serious thought, governance effort, and institutional design into solving it, which is more or less what we've been doing here.
