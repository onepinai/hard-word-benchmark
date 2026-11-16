# How the benchmark is measured

This page gives the scoring rule, the second judge and the statistics behind the numbers in the README. The full method, including the phone distance, the judge-agreement analysis and per-word results, will follow in a paper.

## The set

100 sentences, written for the test around 484 hard words in 32 categories: cities, rivers, mountains, people, drugs, brands, software, mythology and more. Each sentence carries four to five hard words. The sentences are fiction; statements in them about real people, places, products or medicines are invented. 36 of them, the sentences behind the showcase clips, are released with their hard words in `data/sentences.csv`; the rest are held back.

27 commercial TTS models from 17 provider catalogues read all 100 sentences: 2,700 clips, 9.5 hours of audio, 13,068 hard-word readings. Audio was generated on 20 September 2026 with each provider's default settings, plain text and no pronunciation controls. Each clip took a voice from the provider's English catalogue, cycling through it: 1,383 distinct voices in all (1,613 model-voice pairs; a voice shared across a provider's models is counted once), from 4 to 100 per model. Voice counts per model are in `data/models.csv`.

## How Onepin was run

Every clip went through Onepin's pronunciation check and correction, the same feature Onepin users run on their own scripts. It finds the words read wrong and corrects them in the speaker's voice. The headline figures use Onepin's highest-quality setting.

PED, Onepin's pronunciation check, is also the judge: it transcribes each hard word into the speech sounds it hears and compares them with the word's accepted readings.

## The three measures

**Pronunciation accuracy**, the PED score, is the pronunciation score Onepin shows on every line it delivers, from 0 to 100 and written as a percentage in this benchmark. It is 100 minus the percentage of sounds in the whole sentence that PED heard wrong, minus a flat deduction for each hard word it flagged: three points for a word it rates clearly wrong, one for a borderline one, floored at zero. The deduction is what makes a mispronounced name cost more than its share of sounds. 100% means PED heard every sound as an accepted reading and flagged nothing. The score is reported for continuity with the product; it is not comparable with word-level scores from other benchmarks. Because most sounds in a sentence belong to ordinary words that every model reads right, pronunciation accuracy moves less than the hard-word measures: from 90.0% to 98.0% across the set, while hard-word accuracy moves from 44.8% to 87.8%.

**Hard words read right** is the share of the 13,068 hard-word readings that pass. A reading passes when the number of wrong, missing or extra sounds in PED's transcription, divided by the number of sounds in the accepted reading, is at most 0.25: one wrong sound in a word of four to seven sounds, two in a word of eight to eleven, none in a word of three or fewer. Each wrong, missing or extra sound counts one; sound similarity is used only to line the two transcriptions up. The alignment details follow in the paper. Exact matches, with no sound wrong, are rarer: 13.8% of readings in the source audio and 25.7% after Onepin.

**Clips with every hard word right** is the share of the 2,700 clips in which every hard word passed.

## The readings

Each of the 484 words has a primary reading in IPA and, where legitimate variants exist, further accepted readings. A language-model agent checked each against dictionaries, Wikipedia, Wiktionary and official sources, and the released `data/readings.json` gives the target reading and accepted alternatives for the 178 hard words in the released sentences. No phonetician reviewed the list. For 86 words the evidence was thin. Those are scored leniently: every reading the checker proposed counts as accepted, plus a common alternative reading unless the checker found a definite fault in it. Scoring only the other 398 words moves the hard-word figures by under a point (44.1% → 87.8% by PED). Disputed readings can be raised as an issue on this repository. A changed reading gets a changelog entry and a re-score.

## Where TTS goes wrong

Hardest first. The hardest categories for source TTS are foreign place names. The easiest are words that appear in English text every day.

| Category | Words | Readings | Hard words right, source | Hard words right, Onepin |
|---|---|---|---|---|
| Volcano | 13 | 351 | 27.6% | 74.1% |
| River | 16 | 432 | 30.6% | 81.3% |
| Island | 13 | 351 | 31.1% | 83.2% |
| Fortress | 9 | 243 | 35.0% | 96.3% |
| Religious building | 24 | 648 | 35.0% | 89.8% |
| Battle | 13 | 351 | 35.3% | 86.9% |
| City | 51 | 1,377 | 36.2% | 83.1% |
| Lake | 8 | 216 | 37.0% | 91.2% |
| Asteroid or comet | 17 | 459 | 38.6% | 92.6% |
| Mythology | 39 | 1,053 | 40.8% | 87.8% |
| Mountain | 20 | 540 | 41.7% | 76.9% |
| Holiday | 6 | 162 | 42.0% | 80.9% |
| Person | 29 | 783 | 42.9% | 83.9% |
| Music genre | 12 | 324 | 45.1% | 92.0% |
| Brand | 9 | 243 | 45.7% | 91.0% |
| University | 17 | 459 | 46.0% | 77.6% |
| Dance | 10 | 270 | 46.3% | 92.2% |
| National park | 12 | 324 | 46.6% | 92.3% |
| Ship | 14 | 378 | 47.1% | 86.0% |
| Archaeological site | 26 | 702 | 47.3% | 93.6% |
| Music group | 6 | 162 | 47.5% | 93.2% |
| Museum | 7 | 189 | 49.2% | 90.5% |
| Food | 16 | 432 | 50.0% | 94.4% |
| Railway station | 6 | 162 | 50.6% | 82.1% |
| Art movement | 14 | 378 | 50.8% | 87.6% |
| Video game | 7 | 189 | 55.6% | 82.0% |
| Medicine (drug, condition) | 26 | 702 | 60.8% | 91.9% |
| Glacier | 5 | 135 | 61.5% | 99.3% |
| Sport | 14 | 378 | 65.3% | 96.8% |
| Computer science | 4 | 108 | 72.2% | 100.0% |
| Company | 10 | 270 | 72.6% | 95.6% |
| Software | 11 | 297 | 74.1% | 99.0% |


## A second judge

PED is also part of Onepin's correction, which makes its numbers on corrected audio optimistic. So every clip was also judged by a second speech-sound recogniser, the public model `facebook/wav2vec2-lv-60-espeak-cv-ft`, with four of its symbols folded onto PED's inventory so the two judges share one alphabet. It was never consulted during correction and is scored by the same rule.

| Hard words read right | Source TTS | With Onepin |
|---|---|---|
| PED, Onepin's check | 44.8% | 87.8% |
| Second judge, public recogniser | 41.5% | 67.8% |

95% intervals: PED 42.1–47.7 and 86.0–89.7; second judge 39.3–43.6 and 65.7–70.0. By the second judge, clips with every hard word right go from 1.3% to 16.2%.

The second judge confirms the direction for every one of the 27 models, with a smallest gain of 15.5 points. It lands lower on corrected audio because it did not choose the recordings: read PED's column as the upper bound and the second judge's as the conservative estimate.

Per-model second-judge numbers are the `heldout_*` columns of `data/models.csv`.

## Listeners

In a blind human listener study, PED caught 9 in 10 of the pronunciation errors listeners heard in source TTS. A blind listener evaluation of the benchmark audio will be released with version 1.1 and the accompanying paper.

## Statistics

Every rate carries a 95% interval from a cluster bootstrap over the 100 sentences, 2,000 draws, seed 7. A sentence's 27 clips share its words, so the sentence is the unit of resampling, and per-model intervals on 100 clips are about ±4 points on source hard-word accuracy and ±3 after correction. Gains are paired: the same clip before and after. All figures come from the run's full outputs, summarised in `data/results.json` and `data/models.csv`.

## What is withheld

This is a closed benchmark. Released: 36 of the 100 sentences with their hard words and readings, the audio and per-word judge outputs of the 70 showcase clips, per-clip scores for all 2,700 clips, and the aggregate tables. The other 64 sentences, their readings, the per-word outputs for the rest of the set and more than 97% of the audio are held back, so the corrected audio cannot be used to train a corrector and neither the text nor the audio can be used to tune a model or a detector to this set. The recogniser is not released.
