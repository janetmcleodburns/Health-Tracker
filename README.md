Daily Health Tracker
A GitHub Pages habit tracker with Supabase sync.
Setup
1. Create Supabase table
In your Supabase dashboard → SQL Editor, run:
```sql
create table health_tracker (
  date text primary key,
  data jsonb not null,
  updated_at timestamp default now()
);

alter table health_tracker enable row level security;

create policy "Allow all" on health_tracker
  for all using (true) with check (true);
```
2. Deploy to GitHub Pages
Create a new repo (e.g. `Health-Tracker`)
Upload `index.html`
Go to Settings → Pages → Source: main branch / root
Your app will be live at `https://janetmcleodburns.github.io/Health-Tracker/`
3. Connect Supabase
When you first open the app, enter your:
Supabase URL: found in Project Settings → API
Anon key: found in Project Settings → API
These are saved to localStorage so you only enter them once per device.
Optional: Hardcode credentials
Replace these lines in `index.html`:
```js
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_KEY = 'YOUR_SUPABASE_ANON_KEY';
```
What's tracked
Mind & Spirit: Meditation (20 min), Journaling (10 min)  
Exercise: Resistance training (resistance days), Swim (daily)  
Movement: Walk, Recumbent bike  
Nutrition: IF window (first + last meal time), Water intake  
Work: Morning deep work, Midday comms, Evening work block
Features
Toggle between Resistance and Active Recovery days
Notes field on every habit
IF window calculator (shows fasted hours)
Streak badges (🔥 appear at 3+ days)
Progress tab: 7-day stats, weekly grid, streak leaderboard
Navigate past days to backfill
Auto-saves to Supabase on change
