# Fat Loss Tracker

## Description
A daily habit tracking web app designed around the "Lose 2lbs Per Week" framework. Track essential daily habits for fat loss including nutrition targets, sleep optimization, and strength training with customizable options and streak tracking.

## Key Features

### Daily Habit Tracking
- **Nutrition Goals**: Calorie target (TDEE - 1000) and protein goal (bodyweight × 0.8)
- **Sleep Optimization**: No food 3hrs before bed, consistent sleep/wake time
- **Optional Habits**: Blue blockers after sunset and supplements (can be enabled/disabled in settings)
- **Strength Training**: Weekly goal tracking (3-4x per week) with progress display

### Customization
- **Settings Panel**: Toggle optional habits on/off (blue blockers, supplements)
- **Flexible Goals**: Adjust weekly lifting target between 3x or 4x per week
- **Smart Stats**: Completion percentages only count enabled habits

### Progress Tracking
- **Current Streak**: Consecutive days with all enabled daily habits completed (lifting excluded from daily requirement)
- **Weekly Lifting Count**: Track strength training sessions per week
- **7-Day Average**: Rolling completion percentage across the last week
- **Visual History**: 7-day grid showing completion percentage and perfect days

### Date Navigation
- **Time Travel**: Navigate backward through past days to view/edit habits
- **Today Lock**: Cannot navigate beyond current date
- **Auto-Update**: Automatically switches to current date when app regains focus

## Prompt History

1. **Initial Request**: "Create an HTML, CSS, and vanilla JS app based on the contents of this image [fat loss guide]. It should provide series of checkboxes that can be clicked to indicate if these things were accomplished for a given day. I should be able to use this track these things each day. Local storage should be used to track this over time. Some basic stats should be tracked with this information. Note, not all things are required to be completed everyday like lifting (3-4 times a week)"

2. **User Preferences Confirmed**:
   - Filename: `fat-loss-tracker.html`
   - Lifting behavior: Allow toggle off (can uncheck if marked by mistake)
   - Color scheme: Green (health/fitness) → Later changed to orange/dark orange
   - Optional habits: Blue blockers and supplements should be optional and not affect stats unless enabled

3. **Design Iteration**: Initial green design was too similar to pushup-plank-tracker, so frontend-design skill was used to create a distinctive neo-brutalist editorial aesthetic with bold borders, offset shadows, and Fraunces serif typography

4. **Color Refinement**: User requested change from green/terracotta to orange/dark orange color scheme to better match their preference

5. **SVG Enhancement**: Replaced emoji gear icon with custom SVG settings icon featuring bold strokes and rotation animation

## Technical Details

- **Framework**: Vanilla JavaScript (no dependencies)
- **Storage**: localStorage with key `'fatLossTracker'`
- **Data Structure**:
  ```javascript
  {
    settings: {
      weeklyLiftingGoal: 4,       // 3 or 4
      trackBlueBlockers: false,   // optional habit toggle
      trackSupplements: false     // optional habit toggle
    },
    currentDate: null,
    history: {
      '2025-01-02': {
        calories: true,
        protein: true,
        noLateFood: true,
        consistentSleep: false,
        blueBlockers: false,     // only counts if trackBlueBlockers enabled
        supplements: false,      // only counts if trackSupplements enabled
        lifted: true
      }
      // ...date-keyed entries
    }
  }
  ```
- **Streak Calculation**: Only counts consecutive days where all *enabled* daily habits are completed (lifting not required daily)
- **Week Definition**: Sunday to Saturday (standard week start)
- **Responsive Design**: Mobile-first with breakpoints at 768px, reduced shadow sizes on mobile

## Design System

### Typography
- **Display**: Fraunces (variable serif, bold and characterful, 900 weight for headers)
- **Body**: Sora (modern geometric sans-serif, clean and readable)

### Color Palette
- **Primary Orange**: #ff6b35 (energetic, motivating)
- **Dark Orange**: #d94a1a (shadows, depth)
- **Light Orange**: #ff8c61 (subtle highlights)
- **Accent Orange**: #ff4500 (vibrant interactions)
- **Cream**: #faf7f0 (warm background)
- **Charcoal**: #2d3436 (strong borders and text)
- **Warm White**: #fffef9 (card backgrounds)

### Neo-Brutalist Design Elements
- **Bold Borders**: 3-4px solid charcoal borders on all major elements
- **Offset Shadows**: Hard drop shadows (8px offset) in contrasting orange shades
- **No Border Radius**: Sharp, geometric edges throughout (except circular elements)
- **Staggered Animations**: Sequential fade-in effects with varying delays
- **Bounce Easing**: Satisfying spring animations (`cubic-bezier(0.68, -0.55, 0.265, 1.55)`)

### Animations
- Page load: Staggered fade-in with `animation-delay` (0.2s - 0.8s)
- Header gradient: Diagonal clip-path slide-down
- Checkboxes: 360° rotation when checked with bounce easing
- Hover states: Card lift with shadow transitions
- Settings modal: Bounce-in entrance with scale effect
- SVG icon: 90° rotation on hover

### Interactions
- **Habit Items**: Transform to orange background when checked, text turns white
- **Checkboxes**: Square shape that rotates and fills with accent orange on check
- **Day Cards**: Hover lift effect, perfect days highlighted in primary orange
- **Buttons**: Scale and color transitions on hover
- **Modal Close**: Rotates 90° on hover

## Model Used
Claude Opus 4.5 (claude-opus-4-5-20251101) - for initial implementation
Claude Sonnet 4.5 (claude-sonnet-4-5-20250929) - for refinements and enhancements

## Privacy & Data
All habit tracking data is stored locally in your browser using localStorage. No data is sent to any server. Clearing browser data will permanently delete your tracking history.

## Known Limitations
- Data is browser-specific (not synced across devices)
- No export/import functionality
- Cannot edit future dates beyond today
- Week start is fixed to Sunday (not customizable)
- Blue blockers and supplements are hidden when disabled (no historical record of when they were tracked)
- No undo functionality for accidental toggles (though you can toggle back)
- Streak calculation does not account for rest days or planned breaks

## Future Enhancements
- **Data Portability**: JSON export/import for backup and device transfer
- **Historical Analytics**: Charts showing trends over weeks/months
- **Customizable Habits**: Add/remove habits beyond the default set
- **Flexible Week Start**: Choose Monday or Sunday as week start
- **Rest Day Planning**: Mark planned rest days that don't break streaks
- **Notes Field**: Daily notes about how you felt or what you ate
- **Notifications**: Optional reminders for habits (via browser notifications)
- **Dark Mode**: Theme toggle for different preferences
- **Habit Templates**: Pre-configured habit sets for different goals
- **Progress Photos**: Upload and track visual progress alongside habits
- **Weight Tracking**: Optional weight logging with chart visualization
- **Measurement Tracking**: Track body measurements over time
