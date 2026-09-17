# Mister Sparkle

Documentation that people enjoy reading often has a distinct voice: rhythm, well-chosen idiom, concrete examples, and sometimes humor. The approach isn't suitable for all kinds of technical content. But when it supports the content rather than distracting from it, that voice is kind of a superpower. Engaged readers are much more likely to keep going even when the material is dry or challenging.

But those engaging qualities can make documentation hard to translate and difficult for some readers to understand. Machine translation systems are better than they were, but they still struggle with source-language-specific idiom, tone, and cultural context.

The Mister Sparkle experiment aims to retain reader engagement while improving translatability. Strip the sparkle; retain meaning, terminology, constraints, warnings, and uncertainty; translate what's left; re-inject sparkle in the target language.

## The AI opportunity

In 1980, the aerospace industry adopted Simplified Technical English, an English dialect that defines specific vocabulary and sentence structures that make documentation more understandable and translatable. Similar approaches have since been widely adopted in global enterprises.

Writers consistently report that writing in these restricted dialects is soul-crushing, and demotivated writers are less likely to produce their best work.

A chain of LLM-assisted transformations may make it possible to produce documentation that is both enjoyable to read and easier to translate. The first transformation removes language that is difficult to translate while retaining technical meaning, constraints, uncertainty, terminology, or the document’s task structure. The resulting intermediate English would not be strictly Simplified Technical English, but it might occupy similar territory. (Fortunately, LLMs don't have souls to crush.)

This intermediate English version may be useful as a plain-language or controlled-language reading option for readers who prefer direct, low-idiom prose. It's also the input to the next transformation: translation. Reducing idiom and other source-language-specific phrasing might make automated translation more reliable and easier to evaluate.

After translation, we have a simplified Japanese (for example) document that can be published for readers who prefer low-idiom content. AI can then revise that translation into natural, engaging Japanese for its intended audience, using Japanese rhetorical conventions rather than literal English idioms.

We can also "translate" the simplified English version back into idiomatic English, essentially performing a controlled rewriting or editorial normalization pass. That wasn't our original goal, but for some teams, it might actually be Mister Sparkle's primary use case.

## Project status

Mister Sparkle is an experiment and will remain one for the indefinite future. We will develop prompts and reusable skills to achieve the necessary content transformations, along with a rubric for evaluating their effectiveness.

Open questions include, among many:

- What must an intermediate representation preserve to support faithful translation and natural target-language rewriting?
- How do we effectively prompt generation of intermediate representations?
- How much guidance must we provide about the desired target-language voice after translation?
- Do Japanese prompts, for example, work better with Japanese documents than English prompts?
- Which models work best for each stage of the pipeline?
- Which model parameters, such as `temperature` and `top-p`, improve consistency without degrading quality?
- How can we minimize token use in pre-translation and post-translation processing?
- For which document types, language pairs, and risk levels can human review be reduced or eliminated?

It may be that our undertaking is fundamentally infeasible now, or that only some stages of the pipeline can be made effective. That's a useful finding in itself. We'll learn more about the current limits of machine translation and develop metrics for evaluating future language models on the task.

## How you can help

Please suggest approaches, prompts, and other ideas here by raising issues and creating pull requests. For example:

- Source documents, especially deliberately difficult test passages
- Transformation prompts and reusable skills
- Structured representations or annotation guidelines
- Target-language rewrites for languages you know
- Bilingual evaluation rubrics and translation-quality metrics
- Translation-error definitions and taxonomies
- Reproducibility practices, including model, version, and prompt records

I'm looking for bilingual volunteers to evaluate translation effectiveness. Please contact me at engyrus@gmail.com. Spammer no spamming!

## About me

I'm Jerry Kindall, an experienced technical communicator (formerly with AWS, Snowflake, and Microsoft) engaging with AI to improve the effectiveness of technical documents.

Another of my projects is Charlie, a restricted English dialect intended for writing more reliable AI prompts and skills while preserving readability. We might use Charlie concepts in our Mister Sparkle prompting.

## The name

*Of course* t's a Simpsons reference: "In Marge We Trust," season 8, episode 22. The goal of our project is to use AI to retain the engaging qualities ("sparkle") of prose during translation. The name sprang immediately into my head and wouldn't leave.

I spell out "Mister" to help people find the project without wading through a sea of Simpsons fan pages.

## Suggested reading

There's no requirement to read anything in particular, laymen's thoughts are just as valuable here as those of seasoned AI practitioners or researchers, but you might find these useful.

If you only read one thing for this project, make it this book. It is the conceptual anchor for defining "essential traits" when moving across language boundaries. Translating poetry is Mister Sparkle on hard mode. And it's an enjoyable, stimulating read.

*Le Ton beau de Marot: In Praise of the Music of Language,* Douglas Hofstadter, Basic Books, 1997. ISBN 0-465-08645-4. Noted AI researcher explores translation issues by collecting dozens of translations of a light French poem ("Ma Mignonne" by Clément Marot) into English. It includes several 1997-era machine translations, which are as dreadful as you'd expect. The book's title is a multi-layered pun.

### Technical Track: LLM Architecture & Controlled Generation (Optional)

*For volunteers interested in how engineering frameworks isolate abstract concepts and enforce stylistic constraints.*

* **"Attention Is All You Need"**
  * **Authors:** Vaswani et al. (2017)
  * **Why it matters:** The foundational paper that introduced the Transformer architecture. It explains the "Attention" mechanism, which is mathematically how our models decide which semantic features are essential and which are noise.
* **"Decomposing Language Models Into Understandable Components"**
  * **Source:** Anthropic Research (2024)
  * **Why it matters:** Investigates *monosemanticity*—the ability to map specific internal LLM features to abstract concepts (like irony, tone, or idioms). This provides the theory behind stripping out non-essential stylistic traits.
* **"Controlled Text Generation"**
  * **Source:** Survey Papers via ACL Anthology
  * **Why it matters:** Explores the mechanics of style transfer and text simplification, offering direct insight into how we configure an LLM to output a restricted, un-idiomatic version of English.

---

### Theory Track: Translation Foundations & Metrics (Optional)

*For volunteers curious about the historical philosophy of translation and how modern systems measure automated accuracy.*

* **"The Task of the Translator"**
  * **Author:** Walter Benjamin (1923 essay)
  * **Why it matters:** A classic philosophical text arguing that translation should not try to copy the original's surface style, but rather expose the "pure language" hidden underneath. Our un-idiomatic pivot text is conceptually very close to this ideal.
* **Neural Machine Translation**
  * **Author:** Philipp Koehn
  * **Why it matters:** The definitive engineering textbook tracing translation models from classic statistical frameworks to modern deep learning structures.
* **Speech and Language Processing (Chapter 11: Machine Translation)**
  * **Authors:** Daniel Jurafsky and James H. Martin
  * **Why it matters:** Provides an excellent overview of algorithmic evaluation metrics (like BLEU) and sequence-to-sequence pipelines, helping us understand how to evaluate our target outputs.
