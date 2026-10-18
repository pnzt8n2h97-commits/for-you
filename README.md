# Digital Releases for Stremio

A Stremio add-on that lists movies you can rent or buy right now, plus new shows you can stream, with a genre filter on every catalog. It runs on Vercel's free plan and has no dependencies.

## Catalogs

- **Digitally Available:** movies with a digital release in your region.
- **New Shows Streaming:** shows that premiered recently and are on a streaming or rental service in your region.
- **New Episodes This Week:** shows with an episode airing in the last 7 days.

Movies and TV shows can each be switched off on the install page. By default you get the general install: every genre, with a genre dropdown inside Stremio.

**Pick genres:** tap as many genres as you like on the install page. With genres picked, the install only includes those genres. Shows and movies are filtered to the genres that exist for each type (Horror is movies-only, Kids is shows-only, and so on).

**Layout:** choose how the picks appear in Stremio.
- **One combined row (default):** each catalog combines the picked genres into one row, such as "Comedy + Horror: Digitally Available".
- **Separate row per genre:** every picked genre gets its own rows, such as "Comedy: Digitally Available" and "Horror: Digitally Available". With nothing picked, this makes a row for every genre, which is a lot of rows, so it's best with a few genres picked.

Each choice produces its own add-on ID and name, so you can install again with different genres or layouts and they stack side by side. Older single-genre links still work and come back as one pick.

To install just one genre, tap it on the install page (for example Comedy). That install gets its own catalogs already filtered to the genre. Each setup has its own add-on ID, so you can install again with a different genre and they stack side by side. Some genres exist only for movies (Horror, Romance, Thriller, History, Music) or only for shows (Kids, Reality), and those installs include only the matching catalogs.

## Turkish TV

The install page has a third tab, **Turkish TV**, with its own add-on. It has three separate rows, each one picked or left out with the chips:

