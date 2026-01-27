## Text-to-Text Generation Pipeline

The project uses the Hugging Face `text2text-generation` pipeline to convert meeting transcripts into concise action items and key decisions.
This pipeline simplifies the process by handling tokenization, model inference, and text generation internally.
It allows automatic minutes generation to be implemented with minimal code.


## Model Used

The model used for meeting summarization is `sshleifer/distilbart-cnn-12-6`.
It is a distilled version of the BART model trained on the CNN/DailyMail dataset for abstractive summarization.
The model is optimized for speed and works efficiently on CPU while maintaining good summarization quality.

## Why distilbart-cnn-12-6

The distilbart model was chosen because it provides a balance between performance and speed.
It is suitable for summarizing long meeting transcripts and extracting key decisions and action items.
Since it is a lightweight model, it can be easily executed on local machines without GPU support.

## Working of the Meeting Minutes Generator

The generator first encodes the meeting transcript to understand the discussion context.
It then decodes the most important information to generate a shorter version highlighting key decisions.
The model focuses on identifying critical points such as deadlines, action items, and responsibilities assigned.


## Limitations

The distilbart summarizer may produce outputs that closely resemble parts of the original transcript.
This behavior occurs because the model focuses on extracting important sentences rather than heavily paraphrasing the content.
It performs best when the meeting transcript is detailed and clearly structured with speaker identifications.
It may miss implicit decisions if they are not explicitly stated in the transcript.
