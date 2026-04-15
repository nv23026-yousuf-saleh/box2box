# BOX2BOX-STYLE REBUILD GAME  
DEVELOPER PROMPT

Rewritten product brief for a 3-player football rebuild website
based on the uploaded draft, the provided subtitle transcript, and current football data requirements.

Purpose: give a developer a single, implementation-ready brief that matches the Box2Box rebuild flow more closely,
while using original site branding and current real-world football data.

Important note: this brief aims to mirror the gameplay structure and pacing of Box2Box-style rebuild videos, but the website should use its own product identity, UI, and brand assets rather than copying another creator’s visual branding.



1. Executive Summary

This website is a real-time, 3-player football rebuild game. All three players rebuild the same club at the same time under the same opening budget, but each player makes private decisions and reveals the finished build at the end.

The gameplay must follow the actual rebuild rhythm more closely than the old draft: manager decision first, then player-by-player keep-or-sell choices across the starting XI and key squad positions, then a replacement market with exactly three surfaced options plus a bench route, plus competitive bidding when two or more players want the same option.

The old draft is too static in some areas. The new build must remove the untouchables concept, remove overly rigid squad rules that are not central to the video format, and replace them with dynamic constraints driven by management cards, finance cards, realistic transfer values, available budget, and the replacement pool.

The core feeling must be debate-heavy, simple to navigate, quick to understand, and highly replayable. A player should be able to jump into a lobby, understand the club crisis, move through manager and squad decisions, and finish a full rebuild without the interface feeling heavy or complicated.

2. What Changed from the Uploaded Draft



3. Non-Negotiable Product Principles

• Exactly 3 players per match. Not 2. Not 4. The game is built for a three-way rebuild showdown.

• Real football only. Real clubs, real players, real managers, real positions, real contracts, and realistic values.

• Up-to-date data. The site must reflect the current football world at the time the data was last refreshed.

• Easy navigation. A user should always know: current club, current budget, current card effects, current player being decided, current available options, and remaining incomplete positions.

• Replayability over repetition. The same rebuild should not present the same options in the same order every time.

• Strong realism guardrails. The game must stop absurd outcomes such as elite superstars moving to unsuitable clubs for bargain fees without the right context.

• Fast drama. The interface should feel more like a guided football show format than a complicated management simulator.

4. Core Gameplay Loop (Match the Show Format)

4.1 Lobby - One host creates a lobby and two other players join. The host selects a club scenario or a custom rebuild scenario.

4.2 Club crisis intro - Before decisions begin, all players see a short crisis summary explaining why the club needs a rebuild. This should be concise, dramatic, and rooted in the present football reality.

4.3 Shared opening budget - All three players get the same starting budget. Budget size should be configurable by the host or scenario.

4.4 Management card draw - At the start, every player receives one management card. Cards can force sales, require expensive signings, force league-specific signings, or leave a player unrestricted.

4.5 Manager decision - Each player first decides whether to keep the current manager or sell/fire him and enter the manager market.

4.6 Manager market - If a manager is sold/fired, the player sees exactly three manager choices plus their prices and can bid if another player wants the same manager.

4.7 Player-by-player rebuild loop - The website then moves through a fixed order of key positions/players. For each one, the player is told the current player and sale price, then chooses Keep or Sell.

4.8 Replacement market - If the player sells, the game opens a replacement panel with exactly three surfaced options: bottom option, second option, and top option. The user may also choose a bench option instead.

4.9 Bidding - If two or more players choose the same surfaced option, live bidding begins. The highest valid bid wins. Losing players must immediately choose another surfaced option or bench option.

4.10 Finance cards during the build - At defined checkpoints, each player receives finance cards that add or remove money and change the risk profile of the rebuild.

4.11 Final XI review - Once all required decisions are done, the player reviews their lineup, manager, spend, and remaining budget.

4.12 Reveal and voting - All three finished rebuilds are revealed one by one, followed by comparison, voting, and winner selection.

5. The Real Decision Pattern the UI Must Follow

Every position decision should feel like this exact rhythm: current player shown -> host/system states sale value -> player chooses Keep or Sell -> if Sell, replacement market opens with 3 surfaced options + bench -> if there is a collision, live auction starts -> budget updates immediately -> the game advances to the next decision.

The biggest design rule: do not dump the full database on the user as the main action. The main action is the guided keep-or-sell flow. Search and browse exist as support, not as the default experience.

6. Football Data Scope

The database must include players from all clubs in the Top 5 leagues so the surfaced options can pull from a broad and realistic pool: Premier League and LaLiga each have 20 clubs in the 2025-26 season, while Bundesliga and Ligue 1 each have 18; official league pages also provide current club lists for those competitions. The product can use official league sites and football-data providers to refresh club and squad information. 

