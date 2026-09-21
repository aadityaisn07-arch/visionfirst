# VisionFirst

**A free, open-source vision screening toolkit for NGO eye camps. Runs in any phone or laptop browser. No app, no extra hardware, no internet needed during a camp.**

**[▶ Try it now](https://aadityaisn07-arch.github.io/visionfirst/)** — opens straight in your browser.

---

## Why this exists

Community eye camps in India screen large numbers of people under real time and staffing pressure. Most still run on printed acuity charts and paper triage sheets, which slows throughput, makes follow-up hard to track, and leaves organisers without usable data on what the camp actually found.

I grew up around this. My father works as an ophthalmic assistant and goes out on camps as part of his job. VisionFirst is an attempt to close that gap with something free, open and light enough to run on a phone a camp worker already owns.

## What it does today

**Visual acuity test.** Measures how small a shape a patient can correctly identify at a fixed distance, and reports a standard Snellen fraction (6/6, 6/12, …) and logMAR value.

**Distance vision screening.** Finds the furthest distance at which a patient can still identify a fixed-size shape — their far point — and flags likely uncorrected short-sightedness for referral.

Both use a **Tumbling E** optotype: the patient just indicates which way the E opens. No reading required, so it works regardless of literacy or language.

**[Triage questionnaire](https://aadityaisn07-arch.github.io/visionfirst/triage.html).** A structured intake in Hindi and English that records why the patient came, screens for urgent symptoms, and captures the history that matters — diabetes without a recent eye check, family glaucoma, glasses never tested. It sorts each patient into **refer today**, **refer soon** or **routine**, so a worker screening two hundred people knows which few cannot wait. Reachable from the Triage link in the tool's header.

**[Camp report](https://aadityaisn07-arch.github.io/visionfirst/dashboard.html).** Load the day's two CSV exports and get the numbers an organiser actually needs: how many were screened, how many were flagged, the same-day referral list to hand to the supervisor before anyone goes home, the spread of visual acuity, and what drove the referrals. Copy it as text or print it as a PDF. It also carries sample data, so you can show someone what a camp report looks like before you have run one.

## How it stays accurate

A screening tool that shows the wrong size shape produces confident, wrong numbers. Four things guard against that:

**Real-world calibration.** Before the first test, you hold any bank, Aadhaar or ID card against the screen and resize an on-screen rectangle to match it. Every such card is 85.60 mm wide by international standard (ISO/IEC 7810 ID-1), so this measures the actual screen more reliably than typing in a spec sheet number. Saved per device, done once.

**Sizing by visual angle.** Optotypes are drawn so that overall height subtends 5 arc-minutes at logMAR 0, scaled for the distance you enter — the same geometry a printed chart uses.

**A proper staircase.** Responses drive a 2-down / 1-up adaptive staircase, which converges near the 70.7%-correct point, appropriate for a four-alternative forced-choice task. The reported threshold is the mean of the last four reversals, not the single best guess. This typically settles in 13–23 responses.

**Crowding bars.** Optional flanking bars around the optotype, on by default. Isolated letters overestimate acuity in amblyopia — a child with a lazy eye may read a lone letter fine and still fail a real chart line. Keep them on for school and amblyopia screening.

There is also a "Can't tell" response, so hesitation is recorded as not-seen rather than forced into a wrong guess.

## Running it at a camp

1. Open the link on a phone or laptop, calibrate once with an ID card.
2. Mark your testing distance on the ground before patients arrive (3 m suits most tents).
3. Work through the pre-flight checklist: screen brightness at maximum, distance marked, other eye properly covered, patient keeps their usual glasses on.
4. Screen each patient. Results save to a camp log on the device.
5. Export both logs as CSV at the end of the day, then open the camp report and load them in.

The interface switches between **English and Hindi** from the header.

## Data and privacy

Results are stored only in the browser on the device running the test. Nothing is uploaded, transmitted or shared — there is no server. Export the CSV before closing the browser, and clear the log when you're done.

## Status

| Component | State |
|---|---|
| Digital visual acuity test | Working |
| Distance vision / myopia screening | Working |
| Screen calibration | Working |
| Camp log and CSV export | Working |
| Bilingual Hindi/English interface | Working |
| Bilingual triage questionnaire | Working |
| Camp report and analytics | Working |

## Limitations — please read

**This is a screening aid, not a diagnosis.** It identifies people who should see a qualified eye-care professional. It does not produce a spectacle prescription.

**It only screens for reduced acuity and short-sightedness.** It cannot detect long-sightedness, astigmatism, cataract, glaucoma or any other eye disease. A normal result here does not mean healthy eyes.

**The triage questionnaire records what the patient reports; it does not examine them.** A patient who reports nothing can still have advanced disease. Every person screened should be offered a full examination — the questionnaire only decides who cannot wait for one.

**It has not yet been clinically validated.** The methodology follows established practice, but results have not been compared against clinical refraction or a standard chart in a published study. Treat it as a triage aid that flags people for proper examination, and validate it against your own standard before relying on it.

## Contributing

If you run eye camps and want to help shape this — especially on what actually works in the field versus what adds friction — open an issue or get in touch. Field feedback is worth more to this project than code.

## License

MIT. Use it, modify it, deploy it at your camps. See [LICENSE](LICENSE).

## Author

Built by **Aaditya Kumar Ahirwar** — independent researcher, OZTX Research Team.
ORCID: [0009-0009-5202-6337](https://orcid.org/0009-0009-5202-6337)
