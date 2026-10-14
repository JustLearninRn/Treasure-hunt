# QR Treasure Hunt (Netlify)

## Deploy once
1. Put this folder in a GitHub repo (github.com -> New repository -> "uploading an existing file", drag everything in).
2. Netlify -> Add new site -> Import from Git -> pick the repo. Leave build settings as they are.
3. Site configuration -> Environment variables -> add ADMIN_PASSWORD (your organiser password).
   Optional: SESSION_SECRET (any long random text).
4. Deploys -> Trigger deploy (so the variable takes effect).
5. Site configuration -> Change site name, to get a clean permanent link like https://mycollege-hunt.netlify.app

## Run the event
Open <your link>/admin, log in, then: add QR stations, add teams (+ passwords), build each team's route/clues.
Open /admin on your final link BEFORE printing the QR codes (the Stations tab has "Print all QR codes").
Everything is stored in Netlify Blobs; edits in the portal apply instantly, no redeploy needed.

## How the game logic works (routes are fully independent)
1. A QR station is only a sticker. Many teams can use the same station, each with its OWN clue text.
2. Every team has its own route. Nothing one team does can change another team's route or progress.
3. Inside one route a station can appear only once (admin panel flags duplicates, server rejects them).
4. Progress = one number per team. Scanning the CURRENT step's QR moves it +1.
5. Teams only affect each other through ASSIST (send a location hint) and SABOTAGE (jam one clue of one team).
6. A station used in any route can't be deleted. If you edit a route after a team has progressed, the admin asks
   before rewinding that team (other teams are never touched).

## Player extras
Rank system (E → S), XP bar, Sensei hints, typewriter clues, synth sound effects (toggle bottom-right), neon embers background.
