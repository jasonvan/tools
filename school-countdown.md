# School Year Countdown

A chalkboard-themed countdown app built for a third-grade teacher at Taipei American School (TAS) in Taipei, Taiwan. Displays days/hours/minutes/seconds remaining until the last day of school, with a progress bar through the school year and localStorage-tracked visit history.

## Key Features

- **Live countdown** — days, hours, minutes, seconds ticking in real time
- **Milestone messages** — contextual encouragement as the end of year approaches
- **School year progress bar** — visual percentage of year completed (Aug 25 → Jun 5)
- **Visit history** — tracks first visit, last visit, and total times opened via localStorage
- **Editable target date** — settings panel lets the teacher update the last day if the calendar changes
- **Chalkboard aesthetic** — dark green board texture, Permanent Marker + Patrick Hand fonts, floating emoji doodles

## Prompt History

1. User requested a school countdown app for a TAS Grade 3 teacher with localStorage visit tracking
2. Searched for TAS SY25-26 academic calendar; end date inferred as June 5, 2026 (Friday before Summer Academy starts June 8)
3. Designed and implemented the single-file app with chalkboard theme

## Technical Details

**Libraries**: Google Fonts only (Permanent Marker, Patrick Hand)

**localStorage key**: `schoolCountdown`

**State structure**:
```json
{
  "firstVisit": "2026-04-12",
  "lastVisit": "2026-04-12",
  "visitCount": 1,
  "targetDate": "2026-06-05",
  "schoolYearStart": "2025-08-25"
}
```

**Countdown logic**: `setInterval` every 1000ms; calculates remaining seconds to target date at 23:59:59 local time.

**Progress bar**: `(now - schoolYearStart) / (targetDate - schoolYearStart) × 100%`

## Design System

- **Theme**: Retro chalkboard classroom
- **Background**: `#2C3E2D` (dark chalkboard green) with repeating-linear-gradient texture lines
- **Colors**: Chalk white `#F5F0E0`, Sunny yellow `#FFD700`, Sky blue `#87CEEB`, Apple red `#E74C3C`, Green `#5CB85C`
- **Fonts**: Permanent Marker (display/numbers), Patrick Hand (body/labels)
- **Animations**: fadeInDown header, staggered fadeInUp sections, bobble apple, pulse seconds, floating doodles

## Model

Claude Sonnet 4.6

## Known Limitations

- Target date defaults to June 5, 2026 — inferred from Summer Academy start date (June 8). Verify against the official TAS academic calendar and adjust via the settings panel if needed.
- `schoolYearStart` (August 25, 2025) is hardcoded; editing it requires the settings panel date change or localStorage manipulation.

## Future Enhancements

- Add a "weeks remaining" display mode toggle
- Confetti animation when school is out
- Teacher-configurable school year start date in settings