- **Turkish Movies:** Turkish-language films made in Turkey.
- **Turkish Series:** Turkish-language dramas (Drama genre, with a minimum vote count so obscure titles don't dominate).
- **Turkish Reality:** Turkish reality shows, topped up with recent Turkish reality from TVMaze's schedule because TMDB alone has few.

**Layout:** choose **separate rows** (the default, one per pick) or **one combined row**. Stremio rows hold a single kind of thing, so a combined layout makes one row for movies and one for series, with reality grouped into series.

Turkish TV is always about Turkey, so the region setting doesn't apply. Turkish Dramas used to be a row on Trash TV; it now lives here.

## Trash TV

The install page has a second tab, **Trash TV**. It installs its own separate add-on (not a genre of the main one) with eight rows of trashy TV:

- **Bravo Universe:** popular shows from franchises like Real Housewives, Below Deck, Vanderpump Rules, Summer House and Southern Charm.
- **Bravo Universe: On Now:** shows that aired on Bravo in the last 7 days (from TVMaze's real TV schedule), plus those franchises airing elsewhere, such as on streaming.
- **Reality: On Now:** reality shows from your chosen region that aired in the last 7 days, from TVMaze's schedule. If TVMaze is slow or down, both On Now rows fall back to TMDB (episodes in the last 14 days).
- **Dating and Love Shows:** Love Island, Love Is Blind, Too Hot to Handle, The Bachelor, Temptation Island, Married at First Sight and more.
- **Reality Drama:** Jersey Shore, Teen Mom, Dance Moms, Love & Hip Hop, Basketball Wives, The Kardashians, Catfish and more.
- **Daytime Chaos:** Jerry Springer, Maury, Dr. Phil, Judge Judy, Divorce Court and more.
- **Train Wrecks:** My 600-lb Life, Hoarders, Dr. Pimple Popper, Sister Wives, Toddlers & Tiaras and more.
- **Telenovelas:** Spanish-language soaps.

**Region:** pick a region on the Trash TV tab (for example Turkey, the UK or Australia) and the On Now rows show what's actually airing there, using TVMaze's schedules by country. The default is the US.

**Smarter rows:** the On Now rows are topped up with recent and popular shows when a quiet part of the season would leave them thin. The franchise rows (Bravo Universe, Dating and Love Shows, Reality Drama, Daytime Chaos, Train Wrecks) and the On Now rows are sorted by a guilty-pleasure score: shows that are hugely watched but not well rated come first. Turkish Dramas and Telenovelas stay in plain popularity order.

Most rows are matched by show name (see `FRANCHISES` and `GROUPS` in `api/index.js`), so you can add or remove names there. Install every row together (the default), or tap any number of rows to pick them. Choose **one combined row** (the picks are mixed into a single row, taking shows from each in turn) or **separate rows** (the default, one per pick). Each choice gets its own name (for example "Trash TV: Dating and Love Shows + Turkish Dramas"), so you can stack several side by side. It can also be installed alongside the Releases add-on.

## Documentaries

Eight rows in all. (TMDB has no separate nature, science or sport genres, so those styles aren't offered; they could be added through TMDB keywords if you want them.)

The install page has a fourth tab, **Documentaries**, with its own add-on and four separate rows, each picked or left out with the chips:

- **Documentary Movies:** documentary films, with a minimum vote count so obscure titles don't dominate.
- **Documentary Series:** documentary series.
- **True Crime Series:** series tagged both Crime and Documentary (TMDB's "both genres" filter).
- **True Crime Movies:** films tagged both Crime and Documentary.
- **History Documentaries:** documentary films tagged History.
- **Music Documentaries:** documentary films tagged Music.
- **War Documentaries:** documentary films tagged War.
- **War and Politics Documentary Series:** documentary series tagged War and Politics.

**Layout:** choose **separate rows** (the default) or **one combined row**. As on Turkish TV, a combined layout makes one movies row and one series row, so documentary and true crime titles are mixed within each type.

Documentaries don't depend on region, so the region setting is hidden on this tab.

## Everything

The **Everything** tab installs every row from Releases, Trash TV, Turkish TV and Documentaries as one add-on. Tick the rows you want and use the Top, Bottom and arrow buttons, or drag a row by its handle (⋮⋮), to set the order Stremio shows them in. Unticked rows are left out, and **Reset everything** puts the whole page back to its defaults: the Everything order and ticks, plus every tab's picks, layouts and switches. Because it's one add-on, it's the simplest way to get everything at once, but it's a lot of rows, so untick what you don't need.

**It follows each tab's layout.** If a tab is set to one combined row, Everything shows that tab's combined row(s) in its place, and the separate rows for that tab disappear from the list. If a tab is set to separate rows, its separate rows appear as usual. Combined rows only show for the types you picked on that tab. Each tab's picks are carried into the Everything install too.

Releases uses its three rows in either layout, since its combined layout is those same rows. Its separate-per-genre layout (one row per genre) isn't brought into Everything, because that would be dozens of rows.

## For You

The **For You** tab installs its own add-on with two rows, **For You: Movies** and **For You: Shows**, picked for one person. Tap a row chip to install just one of them.

**How it picks:** the add-on gathers titles that are actually available (new digital releases, new and airing shows in your region, and TMDB's weekly trending lists). Then an AI re-orders them for you. The AI can only re-order that list, so it can't invent titles, and anything it returns that wasn't on the list is ignored. Titles the AI didn't pick come after its picks, so the rows stay full.

**Choose an AI (optional), using your own key:**

| AI | Cost | Default model | Get a key |
| --- | --- | --- | --- |
| Gemini | Free tier available | `gemini-3.5-flash-lite` | [aistudio.google.com](https://aistudio.google.com/apikey) |
| Groq | Free tier available | `llama-3.3-70b-versatile` | [console.groq.com](https://console.groq.com/keys) |
| OpenRouter | Some free models (names end in `:free`) | Your OpenRouter default | [openrouter.ai](https://openrouter.ai/keys) |
| Claude | Paid per use | `claude-haiku-5-5` (cheapest) | [platform.claude.com](https://platform.claude.com) |

You can type a different model name. Free tiers and model names change often, so check each provider's page. Google may use free-tier Gemini requests to improve its products.

**Swipe to teach it your taste:** tap **Start swiping** for a deck of 10 movies and then 10 shows that most people know (the most-voted titles on TMDB, recent hits and this week's trending). Swipe right or tap ♥ to like, left or ✕ for nope, up or ★ for **Want to watch**, or tap **Haven't seen** to skip a card without it counting. Arrow keys work on a computer. Undo, Stop here and Swipe 10 more are there too. Your answers are saved in the install link, so install (or reinstall) after swiping.

Swipes work **without an AI key**. For each title you liked, the add-on asks TMDB for similar titles and ranks the ones that come up most often first. Titles similar to your nopes sink or are dropped, and genre taste from your likes and nopes nudges the available-now titles too. Titles you marked **Want to watch** are pinned to the top of For You. With an AI chosen, your swipes are also sent to it, alongside your note and Simkl history.

**Want to watch and Simkl:** with Simkl connected, Want to watch picks are also added to your Simkl **Plan to Watch** list. Quick picks are grouped into one write a few seconds later, and picks made before you connect are sent once you do. If you connected Simkl before this feature existed, your login can only read, and the page asks you to reconnect the first time you tap Want to watch. Undo stops a pick that hasn't been sent yet. Once it's on Simkl, remove it there. With Simkl connected, the deck also skips titles you've watched or already planned.

**Tell it what you like** in a short note, and/or **connect Simkl** so it learns from what you've actually watched, rated, dropped and saved to watch. With Simkl connected, titles you've already watched are hidden (you can switch that off). With no AI and no swipes, For You shows the same titles sorted by popularity, minus anything you've watched. The AI only runs when it has a note, swipes or Simkl history to work from.

**Speed and caching:** each row costs one AI request. A good ranking is cached for 6 hours (at Vercel's edge too), so most opens are instant. The first open after a change can take several seconds, and Stremio may show the row empty until you open it again. If the AI fails (wrong key, quota used up, a bad reply), the row falls back to popular titles and retries after about 10 minutes. **Check my setup** tests the AI key and the Simkl connection without showing either.

### For You as its own add-on

For You also has its own install page at **`/foryou`** on your site (for example `https://your-site.vercel.app/foryou`), built like a dating app:

1. **It opens on the swipe deck.** Full-screen cards with the poster, title, year and genres, progress bars across the top, and round buttons: Undo, Nope, Want it, Like and Not seen. Swiping works the same as on the main page (right, left, up; arrow keys on a computer).
2. **Done** (top right, or when the deck runs out) asks **"Are you done with your selections?"** on a match-style screen with the posters of what you liked. Choose **Yes, I'm done** or **Keep swiping**.
3. **Setup** follows: your picks, the rows to include, the AI, a taste note, Simkl, region and poster style, then **Install For You**. **Back to swiping** returns to the deck where you left off.

The deck can open before anyone types a key only if the site has its own TMDB key: set `TMDB_KEY` in Vercel and the TMDB field at setup becomes optional. Without it, the deck first asks for the visitor's TMDB key. Its Configure button in Stremio opens `/foryou` straight on the setup screen with your settings filled in.

- **One codebase, always in sync:** `/foryou` is the same page and the same server code as the For You tab on the main page. Any change to For You (the deck, the ranking, Simkl, the AI) reaches both on the next deploy. There's nothing to copy across.
- **Separate in Stremio:** its links live under `/foryou/...` and its add-on id is `community.foryou.app.<hash>`, so installing it never replaces a For You installed from the main page's tab (and the other way round). Install one or the other, unless you want two copies of the rows.
- **For You only:** whatever settings a `/foryou` link carries, it only ever serves the For You rows.
- The main page keeps its For You tab, and existing installs and links keep working unchanged.

### Turning on Simkl (for whoever runs the site)

1. Sign in at [simkl.com/settings/developer](https://simkl.com/settings/developer) and create an app of the **TV, devices & command line** type. This is a public app with no secret, which is what the PIN login needs.
2. Copy its **client ID** into a Vercel environment variable named `SIMKL_CLIENT_ID`, then redeploy.

Visitors then see a **Connect Simkl** button. It shows a short code to enter at simkl.com/pin; once approved, the add-on can read the person's history and add titles to their lists (Simkl's `media:write` permission, which is only used when they tap Want to watch). Simkl's refresh token lasts 180 days and renews each time it's used, so an add-on in regular use stays connected. Disconnecting removes it from the link; to revoke it fully, remove the app at simkl.com/settings/apps.

Simkl's rules allow free use for non-commercial projects and cap each app at about 1 POST a second (logins and Plan to Watch adds) and 10 reads a second, which is plenty for personal use but could be hit by a busy public site. Their published rules don't say anything about sending history to an AI provider, so check their full terms if you run this for other people.

## Deploy your own

1. Get a free API key at [themoviedb.org](https://www.themoviedb.org/settings/api).
2. Fork or copy this repo, then import it into [Vercel](https://vercel.com) with the **Other** framework preset.
3. Optional: add environment variables in Vercel (Settings, Environment Variables), then redeploy.
4. Open your Vercel address, enter your settings, and tap **Install in Stremio**.

### Environment variables (all optional)

| Name | What it does |
| --- | --- |
| `TMDB_KEY` | Fallback TMDB key. Also fills the decorative poster strips for every visitor. |
| `RPDB_KEY` | Fallback key for Rating Poster Database posters. |
| `TOPPOSTERS_KEY` | Fallback key for Top Posters. |
| `REGION` | Default region, such as `US`. |
| `DAYS_BACK` | Default "released within" window in days. |
| `SIMKL_CLIENT_ID` | Turns on **Connect Simkl** on the For You tab (see above). |

Keys belong in Vercel's environment variables, never in the repo.

If you share your deployment widely, set up Vercel's usage alerts so a burst of visitors doesn't surprise you.

## Poster styles

Plain TMDB posters, [RPDB](https://ratingposterdb.com) rating posters, [Top Posters](https://top-posters.com/api) rating posters, or a custom URL pattern from another provider. Use `{imdb_id}`, `{tmdb_id}` and `{type}` (movie or tv) as placeholders in the custom pattern.

Top Posters needs your own API key (free keys include 10,000 requests a month). Badge style and language are set in your Top Posters dashboard. The add-on asks Top Posters for the poster by IMDb ID and passes the plain TMDB poster as a fallback.

## Checking your setup

The **Check my setup** button on the install page tests your settings with one tap: whether your TMDB key works, whether TVMaze answers (on the Trash TV tab), whether your AI key works and Simkl is connected (on the For You tab), and whether your chosen poster provider's images load. Poster tests run in your browser, so the server never fetches a URL you typed in, and no key is ever shown in the results. The server side of the check is `/<settings>/check.json`.

## Updating without breaking installs

Stremio only re-reads an add-on's manifest when it is installed, and it can't auto-update configurable add-ons. So:

**Safe (everyone gets it automatically, no reinstall):**
- Changing filters, sorting, date windows or how titles are picked inside the existing rows
- Poster logic, bug fixes, and everything on the install page
- Adding a new optional setting, as long as it has a default so older links still work

**Needs a reinstall (avoid unless it's worth it):**
- Adding, renaming or removing catalogs or rows
- Changing the genre options or the add-on's name or types

**Never do this:**
- Rename or remove a catalog id or change the URL routes
- Remove or rename a setting that old install links contain
- Change how the add-on id is generated (it would install as a duplicate)

A reinstall is one tap: open your install page (or Stremio's Configure button, which opens it with your settings filled in) and press Install again. Reinstalling the same link replaces your copy.

## Privacy

Your settings, including your keys, are encoded in the add-on link so Stremio can use them. The add-on doesn't store keys, but it passes them to TMDB (and your poster provider) to fetch titles, and hosting logs may record requested addresses, which include the link. Treat your link like a password and don't share it. If a key leaks, regenerate it with the provider.

For You adds two more secrets to the link: your AI key and your Simkl login. Anyone with the link could use your AI quota (and run up charges on a paid plan), read your Simkl history and add titles to your Simkl lists. Your taste note, swipes and watch history are sent to the AI you pick so it can rank titles. Swipes are stored in the link as TMDB ids only. The Simkl login code is passed between the page and the server only in request bodies, never in a web address.

## Credits

- Watch history from [Simkl](https://simkl.com) when you connect it.
- Recommendations ranked by the AI you choose (Gemini, Groq, OpenRouter or Claude).
- Rating posters from [Top Posters](https://top-posters.com) when you choose it.
- TV schedules from [TVMaze](https://www.tvmaze.com), licensed CC BY-SA 4.0. It's free and needs no key, with a limit of about 20 calls per 10 seconds, so results are cached.
- Movie and TV data from [TMDB](https://www.themoviedb.org). This product uses the TMDB API but is not endorsed or certified by TMDB.
- Streaming availability data comes from JustWatch via TMDB.
- Rating posters from [RPDB](https://ratingposterdb.com) or the provider you choose.
- Not affiliated with Stremio.

## License

MIT. See `LICENSE`.
