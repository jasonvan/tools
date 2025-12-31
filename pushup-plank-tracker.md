# Pushup & Plank Tracker

## Description
A fitness tracking web app for building strength through progressive pushup goals and daily plank holds. Track your daily workouts, maintain streaks, and progress toward 40 pushups by summer with automatic goal progression.

## Key Features

### Progressive Training
- **Pushup Goals**: Daily targets that increase linearly from your starting point to 40 pushups by summer (June 21, 2025)
- **Plank Progression**: Starting at 15 seconds, automatically increasing by 2 seconds each day
- **Smart Tracking**: Only your best plank time of the day is saved

### Workout Logging
- **Pushup Counter**: Large, easy-to-read counter with +1, +5, +10, and -1 buttons
- **Plank Timer**: Digital stopwatch with start/pause/resume/stop controls, displaying time to 0.1 second precision
- **Real-time Progress**: Visual progress bars showing advancement toward daily goals
- **Instant Save**: All data automatically saved to localStorage on every change

### Progress Dashboard
- **Streak Tracking**: Consecutive days with activity (any pushups OR plank hold counts)
- **7-Day Averages**: Rolling averages for both pushups and plank duration
- **Summer Countdown**: Days remaining until your target date
- **Overall Progress**: Visual indicator of average performance toward 40-pushup goal

### History View
- **14-Day Grid**: Responsive layout showing last two weeks of activity
- **Achievement Badges**: Visual indicators when daily goals are met
- **Rest Day Display**: Inactive days clearly marked with muted styling

## Prompt History

1. **Initial Request**: "I'd like you to make an app that allows me to track the number of pushups I do each day. As I'm starting the new year, I want to build up to 40 pushups by the summer. I'd also like to track planks starting at 15 seconds and going up by 2 seconds every day. This information should be stored in local storage, however you think is best. No React, everything should just be HTML, CSS, and vanilla JavaScript. The front-end design skill to come up with an interesting fitness-based design that is modern and clean. Orange, but not too much."

2. **Design Direction**: Athletic scoreboard aesthetic with bold Anton font for numbers, Outfit for body text, strategic orange accents, and smooth animations

3. **User Preferences Confirmed**:
   - Progressive daily pushup goals (not just tracking toward 40)
   - Daily total tracking only (not individual sets)
   - Best plank time per day (not multiple attempts)

## Technical Details

- **Framework**: Vanilla JavaScript (no dependencies)
- **Storage**: localStorage with key `'pushupPlankTracker'`
- **Data Structure**:
  ```javascript
  {
    settings: {
      pushupGoal: 40,
      summerDate: '2025-06-21',
      plankStartDuration: 15,
      plankIncrementPerDay: 2,
      startDate: null  // Set on first use
    },
    history: {
      '2025-01-01': { pushups: 25, plank: 30 },
      // ...date-keyed entries
    }
  }
  ```
- **Timer Precision**: 100ms update interval for smooth display
- **Goal Calculation**: Linear progression formula: `Math.ceil((goal × currentDay) / totalDays)`
- **Responsive Design**: Mobile-first with breakpoints at 640px (tablet) and 1024px (desktop)

## Design System

### Typography
- **Display/Numbers**: Anton (bold, athletic, high-impact)
- **Body Text**: Outfit (modern, clean, geometric)

### Color Palette
- **Primary Orange**: #ff6b35 (energy, action, progress)
- **Success Green**: #4caf50 (achievements, goals met)
- **Dark Text**: #1a1a1a (high contrast)
- **Light Background**: #f8f9fa (subtle, clean)

### Animations
- Entrance animations with staggered delays
- Number pop effect on counter updates
- Timer pulse during active plank
- Progress bar shimmer effect
- Smooth hover transitions

## Model Used
Claude Sonnet 4.5 (claude-sonnet-4-5-20250929)

## Privacy & Data
All workout data is stored locally in your browser using localStorage. No data is sent to any server. Clearing browser data will permanently delete your workout history.

## Known Limitations
- Data is browser-specific (not synced across devices)
- No export/import functionality (yet)
- No historical editing for dates older than present
- Summer date is hardcoded to June 21, 2025
- Timer may lose sub-second precision if browser tab is backgrounded for extended periods
- No offline PWA support

## Future Enhancements
- **Data Export/Import**: JSON download and upload for backup/transfer
- **Custom Goals**: User-configurable targets and dates
- **Additional Exercises**: Support for other bodyweight exercises (squats, sit-ups, etc.)
- **Charts & Graphs**: Visual progression charts using SVG or Canvas
- **Rest Day Planning**: Scheduled rest days that don't break streaks
- **Achievement System**: Badges and milestones for motivation
- **Dark Mode**: Theme toggle for different viewing preferences
- **PWA Support**: Offline functionality and mobile app installation
- **Historical Editing**: Ability to correct or update past entries
- **Notes Field**: Daily workout notes or how you felt
- **Social Sharing**: Share progress screenshots or achievements
