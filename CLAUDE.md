# Health Planner

## What this is
Single-file personal meal + fitness planner. One HTML file (~190KB),
all CSS, JS, and data inline. No build step, no dependencies.

## Architecture
- Storage key: wp_v7 (localStorage)
- buildTimeline(wk, dk) assembles all events for a day
- getDayTotals() sums kcal/protein from the live timeline
- renderMobileCards() for mobile, renderDesktopGrid() for desktop
- genMeals(exTypes) generates the week's meals

## How to check for JS errors after any change
python3 -c "
c=open('planner_app.html').read()
s=c.rfind('<script>');e=c.rfind('</script>')
open('/tmp/check.js','w').write('(function(){\n'+c[s+8:e]+'\n});\n')
" && node --check /tmp/check.js

## Critical rules
- ALWAYS run the check above after any JS change
- Never use Object.values() — use for-in loops instead
- Inline onclick in innerHTML does NOT work — use addEventListener
- All date operations use localDateStr() — never toISOString()
- Function declarations are hoisted so order in file doesn't matter

## User profile
Female, 37, 53kg goal 50kg. Pescatarian.
Default week: Mon/Thu/Sat=gym, Tue/Fri=pilates, Wed=recovery, Sun=rest
Wine nights: Fri + Sat
But this should be changable later for different profiles, and need and onboarding flow to best select these infos

## Design
- Fonts: Instrument Serif (headlines), Nunito (body), JetBrains Mono (numbers)
- Primary: #1a6b46 green, Background: #faf8f3 cream
- Card radius: 18px