The recommendation is to keep two layers of data: a complete underlying database covering the full Top 5 leagues, and a surfaced recommendation engine that strongly favors top clubs, high-profile talents, realistic stepping-stone clubs, and players whose profile fits the current rebuild.

Because the user explicitly wants many players from all Top 5 leagues and realistic price options, the surfaced market must not feel like a tiny handpicked list. The generator should be able to draw from hundreds of relevant options while still only showing three at a time.

For replayability, replacement options must be generated from weighted pools instead of fixed lists. A Real Madrid rebuild should usually surface elite or near-elite solutions, but not always the exact same three names.

7. Required Data Model

Player entity

• Full name, common name, nationality, date of birth, age, dominant foot, height, primary position, secondary positions

• Current club, league, contract expiry, current squad role (starter / rotation / prospect / depth)

• Current estimated market value in EUR

• Realism tags: homegrown, captaincy, injury risk, resale potential, wages band, prestige tier, adaptability, rivalry sensitivity

• Club-fit tags: can move up, lateral move, unlikely move, almost impossible move, loan candidate, bench-option candidate

Club entity

• Club name, league, crest asset, prestige tier, financial power tier, tactical identity tags, current manager, current squad snapshot, current season context

Manager entity

• Full name, nationality, status (employed / free / legend-return / caretaker), tactical style, formation tendencies, salary/hiring cost, difficulty score, realism tags for club fit

Scenario entity

• Club, crisis summary, opening budget range, fixed decision order, special pool weights, allowed/blocked manager logic, card deck version

8. Realism and Pricing Engine

Do not hard-code simple 70%-130% bands as the only realism test. Keep pricing bands, but add transfer realism scoring. The game should understand that some deals are realistic because of age, contract, role, league jump, and club pull, while others are unrealistic even if the fee looks mathematically valid.

Use a realistic transfer value engine with a base asking value, a realism multiplier, and a competition multiplier. Example drivers: age, contract length, squad importance, club wealth, league prestige, destination prestige, rivalry, player status, and whether the move is upward, lateral, or downward.

Replacement prices can be host-assigned for surfaced options, but they must still come from a pricing engine that keeps them believable. The transcript shows debate around prices, but the prices are still intended to feel like football logic rather than random numbers.

A move like Mbappe out and a weak low-ceiling replacement in should be blocked or given an extreme realism penalty. Equally, a small club should not casually sign a galactico-level player without a major budget and prestige explanation.

9. Replacement Market Rules

• Exactly three surfaced options appear when a sold player is being replaced.

• The surfaced options should be ranked and labeled in the UI as bottom option, middle option, and top option.

• A fourth route called Bench Option must always exist when appropriate. This can mean promoting an internal player, moving an existing squad player into the role, or using a lower-profile fallback candidate.

• Surfaced options must be position-aware and scenario-aware. Selling a right winger should mainly produce right-wing or role-compatible attacking replacements, not random stars from unrelated roles.

• Option strength should scale with the club. Elite clubs should see stronger ceilings. Mid-level clubs should see more development and value options.

• Option generation should be varied across matches. The same club rebuild must not constantly output the same trio.

• If a player cannot afford a desired option after previous decisions or finance-card damage, the UI must gray it out or show why it is invalid.

10. Auction and Collision Logic

If two or three players select the same surfaced option, the game enters a quick live auction. This is essential and should not be optional because it is one of the best tension mechanics in the format.

The auction should be simple: current price, minimum next increment, valid bid button or input, countdown, and live budget validation.

Once a winner is confirmed, the losing players immediately return to the same replacement panel with the won player removed. They can then choose another surfaced option or bench option.

The site should support both automatic minimum bid increments and manual overbids.

11. Management Cards and Finance Cards

Cards are not a side feature. They are part of the show identity and should be implemented as core gameplay.



Card design rules: cards must be scenario-themed, readable in one glance, and applied immediately. Active card effects must stay pinned in the interface so a player cannot forget a restriction.

12. Final Build Validity Rules

• Every player must finish with one manager and one coherent starting XI.

• The final XI must be positionally sensible for the chosen formation.

• The game should allow smart flexibility, but it should reject lineups that are clearly broken or impossible.

• There should be at least a lightweight bench and backup structure, but do not overcomplicate the game with heavy squad-registration admin.

• Budget cannot go below zero unless the scenario explicitly allows debt and marks it as a penalty.

13. Reveal, Voting, and Results

After all three builds are complete, reveal them one by one in random order.

Each reveal should show: manager decision, sold players with prices, signed players with prices, card effects, remaining budget, and final XI on a pitch.

After all reveals, show a side-by-side comparison. Keep this visual and easy to scan.

