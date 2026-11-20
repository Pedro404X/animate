# Log: history-of-ai

## Run 1 - 2026-11-20 (verification run: build, export, review, visual pass; no code changes)

- **Environment:** Linux x86_64 cloud container, Node 22.23, Playwright 1.63 + Chromium (pre-installed), ffmpeg 6.1.1, 4 CPUs, no GPU (software rendering; fine for this 2D canvas piece).
- **Time, outputs:** build ok (1830 lines from 10 parts, style cut-paper, syntax ok, no external assets). Export `--share` 6m19s: 1440 frames in 70.7s (~49 ms/frame), `audio.wav` 35.2s, stems (music, sfx) 100.9s. `renders/final.mp4` (101 MB) and `renders/share.mp4` (29 MB): H.264 1080x1920 yuv420p, 24 fps, 1440 frames, AAC 48 kHz stereo, 60.0s; both decode end to end with no errors. Review 2m20s.
- **Numbers:**
  - Cuts on grid: 1/1 (46.000s, f1104, err +0.0 f) PASS. Morphs: 13 at 4, 8, 12, 16, 22, 25, 29, 33, 37, 41, 44, 51, 56s, all on the 8th grid PASS.
  - Story arc 4/4 PASS: gift p90 -11.9 dB (loudest act; next -13.6), gift >= peak +1 dB (-11.9 vs -15.4), silence median -78.4 vs peak -18.1, gift 0.20 cuts/s.
  - Anchor 41.25-43.4s: 52/52 frames (100%), max offset 9 px PASS.
  - Text: 0 cut-off / overlap / safe-zone issues in 177 sampled frames; 7 issues in 46-51s allowed by `review.textIgnore` (the bubble storm) PASS.
  - Sound: loudest 100 ms window 46.0s (-9.6 dBFS) in the payoff act; 2.0s silence (<= -40 dBFS) before it; -15.0 LUFS integrated, LRA 7.8 LU, true peak -1.0 dBFS.
  - Flat frames: none. Dead beats: 0 stretches over 3s. Loop: last vs first diff 9.03 (returns to the opening image, changed; info only).

### Per-shot PASS table (contact sheets vs grammar/FRAME.md + styles/cut-paper/STYLE.md)

| Shot | Time | Beat | Result | Notes |
|---|---|---|---|---|
| 1 | 0-4s | 1950: Turing writes "Can machines think?" | PASS | Night study, cat, clock, lamp, steam: full-bleed world and background life. Write-on in sync with the caption; spark is born on the "?" at 2.5s. |
| 2 | 4-8s | 1956: Dartmouth, the field gets its name | PASS | Chalkboard write-on, three people from behind, spark takes the "AI" name tag. Secondary text ("summer 1956" pennant, "a summer research project") is small at phone size; decoration, not plot. |
| 3 | 8-12s | 1958: perceptron, knobs turn, "yes!" | PASS (minor) | The learning is acted out (dot grid fills toward the triangle). During the push-in (10.75-11.5s) the spark is cropped at the left edge and the year tag sits over the dials. |
| 4 | 12-16s | 1966: ELIZA talks back | PASS (minor) | Typed dialogue reads well on the sheet, but the monospace screen text is about 30 px at 1080 wide: hard to read on a phone. The spark's "!" reaction lands. |
| 5 | 16-22s | 1974: AI winter, the money runs out | PASS | Acted out, not labelled: snow, CLOSED lab, piggy bank, birds on a wire, spark in hat and scarf with the candle. Longest held framing (6s), kept alive by snowfall and idle motion. |
| 6 | 22-25s | 1986: try again, closer (backprop) | PASS (minor) | Candle carried over from 1974 (good continuity). "error, sent back" on the diagram is very small; crumpled paper balls land under the caption strip. |
| 7 | 25-29s | 1997: Deep Blue beats Kasparov | PASS (minor) | Strong push-in as the hand tips the king. The spark (the constant) is off screen for about 1.25s (26.75-28.0s) and cropped at the top on entry. |
| 8 | 29-33s | 2012: AlexNet, "cat!" | PASS (minor) | Clear idea (magnifier finds the cat among drawings). On the push-in (31-32s) the spark is cut by the left edge, outside x 60. |
| 9 | 33-37s | 2016: AlphaGo, move 37 | PASS (minor) | The stone drop and red ring read well; the stone becomes the spark at the morph. The mug overlaps a white stone in the corner, and the "move 37" tag is small. |
| 10 | 37-41s | 2017: Attention Is All You Need | PASS | Strings tie "it" to "animal": the paper's idea shown, not told. Clean cork-board composition, words readable. |
| 11 | 41-44s | 2020: GPT-3, bigger models, more text | PASS (minor) | Book towers and flying pages are energetic; spark at its largest. The "175 billion parameters" tag jitters and touches the caption strip at 42.5-43.5s. |
| 12 | 44-46s | Nov 30 2022: an empty box | PASS (minor) | Good quiet setup before the payoff (cursor, "hi" typed). The caption strip covers the lower half of the spark peeking in. |
| 13 | 46-51s | ChatGPT: millions say hi (the hard cut) | PASS | Hard cut on the beat to the sunburst; hands with phones, bubbles flood in (allowed overlap). Payoff reads instantly. |
| 14 | 51-56s | 2025: Claude Code, AI that does the work | PASS (minor) | The "Can machines think?" note framed on the wall is a good callback; cat, plant, sticky notes, ticks. Terminal text (Read/Edit/Bash, "12 passed") is about 25 px: unreadable on a phone. |
| 15 | 56-60s | today: "good question." | PASS | Returns to the opening study, changed: the spark (full rays) holds the pen and answers in its own colour. Bookends shot 1. |

Continuity: the year tag stays top-left in every era (1950, 1956, 1958, 1966, 1974, 1986, 1997, 2012, 2016, 2017, 2020, Nov 30 2022, 2025, today); the caption strip stays bottom-centre; the spark appears in every era and every morph passes through it or its prop (paper -> chalkboard, lamp -> lava lamp, paper -> snow, candle, note -> chessboard, cork board -> Go board, stone -> spark, spark -> screen). No flat or broken frames seen.

- **What the review caught:** no failures. Visual notes only (all minor, none blocking): the hero leaves or is cropped by the frame on three push-ins (shots 3, 7, 8); in-world screen text is too small for a phone (shots 4, 14; also 2, 6, 9 secondary labels); small overlaps of tags or the caption strip with other elements (shots 9, 11, 12).
- **Weakest shot:** 7 (1997). The push-in loses the spark for about 1.25s, the only stretch where the constant is out of frame. Fix: frame the push-in so the spark stays in the top-right inside the safe zone (or let it react at the board's edge as the king falls).
- **Not verified:** the score was measured, not listened to. Facts on screen were not re-checked against sources in this run.
- **Proposed rule (for craft.md, pending agreement):** on a push-in, keep the hero inside the phone-safe box (x 60-940, y 250-1500) for the whole move; in-world screen text that carries the idea should be at least ~40 px at 1080 wide.
