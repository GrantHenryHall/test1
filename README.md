# 🔔 Whistle Alarm

A single-page web app that listens through your device's microphone, counts
pressure-cooker whistles, and sounds an alarm once a target number is reached.

No install, no build step — it's one `index.html` file.

## How it works

The app uses the browser's microphone (Web Audio API) to measure how loud the
room is, many times per second. When the loudness crosses **above a threshold**
and stays there long enough, it counts that as one whistle. Once the count
reaches your target, it plays a loud beeping alarm and vibrates (on phones).

## How to use it

1. Open `index.html` in a browser.
   - On a phone this must be served over **HTTPS** (or `localhost`) for the
     microphone to work. The easiest options:
     - GitHub Pages (enable Pages for this repo → open the published URL), or
     - run a local server: `python3 -m http.server` then open
       `http://localhost:8000` on the same machine.
2. Set **Whistles before alarm** (e.g. 3).
3. Tap **▶ Start listening** and allow microphone access.
4. Place the phone near the cooker.
5. Watch the **Mic level** meter. The white line is your threshold:
   - If normal kitchen noise pushes the bar past the line, **raise** the
     threshold.
   - If real whistles don't reach the line, **lower** it.
6. **Min. whistle length** filters out short clicks/clinks so only a sustained
   whistle counts.
7. When the target is hit, the alarm sounds. Tap **↺ Reset count** to silence
   it and start over.

Use **🔊 Test alarm sound** to preview the alarm at any time.

## Tips

- Keep the screen on — the app requests a wake lock while listening, but you
  may also want to disable auto-lock.
- Start with threshold ~50% and a 0.3s minimum length, then fine-tune against
  one real whistle.
- The mic uses no noise suppression / auto-gain so readings stay consistent.

## Privacy

Everything runs locally in your browser. No audio is recorded, stored, or sent
anywhere.
