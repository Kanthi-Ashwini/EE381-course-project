# Pushing this to GitHub

Nothing is committed yet — no `git init` has been run, so rename or edit freely
first.

1. Create an empty repo on GitHub named `EE381-biosig-ecg-shield`
   (no README, no .gitignore — this folder has both).

2. From inside this folder:

```bash
git init
git add .
git commit -m "BioSig: ECG acquisition shield (Altium PCB + fabrication data)"
git branch -M main
git remote add origin https://github.com/<user>/EE381-biosig-ecg-shield.git
git push -u origin main
```

3. Put the resulting URL into `../ee381-resume-snippet.tex`, replacing `<user>`.

## Before pushing

- **Size:** `BioSig.PcbDoc` is 5.1 MB and the Gerber container 0.8 MB — about
  5.9 MB total. Fine for GitHub (the warning threshold is 50 MB), but they are
  binary, so every future revision stores a fresh full copy. `.gitattributes`
  already marks them binary so git will not try to merge or rewrite them.
- **Add the schematic** if it exists anywhere. Without it the values and
  topology cannot be recovered, which is the repo's main weakness.
- **Add a board photo** and, if it was ever captured, an ECG trace. For a
  hardware repo these do more than any amount of README text.
- Fill in the instructor, semester and team members at the top of `README.md`.
- The design files are byte-identical copies of the originals in `KKSS.zip`;
  only the folder layout is new.
