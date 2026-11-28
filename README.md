# IAT 360 Group 17: Document Simplifier Chatbot

Manroop Sandhu, Sean Penner, Kent Nguyen, Marielle Reyes Lao

We fine-tune Qwen2.5-7B-Instruct (with LoRA) to do sentence-level text simplification: given a complex sentence, generate a simpler one that keeps the same meaning. We then apply it to real documents (government forms, policies, guides), simplifying page by page.

Confirmed with Dr. Yalcin and TA Minoo that this is an Option 1 project (training a model). Our first idea used RAG to build a Q&A chatbot, but that's not the right fit for a simplification task, so we dropped it.

- Model: Qwen2.5-7B-Instruct, fine-tuned with LoRA
- Training data: WikiAuto, via the `GEM/wiki_auto_asset_turk` dataset (complex/simple Wikipedia sentence pairs)
- Evaluation: SARI + Flesch-Kincaid grade level on ASSET (the `test_asset` split of that same dataset), comparing our fine-tuned model against the un-tuned base model

## Data
- **Training/evaluation data** comes from Hugging Face (`GEM/wiki_auto_asset_turk`), loaded directly in the notebook.
- **Test documents**, one per person, all public, for checking how the model handles real government/legal text instead of Wikipedia sentences. Not uploaded here (ICBC's guide is copyrighted, so we're playing it safe with all of them) — keep PDFs in `data/`, which is gitignored.
  - ICBC Learn to Drive Smart guide, https://www.icbc.com/driver-licensing/driving-guides/Pages/Learn-to-Drive-Smart
  - SFU Policy S10.01, Code of Academic Integrity, https://www.sfu.ca/policies/gazette/student/s10-01.html
  - Canadian adult passport application, https://www.canada.ca/en/immigration-refugees-citizenship/services/canadian-passports/new-adult-passport/get-application-form.html
  - BC annual property tax info, https://www2.gov.bc.ca/gov/content/taxes/property-taxes/annual-property-tax

## Code
`Group17_DocumentSimplifier.ipynb`, run in Colab with a T4 GPU. Still a work in progress — see the TODO list at the end of the notebook.
