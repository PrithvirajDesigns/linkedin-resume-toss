# LinkedIn Toss 🏀🗑️

> A real simulation of LinkedIn job listings.

Crumple your application into a ball, toss it at the hoop, and watch it end up exactly where it was always going: the trash can.

**LinkedIn Toss** is a satirical 3D browser game about the modern job hunt. It's a single HTML file with no build step, no image assets and no install.

<!-- Demo: drag demo.mp4 into this README on GitHub to embed it here -->

---

## Features

- **3D third-person view.** The ball, a toy-style hoop on a smoked-glass backboard, and a brushed-steel trash can, rendered with Three.js.
- **Cover-letter crumple intro.** A full application letter folds itself into the paper ball before your first throw.
- **Pull-and-release controls.** Drag down to wind up, sideways to aim, and let go. A live arc preview shows whether you're *On target*, *Close*, *Wide* or *Too short*.
- **Hand-rolled physics.** Gravity, drag, spin, and collisions with the rim, backboard, can and floor, run at a fixed 240 Hz step.
- **Job-hunt events:**
  - **Requirements updated:** every 5 throws the rim shrinks or the hoop moves ("10+ years of experience for entry level").
  - **Ghosted:** the hoop can fade away mid-flight.
  - **Referral:** a bigger rim for one shot.
  - **Networking bonus:** a bank shot off the backboard scores +3.
- **Recruiter replies.** After every throw a chat-style toast arrives with a (rejection) message.
- **Offer letter.** After 20 applications you get a paper-style offer letter with your stats and a rank based on your score.
- **Apple-inspired UI.** Liquid-glass scoreboard, Dynamic-Island-style alerts and iOS-style sheets, set in Helvetica Neue.
- **Synthesized sound.** Every effect is generated with the Web Audio API (no audio files), with a mute toggle.
- **Responsive.** Works with a mouse or touch on desktop, tablets and phones, in portrait and landscape.

## Play

1. Download or clone the repo.
2. Open `index.html` in a modern browser.

That's it. You need an internet connection the first time, because Three.js loads from cdnjs.

To run it from a local server instead:

```bash
npx serve .
# or
python3 -m http.server 8000
```

### Host on GitHub Pages

Go to **Settings → Pages**, set the source to the `main` branch and the root folder (`/`), and the game goes live at `https://<your-username>.github.io/<repo-name>/`.

## How to play

| Action | Mouse | Touch |
|---|---|---|
| Wind up | Click the ball and drag down | Touch the ball and pull down |
| Aim | Drag left / right while pulling | Same |
| Throw | Release | Lift your finger |
| Mute | 🔊 button on the scoreboard | Same |

**Scoring**

| Shot | Points |
|---|---|
| Through the hoop | +2 |
| Bank shot off the backboard | +3 bonus |
| Miss | 0 (and the ball stays on the floor) |

You get 20 throws. Your score sets the job title on your offer letter.

## Customize

All the game tuning lives in the `CFG` object near the top of the script:

```js
const CFG = {
  gravity: 9.81,
  launchAngle: 52,        // degrees above horizontal
  minSpeed: 4.0,          // m/s at the smallest pull
  maxSpeed: 11.5,         // m/s at full pull
  rimR: 0.25,             // starting rim radius
  rimShrink: 0.025,       // per "requirements update"
  totalThrows: 20,
  ghostChance: 0.14,      // chance the hoop ghosts you
  referralChance: 0.14,   // chance of a bigger rim
  exposure: 0.8,          // scene brightness
  // ...
};
```

Recruiter messages, event alerts and offer-letter ranks are in the `MSG` and `RANKS` lists, so you can add your own.

## Tech

- **Three.js r128**, loaded from cdnjs, for rendering
- Custom sphere-vs-ring, sphere-vs-box and sphere-vs-cylinder physics, no physics library
- Procedural canvas textures for the paper, letter, stickers, steel and glass
- **Web Audio API** for every sound
- Plain HTML, CSS and JavaScript in one file, with no frameworks or build tools

## Project structure

```
.
├── index.html   # the entire game
└── README.md
```

## Browser support

Recent Chrome, Edge, Safari and Firefox on desktop and mobile. WebGL must be available. The liquid-glass refraction is strongest in Chromium browsers and falls back to a frosted blur elsewhere.

## Disclaimer

This is a parody made for fun. It is **not affiliated with, endorsed by or connected to LinkedIn Corporation**. "LinkedIn" is a trademark of LinkedIn Corporation. The game uses no LinkedIn logos or brand assets. All companies, recruiters and job titles in the game are fictional.

## License

MIT. Do whatever you like, and maybe send one more application while you're at it.
