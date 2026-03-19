# Chinese Flashcards

A spaced repetition flashcard app for learning the most common traditional Chinese characters. Study smarter with an adaptive SM-2 algorithm that schedules reviews at the optimal time.

## Key Features

- **Spaced Repetition System (SRS)**: SM-2 algorithm adapts interval scheduling to your performance
- **500 Traditional Characters**: The most common characters covering approximately HSK 1–5 vocabulary
- **4-Button Rating**: Again / Hard / Good / Easy with live interval previews on each button
- **3D Card Flip**: CSS perspective flip animation revealing pinyin and meaning
- **Daily Limits**: Configurable new cards per day (default 20) to prevent overwhelm
- **Streak Tracking**: Consecutive study days with longest-streak record
- **Session Resume**: Refreshing mid-session picks up where you left off
- **Keyboard Shortcuts**: Space to flip, 1–4 to rate, Escape to go back
- **Settings**: Toggle pinyin-on-front, adjust daily new card limit, export/import data, reset progress
- **Fully Offline**: No external dependencies except Google Fonts

## How to Use

1. **Dashboard**: Shows cards due, total learned, and current streak. Click "開始學習 Begin Study".
2. **Review**: See the Chinese character. Press Space or click "顯示答案 Show Answer" to flip.
3. **Rate**: Choose how well you recalled the character:
   - **Again** — Complete blackout; card comes back in 1 day
   - **Hard** — Recalled with difficulty; interval increases slightly
   - **Good** — Recalled with effort; standard interval increase
   - **Easy** — Effortless recall; larger interval increase
4. **Summary**: After finishing, see your session results and what's due next.

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` or `Enter` | Show answer / rate Good |
| `1` | Rate Again |
| `2` | Rate Hard |
| `3` | Rate Good |
| `4` | Rate Easy |
| `Escape` | Close settings / back to dashboard |

## Technical Details

**localStorage Key**: `chineseFlashcards`

**Data Structure**:
```json
{
  "version": 1,
  "settings": { "newCardsPerDay": 20, "showPinyin": true },
  "cards": {
    "0": { "interval": 4, "easeFactor": 2.5, "repetitions": 2, "lapses": 0, "dueDate": "2026-03-20", "lastReviewed": "2026-03-18" }
  },
  "stats": { "2026-03-18": { "reviewed": 45, "newIntroduced": 12, "again": 3, "hard": 8, "good": 22, "easy": 12 } },
  "meta": { "streakStart": "2026-03-01", "longestStreak": 18, "totalReviewed": 850, "totalLearned": 112, "lastStudyDate": "2026-03-18" },
  "session": { "date": "2026-03-18", "newCardsIntroducedToday": 12, "queue": [], "currentIndex": 0, "sessionReviewed": 0, "sessionCorrect": 0 }
}
```

**Card state**: Cards absent from `cards` object are treated as new (not yet introduced). Only introduced cards are stored, keeping localStorage lean.

**SRS Algorithm**: SM-2 variant
- Ease factor range: 1.3 – 9.9 (initialized at 2.5)
- Again: interval → 1 day, ease − 0.2, repetitions reset, lapses +1
- Hard: interval × 1.2 (min 1), ease − 0.15
- Good: 1d → 6d → interval × easeFactor progression
- Easy: 4d → 10d → interval × easeFactor × 1.3, ease + 0.15

**Character Data**: Array-of-arrays format `[traditional_char, pinyin_tone_marks, english_meaning]`. Traditional characters throughout; pinyin uses Unicode tone marks (e.g. `nǐ` not `ni3`).

## Design System

**Aesthetic**: "Ink & Vermillion" — East Asian scholarly aesthetic. Rice paper warmth, ink-black typography, vermillion accents. Restrained and functional with deliberate calligraphic moments.

**Fonts**:
- `Ma Shan Zheng` — Authentic Chinese calligraphy style; used exclusively for large character display
- `Lora` — Warm readable serif for all UI text

**Colors**:
- Rice paper background: `#f5f0e8`
- Ink black: `#1a1410`
- Vermillion accent: `#c0392b`
- Gold accent: `#b8860b`
- Answer buttons: red / amber / green / blue (distinct from palette)

**Animations**:
- Staggered `fadeInUp` entrance on dashboard cards
- 3D CSS perspective card flip (0.5s ease-in-out)
- Settings panel slides in from right (0.35s)
- Rice paper grain texture via `body::before` repeating radial-gradient

## Prompt History

**Model**: Claude Sonnet 4.6

### Session 1 — Initial Build
Prompted to build a spaced repetition Chinese flashcard app for traditional characters following the single-file architecture in the tools repository. Planning phase involved research into:
- Existing tool patterns (fat-loss-tracker.html, pushup-plank-tracker.html)
- SM-2 SRS algorithm design
- Traditional Chinese character frequency lists
- "Ink & Vermillion" aesthetic concept

Built complete app including: SM-2 SRS algorithm, 500 traditional character entries, 3D card flip animation, dashboard with streaks and activity grid, session management with resume capability, settings panel with export/import.

## Known Limitations

- Character set covers ~500 of the most common traditional Chinese characters (not 2000 as originally planned — quality over quantity for initial release)
- No audio pronunciation (browser TTS could be added via Web Speech API)
- No stroke order diagrams
- Simplified characters are not included (traditional only)
- No multi-character word compounds — single characters only

## Future Enhancements

- Expand to 2000 characters covering full HSK 6 range
- Add audio via Web Speech API (Mandarin TTS)
- Stroke order animation using HanziWriter
- Example sentences for each character
- Dark mode (rice-paper-dark palette)
- Export to Anki format
- Simplified/Traditional toggle
- Filter by HSK level
