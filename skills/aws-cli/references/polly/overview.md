# AWS CLI v2 — Polly (Text-to-Speech)

## Overview

Complete reference for all `aws polly` subcommands in AWS CLI v2. Covers real-time speech synthesis, asynchronous synthesis tasks with S3 output, voice discovery, and pronunciation lexicon management. Polly supports standard, neural, long-form, and generative speech engines across 40+ languages.

## Quick Reference — Common Workflows

### Synthesize speech to an MP3 file
```bash
aws polly synthesize-speech \
  --text "Hello, welcome to Amazon Polly." \
  --voice-id Joanna \
  --output-format mp3 \
  output.mp3
```

### Synthesize speech using SSML
```bash
aws polly synthesize-speech \
  --text-type ssml \
  --text '<speak>Hello <break time="500ms"/> world!</speak>' \
  --voice-id Matthew \
  --output-format mp3 \
  --engine neural \
  output.mp3
```

### List available neural voices for English
```bash
aws polly describe-voices \
  --language-code en-US \
  --engine neural \
  --query 'Voices[].{Name:Name,Gender:Gender,Id:Id}'
```

### Start an asynchronous synthesis task (large text)
```bash
aws polly start-speech-synthesis-task \
  --text file://long-text.txt \
  --voice-id Joanna \
  --output-format mp3 \
  --output-s3-bucket-name my-audio-bucket \
  --output-s3-key-prefix audio/
```

### Check synthesis task status
```bash
aws polly get-speech-synthesis-task \
  --task-id 70b61c0f-57ce-4715-a247-cae8729dcce9
```

### Create a pronunciation lexicon
```bash
aws polly put-lexicon --name MyLexicon --content file://lexicon.pls
```

### Synthesize with a lexicon applied
```bash
aws polly synthesize-speech \
  --text "AWS is great." \
  --voice-id Joanna \
  --output-format mp3 \
  --lexicon-names MyLexicon \
  output.mp3
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Synthesis | [`synthesis.md`](synthesis.md) | synthesize-speech, start-speech-synthesis-task, get-speech-synthesis-task, list-speech-synthesis-tasks, describe-voices |
| Lexicons | [`lexicons.md`](lexicons.md) | put-lexicon, get-lexicon, delete-lexicon, list-lexicons |
