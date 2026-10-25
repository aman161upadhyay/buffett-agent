# Research guide for all workers on the Buffett-agent project

## What this project is
Aman Upadhyay (HBS, Seminar in Investing, Fall 2026; sponsor Laurion Capital) is building AI agents that reason like
specific great investors. This repository is the **Warren Buffett / Berkshire Hathaway** agent (a sibling of
`ackman-agent/`, which is finished and is the template for everything here — same folder layout, same file schemas,
same grading harness). The agent is graded on *fidelity of decision AND reasoning* to Buffett's real decisions, replayed
point-in-time, not on returns. Rubric per trade: Direction, Reasoning overlap (did it cite the drivers Buffett cited?),
Discipline (does it pass on what he passed on?), Grounding (claims traceable to the data pack, not model memory).
The final model is a small, pre-dated open model (Llama 3.1 8B, data to Dec 2023), so everything the agent must
"know" has to be written down explicitly.

Today's date: 25 October 2026. Anything up to today is fair game for the archive. Be especially careful with
2024-2026 events (Apple and Bank of America trims and their stated tax rationale, the record cash build, the buyback
halt, Chubb, Constellation, Domino's/Pool, UnitedHealth (Q2 2025), Alphabet (Q3 2025), the OxyChem purchase (Oct 2025),
Buffett's 10 Nov 2025 letter and CEO hand-over to Greg Abel on 1 Jan 2026, every 13F from Q3 2025 through Q2 2026, the
2026 annual letter and meeting, and anything Buffett/Abel/Combs/Weschler did in 2026) because those are the hold-out
decisions. Decisions made by Todd Combs or Ted Weschler must be labelled as such (`decider: Combs|Weschler|Buffett|Abel|unknown`).

Era switch used in this repo (keep these labels): A = Partnership & early Berkshire 1956-1979 (Graham cigar butts ->
quality, control positions, insurance float); B = 1980-1999 (great businesses at fair prices, Coke/Gillette/Wells, Salomon,
Gen Re, "Mr. Buffett on the stock market"); C = 2000-2015 (elephants, crisis deals 2008-11, BNSF, Heinz/3G, IBM, deputies
hired 2010-12); D = 2016-mid 2025 (Apple, airlines, Occidental, Japan, buybacks, cash build); E = hold-out, H2 2025-2026
(UNH, Alphabet, OxyChem, Abel era).

## Tools that work here (use them from CodeExecution)
- `webSearch({ query, searchQueries: [..], count: 10, isTextExtended: true })` — best first move. Returns snippets + URLs.
- `webFetch({ url })` — fetch a page/PDF as markdown (50k-char chunks; use `startIndex` to continue).
- `externalApi__exa({ path:'/search', method:'POST', headers:{'Content-Type':'application/json'}, body:{ query, numResults: 10, contents:{ text:{ maxCharacters: 3000 } }, startPublishedDate?, endPublishedDate?, includeDomains? } })` — semantic search with page text; `/contents` with `urls:[...]` pulls full text (works where Firecrawl is rate-limited).
- `externalApi__firecrawl({ path:'/scrape', method:'POST', headers:{'Content-Type':'application/json'}, body:{ url, formats:['markdown'] } })` — works on SEC EDGAR pages, PDFs, most news sites, x.com status URLs. Expect 429s under load; back off and prefer Exa `/contents` or `webFetch`.
- `queryWithLLM({ content, query })` — ask a question of a long document (a 25-page letter) instead of reading it all.
- NOT available: the X API (402). Reddit: `webFetch` is blocked; try Firecrawl on `https://old.reddit.com/...` and snippets via `webSearch`/Exa.
- Keep ≤5 Exa/Firecrawl requests in flight at once.

## High-value primary sources
- Berkshire shareholder letters 1977-2025: https://www.berkshirehathaway.com/letters/letters.html (1965-1976 letters are in the
  "Berkshire Hathaway Letters to Shareholders 1965-2014" compilation; many mirrors). Buffett's 10 Nov 2025 letter and Greg Abel's
  first annual letter (Feb 2026) are on berkshirehathaway.com/news.
