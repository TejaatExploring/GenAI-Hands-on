## What I Understood

Model architecture matters a lot. BERT and RoBERTa are encoder-only, so they're good at understanding tasks but can't generate text. BART is encoder-decoder, which lets it generate but it needs fine-tuning for good results. The tokenizer differences also play a role—different models use different mask tokens, which affects how they process inputs.

## What I Implemented

I tested BERT, RoBERTa, and BART on three tasks: text generation, fill-mask, and question answering. Used Hugging Face pipelines to run the experiments and recorded what worked and what didn't. The key finding was that encoder-only models failed at generation while encoder-decoder BART could generate (though poorly without fine-tuning). For fill-mask, BERT and RoBERTa performed well since they're trained on MLM.

## Challenges Faced

Different models needed different mask tokens ([MASK] for BERT, <mask> for RoBERTa and BART). Also got some warnings about loading models for tasks they weren't fine-tuned for, which actually made sense once I understood what was happening. The BART model had some checkpoint issues but still ran.


## Tools Used
- Python
- Hugging Face Transformers 