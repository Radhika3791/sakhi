# Sakhi Voice

A voice-first assistant for India's ASHA and anganwadi workers. She speaks a home-visit note in Hindi, Telugu, Marathi or English (mixed words are fine). Sakhi Voice turns it into a structured health record, reads it back for confirmation, flags danger signs, and fills a mock government register.

Theme: Healthcare access. Extension of my Round 1 idea.

## Run it (one command)

```
docker compose up --build
```

Then open http://localhost:8080 in Chrome or Edge. No secret keys, no accounts, no backend.

Without Docker: open `index.html` in Chrome.

## The core flow

1. Pick a language and tap the mic.
2. Speak the visit note, for example: "Sunita Devi, 8 mahine ki pregnant, BP dedh sau by sau tha, iron ki goli di, agle hafte dobara jaana hai."
3. The app shows the live transcript and extracts name, months pregnant, BP, medicines, next visit.
4. It reads the summary back aloud and asks "Is this correct?"
5. Say "haan" to save, or say a correction ("nahi, BP 160 by 100 hai") and only that field changes.
6. Danger signs (high BP, bleeding, newborn fever, missed vaccine, low weight) show a red alert and a spoken same-day referral action.
7. The saved visit appears in the visit list and the mock government register.

## Noise, accents and mixed languages

- Empty or very short speech: the app says "I could not hear clearly" and asks again. It never guesses silently.
- Hinglish and code-mixing: rule-based parsing of Hindi, English, Telugu and Marathi keywords in one sentence.
- Spoken numbers and dates: "dedh sau by sau" becomes 150/100, "agle hafte" becomes 7 days, "kal" becomes 1 day.
- Missing name: asks one short follow-up question.
- Type-instead box and example buttons always work if the mic does not.
- Records are saved in the browser, so it works offline.

## Dependencies

- Browser speech recognition and speech synthesis (Chrome or Edge recommended).
- Docker with nginx:alpine, only to serve one static file.

## Limits

This is a prototype. Parsing is rule-based. Do not use real patient data.