- Buffett Partnership letters 1957-1970 (full text on many sites: search "Buffett Partnership letter 1963 Sanborn Map" / "Dempster" /
  "American Express 1964 letter").
- Annual meeting Q&A 1994-2026: CNBC Warren Buffett Archive https://buffett.cnbc.com (transcripts + video), buffettfaq.com
  (quotes by topic, 1994-2021 meetings), "University of Berkshire Hathaway" (meeting notes 1986-2015).
- Fortune/Carol Loomis pieces ("Mr. Buffett on the Stock Market" 1999, "Warren Buffett on the stock market" 2001, "Buy American. I Am."
  NYT 2008-10-16, "The Superinvestors of Graham-and-Doddsville" 1984), Forbes 1979 "You pay a very high price in the stock market for a
  cheery consensus", 1991 Salomon Congressional testimony, Becky Quick CNBC interviews 2008-2025, Charlie Rose interviews.
- SEC: Berkshire 13F (CIK 1067983, quarterly since 1999 — 13f.finance, dataroma, whalewisdom, stockcircle for history and change
  tables), 13D/13G filings (Occidental, Kraft Heinz, American Express, Coca-Cola, BofA), 8-Ks and merger proxies (BNSF 2009-10,
  Heinz 2013, Precision Castparts 2015, Alleghany 2022, Pilot, OxyChem 2025), Berkshire 10-Ks/10-Qs (equity concentration tables,
  cash, buybacks), press releases https://www.berkshirehathaway.com/news/newslist.html.
- Books (cite by chapter): *The Snowball* (Schroeder), *Buffett: The Making of an American Capitalist* (Lowenstein), *Berkshire
  Beyond Buffett* (Cunningham), *The Essays of Warren Buffett* (Cunningham), *Of Permanent Value* (Kilpatrick), *Dear Chairman*
  (Gramm — Buffett and American Express chapter), *Richer, Wiser, Happier* (Green), *Poor Charlie's Almanack*, *Damn Right!*.
- Secondary analysis: Rational Walk, Kingswell, Brooklyn Investor, Semper Augustus letters, COBF (cornerofberkshireandfairfax.ca —
  the Berkshire board is the deepest forum), r/ValueInvesting, r/SecurityAnalysis, Value Investors Club write-ups on Berkshire
  positions, Seeking Alpha, Barron's/WSJ/FT/Bloomberg/Reuters coverage, Nikkei for the Japanese trading houses.

## Writing rules
1. Every factual claim gets a source (URL + date) inline or in a numbered list. Prefer primary sources (letters, filings, transcripts).
2. **No hindsight contamination** in "point-in-time" sections: write only what was knowable on that date and date-stamp numbers.
3. Quote Buffett verbatim wherever possible; his *stated reasons at the time* are the grading key. Mark hindsight quotes as hindsight
   (he often explains a purchase only in the following February's letter — note the lag explicitly).
4. Be honest about losses, reversals and sins of omission; divergences are as valuable as matches. Buffett's own post-mortems
   (Dexter, ConocoPhillips, Tesco, IBM, Precision Castparts, Kraft Heinz, USAir, Salomon, Gen Re, Berkshire textiles, Blue Chip,
   airlines 2020, Paramount, "thumb-sucking" on Walmart/Fannie Mae) are first-class material.
5. Where sources conflict or you are unsure, say so explicitly (`unverified`, `conflicting`). Never invent dates, numbers or quotes.
6. Dense, factual prose and tables; no filler, no hagiography.
7. Files are Markdown; keep each under ~60 KB; split if needed. Write with the `writeFile` callback or the WriteFile tool.
8. When you finish, append a short entry to `buffett-agent/run_log.md` (what you produced, open gaps, corrections you verified).
9. Mirror the Ackman repo's file schemas exactly: `compendium/SCHEMA.md` (trade files), `calibration/README.md` (packs/keys),
   and look at `ackman-agent/calibration/data_packs/2025_uber_buy/` + `ackman-agent/calibration/answer_keys/2025_uber_buy.json`
   as the worked example of a pack and key. In `meta.json` use `fund_aum_usd_bn` (Berkshire equity portfolio or cash figure,
   say which) instead of `pershing_aum_usd_bn`.
