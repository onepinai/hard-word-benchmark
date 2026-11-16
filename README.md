# Onepin Hard-Word Pronunciation Benchmark

**Version 1.0 · 27 commercial TTS models · 2,700 clips · 484 hard words · English (US) · [Onepin](https://onepin.ai) Research · Benchmark runs October 2026 · Published November 2026**

Text-to-speech leaderboards score how natural a voice sounds and how fast it renders. They do not score whether it says Quelimane, Jaworzynka or ReVia the way the people who live there, or take it, do. In a documentary, an audiobook, a training course or a pharmacy line, that is the error the listener remembers.

This benchmark measures it. We wrote 100 sentences, each around four or five hard words: cities, people, drugs, brands, mountains, mythology, 484 words in all. We generated every sentence with 27 commercial TTS models, the providers integrated in [Onepin](https://onepin.ai) at the time, 2,700 clips in all, and scored the pronunciation of every clip sound by sound, before and after Onepin's pronunciation check and correction had run on it.

## Results

PED is Onepin's pronunciation check. It listens to the audio, writes down each speech sound it hears, and compares them with the accepted pronunciations of the words. Pronunciation accuracy scores the line. Hard words read right scores the names inside it.

| | Source TTS | With Onepin |
|---|---|---|
| **Pronunciation accuracy** · Onepin's sentence score, 0 to 100: the share of sounds heard right, minus a deduction for each hard word read wrong (the PED score) | **90.0%** | **98.0%** |
| **Hard words read right** · share of the 13,068 hard-word readings within one sound of an accepted reading | **44.8%** | **87.8%** |

<sub>484 hard words read by 27 models: 13,068 readings in 2,700 clips. 95% intervals: pronunciation accuracy 89.4–90.5 and 97.7–98.3; hard words 42.1–47.7 and 86.0–89.7.</sub>

**Source TTS gets most sounds right. The ones it gets wrong are in the names.** Before Onepin the 27 models score 85.9% to 92.3% on pronunciation accuracy; the best is Google Cloud gemini-3.1-flash-tts. The wrong sounds sit almost entirely inside the hard words: source TTS reads more than half of them wrong, and only 2 sentences in 100 come out with every hard word right.

**With Onepin, 88 hard words in 100 are right**, and 52 sentences in 100 have every hard word right, between 42 and 60 depending on the model.

**Every one of the 27 models improves, and the spread closes.** On pronunciation accuracy 27 of 27 improve, by 6.2 points at the least, and finish within two points of each other, 96.6% to 98.5%. A second, public recogniser that took no part in the correction confirms the gain for all 27. The choice of TTS still matters for the voice. For the names, the check matters more.

**It is the number Onepin shows on every line.** The PED score counts every sound in the sentence and adds a penalty for each hard word read wrong, so one mispronounced name costs a sentence more than its share of sounds. Onepin shows it on every line it delivers, on the same scale as here.

## Leaderboard

Ranked by the pronunciation accuracy of the source TTS. Each model read all 100 sentences on 20 September 2026 with each provider's default settings, plain-text input and no pronunciation controls, with voices drawn from the provider's English catalogue (1,383 distinct voices; every clip's provider, model and voice is listed in `clips_full` on Hugging Face). Onepin columns use the same setting for every model. Two providers are shown as Provider A and Provider B, with their model and voice names withheld, because their terms of service restrict publishing benchmark results that name them. Provider names link to their product pages; no provider is affiliated with or endorses this benchmark.

| # | Provider | Model | Pronunciation accuracy, source | Pronunciation accuracy, Onepin | Hard words right, source | Hard words right, Onepin |
|---|---|---|---|---|---|---|
| | **All 27 models** | | **90.0%** | **98.0%** | **44.8%** | **87.8%** |
| 1 | [Google Cloud](https://cloud.google.com/text-to-speech) | gemini-3.1-flash-tts | 92.3% | 98.5% | 55.6% | 89.9% |
| 2 | [Microsoft Azure](https://azure.microsoft.com/en-us/products/ai-foundry/tools/speech) | mai-voice-2 | 91.8% | 98.5% | 52.3% | 90.3% |
| 3 | [OpenAI](https://developers.openai.com/api/docs/guides/text-to-speech) | gpt-4o-mini-tts | 91.5% | 98.4% | 51.2% | 89.7% |
| 4 | [Cartesia](https://www.cartesia.ai/) | sonic-preview | 91.4% | 98.2% | 50.4% | 88.8% |
| 5 | [Alibaba Qwen](https://qwen.ai/) | qwen-audio-3.0-tts-flash | 91.4% | 97.9% | 50.4% | 86.2% |
| 6 | [ElevenLabs](https://elevenlabs.io/) | eleven_multilingual_v2 | 91.1% | 98.3% | 50.4% | 89.7% |
| 7 | [Inworld](https://inworld.ai/tts) | inworld-tts-2 | 91.0% | 98.5% | 49.6% | 90.7% |
| 8 | [ElevenLabs](https://elevenlabs.io/) | eleven_flash_v2_5 | 90.7% | 97.7% | 47.5% | 86.6% |
| 9 | [Microsoft Azure](https://azure.microsoft.com/en-us/products/ai-foundry/tools/speech) | dragonhdlatestneural | 90.6% | 98.1% | 48.1% | 88.2% |
| 10 | [ElevenLabs](https://elevenlabs.io/) | eleven_turbo_v2_5 | 90.6% | 97.4% | 47.7% | 85.1% |
| 11 | [MiniMax](https://www.minimax.io/audio) | speech-2.8-hd | 90.5% | 97.8% | 46.5% | 87.0% |
| 12 | [Inworld](https://inworld.ai/tts) | inworld-tts-1.5-max | 90.4% | 98.4% | 46.7% | 89.7% |
| 13 | [Alibaba Qwen](https://qwen.ai/) | qwen-audio-3.0-tts-plus | 90.3% | 97.6% | 45.9% | 85.7% |
| 14 | Provider B | undisclosed | 90.3% | 98.4% | 44.8% | 89.3% |
| 15 | [Google Cloud](https://cloud.google.com/text-to-speech) | wavenet | 90.1% | 98.5% | 45.2% | 90.1% |
| 16 | [Amazon Polly](https://aws.amazon.com/polly/) | long-form | 90.0% | 98.3% | 46.1% | 88.4% |
| 17 | [ElevenLabs](https://elevenlabs.io/) | eleven_v3 | 90.0% | 96.9% | 47.5% | 82.4% |
| 18 | [Gradium](https://gradium.ai/) | default | 89.9% | 98.1% | 43.4% | 87.8% |
| 19 | [Cartesia](https://www.cartesia.ai/) | sonic-3.5 | 89.8% | 98.4% | 43.4% | 89.5% |
| 20 | [Fish Audio](https://fish.audio/) | s2-pro | 89.7% | 98.0% | 42.8% | 87.4% |
| 21 | [Microsoft Azure](https://azure.microsoft.com/en-us/products/ai-foundry/tools/speech) | neural | 89.7% | 98.1% | 43.2% | 87.6% |
| 22 | Provider A | undisclosed | 88.8% | 98.1% | 39.3% | 88.0% |
| 23 | [Rime](https://www.rime.ai/) | coda | 88.8% | 97.9% | 39.5% | 87.8% |
| 24 | [Respeecher](https://www.respeecher.com/) | respeecher-tts | 88.2% | 97.5% | 38.6% | 86.4% |
| 25 | [Naver](https://www.ncloud.com/product/aiService/clovaVoice) | clova | 87.9% | 98.4% | 35.3% | 89.9% |
| 26 | [Rime](https://www.rime.ai/) | mistv2 | 86.1% | 97.0% | 30.8% | 85.7% |
| 27 | [Respeecher Marketplace](https://marketplace.respeecher.com/) | marketplace | 85.9% | 96.6% | 28.3% | 83.3% |

<sub>100 clips per model give intervals of about ±4 points on source hard-word accuracy and ±3 after correction, so neighbouring ranks are not distinguishable. The second judge's columns are in `data/models.csv`.</sub>

## Where TTS goes wrong

The hardest categories for source TTS are names of volcanoes, rivers, islands, fortresses and religious buildings, 27.6% to 35.0% of readings right, with cities, the largest category, close behind at 36.2%. The easiest are words that appear in English text every day: software, companies, computer-science terms and sports, 74.1% down to 65.3%.

Three corrections from the released showcase clips, as PED transcribed the audio, written as plain respellings:

| Word | Reading | Source TTS said | With Onepin | Clip |
|---|---|---|---|---|
| Quelimane, a city in Mozambique | keh-lee-MAH-nee | kwell-uh-MAHN | keh-luh-MAH-nee | Qwen 3.0 TTS Plus, sentence 3 |
| Jaworzynka, a village in Poland | yah-vo-ZHIN-kah | chuh-WOR-zink-uh | yah-vo-ZHIN-kuh | Qwen 3.0 TTS Plus, sentence 3 |
| Loge, a moon of Saturn | LOH-ghee | lodge | LOH-ghee | Google WaveNet, sentence 4 |

The model reads the spelling as English, so *Qu* becomes *kw* and *Loge* rhymes with *lodge*. The correction keeps the speaker's voice.

## Listen

70 showcase clips, five per model for 14 models, play in the browser on the [Hugging Face dataset viewer](https://huggingface.co/datasets/onepin/hard-word-benchmark/viewer/showcase_audio), each as the provider generated it (`source`) and after Onepin (`onepin`), with its sentence, voice and PED score. Each clip's `words.json` on Hugging Face lists the words PED flagged and corrected. The clips were chosen by a fixed rule with no listening, the five per model where the most hard words went from wrong to right by both judges, so they show the pipeline at its best.

All showcase audio is AI-generated synthetic speech; every `onepin` version is the provider's audio modified by Onepin. Audio is released only where the provider's terms allow it; for the other 13 models only aggregate scores are released.

## Run it on your own script

The same check and correction run inside any [Onepin](https://onepin.ai) workflow: add the pronunciation check and the Pronunciation Corrector to a workflow and run your script through it.

## How it is measured

**What is measured.** PED transcribes each hard word into the speech sounds it hears and compares them with the word's accepted readings. Every clip is measured as the provider generated it and after Onepin's pronunciation check and correction.

**Pronunciation accuracy** is the PED score, from 0 to 100, written here as a percentage: 100 minus the percentage of sounds in the sentence PED heard wrong, minus a deduction for each hard word read wrong (three points for a clearly wrong word, one for a borderline one), never below zero.

**Hard words read right** is the share of hard-word readings within 0.25 wrong, missing or extra sounds per sound of an accepted reading: one wrong sound in a word of four to seven sounds, two in a word of eight to eleven.

**Readings.** Each word has a primary reading in IPA and, where legitimate variants exist, further accepted readings, checked against dictionaries, Wikipedia, Wiktionary and official sources. The readings are in `data/sentences.csv`. Disputed readings can be raised as an issue; a changed reading gets a changelog entry and a re-score.

[docs/METHOD.md](docs/METHOD.md) has the full scoring rule, the second judge and the statistics. In a blind human listener study, PED caught 9 in 10 of the pronunciation errors listeners heard in source TTS. A blind listener evaluation of the benchmark audio will be released with version 1.1 and the accompanying paper.

## Independence and limits

This benchmark was built, run and judged by Podonos, the maker of Onepin. No provider paid for inclusion, was consulted on the set or saw the results before publication. The source-TTS columns do not depend on Onepin.

- **PED is also part of Onepin's correction**, so its corrected numbers are an upper bound; the second recogniser confirms the gain for every model.
- **Provider defaults, plain text, US English, one snapshot** (20 September 2026).

## What comes next

Version 1.1 adds a blind listening round on this audio and a re-run with one fixed voice per model. Version 2 moves to a held-out sentence set with new words.

## What is in this repository

| Path | Contents |
|---|---|
| `data/sentences.csv` | The 100 sentences, their hard words, and each hard word's target IPA reading and accepted alternatives. The sentences are fiction written for the test; statements in them about real people, places, products or medicines are invented |
| `data/models.csv` | The per-model table: pronunciation accuracy, hard-word accuracy and the second judge, source and after Onepin, with intervals |
| `data/results.json` | Aggregate results with bootstrap intervals, per category and per provider |
| `data/providers.csv` | The provider catalogues and their product pages, as linked in the leaderboard |
| `docs/METHOD.md` | The scoring rule, the second judge, statistics |

Per-clip scores for all 2,700 clips, the showcase audio with a player and each showcase clip's per-word outputs are on Hugging Face: [huggingface.co/datasets/onepin/hard-word-benchmark](https://huggingface.co/datasets/onepin/hard-word-benchmark). Per-word results outside the showcase clips and the rest of the audio are held back.

## Licence

Text, readings, labels and judge outputs: [CC BY 4.0](LICENSE). The showcase audio on Hugging Face is AI-generated output of third-party TTS services, provided for listening and comparison only, and remains subject to each provider's terms. It may not be used to train, fine-tune, develop or improve any AI model, or to build a competing product or service.

## Citation

```
Podonos (2026). Onepin Hard-Word Pronunciation Benchmark, version 1.0.
https://github.com/onepinai/hard-word-benchmark
```

A `CITATION.cff` is included. Questions and disputed readings: open an issue or write to research@podonos.com.

[Onepin](https://onepin.ai) is Podonos's voice production agent. It plans, generates, validates and retries every line of a script before it ships. Listen to the showcase clips, run your own script through Onepin, and tell us where a reading is wrong.