Each user then votes for the best rebuild, but cannot vote for themselves.

Use secondary algorithmic scoring only as a tiebreak or side statistic. The main winner should still feel community-driven, just like the show format.

14. Replayability Rules So Rebuilds Do Not Repeat

• Use weighted randomness with protected variety. Do not repeat the exact same surfaced player in the same club-position scenario too often.

• Track prior surfaced options within the session and de-prioritize repeats.

• Use multiple option archetypes for every sale: safe option, upside option, star option, value option, internal/bench option, stylistic fit option, wildcard option.

• Make top clubs in each Top 5 league heavily represented in candidate pools, but still allow strong fits from non-elite clubs.

• Rotate scenario decks, manager pools, and card decks so two Real Madrid rebuilds can feel meaningfully different.

• Allow a season-data refresh to naturally shift player pools over time.

15. UX and Navigation Requirements

• Clean, fast dark-theme layout with strong contrast and large readable numbers.

• Persistent top bar: club, current budget, current manager, active cards, decisions remaining.

• Main center panel: current player or current decision stage.

• Right-side or lower drawer: surfaced market options and bench route.

• One-click keep/sell choice. One-click choose option. Simple auction modal. Minimal clutter.

• Mobile responsiveness is required, but desktop should be the main reference experience.

• The site should feel guided and cinematic, not like a spreadsheet.

16. Technical Build Recommendation

Frontend: Next.js or React with a clear match-state architecture.

Realtime: WebSockets or Socket.io for auctions, synchronized reveals, and live votes.

Backend: Node.js, NestJS, or equivalent service layer.

Database: PostgreSQL for structured football data; Redis for live lobby state.

Data ingestion: football-data.org and/or API-Football for competition and team data, combined with a curated valuation layer for realism and surfaced pricing.

Admin tools: internal dashboard to refresh squads, adjust valuation rules, tune option weights, edit scenario texts, and manage card decks.

17. Final Developer Prompt

Build a web-based, 3-player football rebuild game that closely matches the guided Box2Box-style rebuild format rather than a generic transfer simulator.



The website must work like this:

- Exactly 3 players join the same lobby and rebuild the same club at the same time.

- The host picks a club scenario and all 3 players receive the same opening budget.

- Each player receives a management card at the start.

- Each player first decides whether to keep the current manager or fire/sell him and enter the manager market.

- If they enter the manager market, they see exactly 3 manager options and may need to bid if another player wants the same manager.

- The game then moves through a fixed sequence of important players/positions.

- For each one, the user is shown the current player and sale price and must choose Keep or Sell.

- If the user sells, the website must show exactly 3 surfaced replacements: bottom option, middle option, and top option, plus a bench option.

- If multiple users choose the same replacement, the game launches a live auction and the highest valid bid wins.

- Finance cards must appear during the build and can add or remove money.

- All money changes, restrictions, and decisions must be reflected live in the UI.

- At the end, each user submits a final manager and coherent starting XI.

- Then the site reveals each rebuild, compares them side by side, and lets the players vote for the best one.



Critical realism requirements:

- Remove the untouchables system completely.

- Use real, current football data only.

- Include players from all clubs across the Top 5 leagues, with strong weighting toward top clubs and realistic replacements.

- Prices must be realistic and context-aware, not random.

- The site must block absurd transfers and absurd fees.

- It must not output the same rebuild choices every time.

- A Real Madrid rebuild should not always surface the same signings in the same order.

- If a user sells a superstar, the replacements must still make football sense for the club and scenario.

- The surfaced options should feel curated, but the underlying database should be broad and deep.



Product feel requirements:

- Very easy to navigate.

- Fast, guided, and cinematic.

- Focus on debate, auctions, money pressure, and realistic team-building.

- The main interaction is the guided keep-or-sell loop, not a giant open transfer list.

- Use original branding for the website product itself; do not copy another channel’s visual identity.



Data and logic requirements:

- Maintain a full Top 5 league player database.

- Maintain a manager database with employed, available, and special-return candidates where realistic.

- Build a weighted option-generation engine so surfaced choices vary by club, position, price range, tactical fit, prestige, and replay history.

- Support scenario-specific crisis text, card decks, and pool weighting.

- Include an admin layer for data refresh, option tuning, and scenario editing.



This website should feel like a polished digital version of the three-person rebuild show format: current, realistic, competitive, replayable, and simple to use.

18. Sources Used for This Rewrite

• Uploaded website prompt draft

• Uploaded subtitle transcript, which shows the management-card -> manager-decision -> keep/sell -> 3 options + bench -> bidding -> finance-card loop

• Official league pages and current data-provider documentation used to keep the Top 5 league and data-source recommendations current
