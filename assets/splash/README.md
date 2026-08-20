# Splash screens – Your Budgeting

## Folder layout (put this under your repo root as `assets/splash/`)

```
assets/splash/
├── ios/
│   └── splash-2732x2732.png    # 2732×2732 – iPhone + iPad
└── android/
    ├── splash.png              # 1280×1920 – Android phones
    └── splash-2732x2732.png    # 2732×2732 – Android tablets (optional)
```

## Codemagic (after `npx cap sync ios`)

```yaml
- name: Replace iOS splash
  script: |
    SPLASH_SRC="assets/splash/ios/splash-2732x2732.png"
    test -f "$SPLASH_SRC"
    DEST="ios/App/App/Assets.xcassets/Splash.imageset"
    test -d "$DEST"
    rm -f "$DEST"/*.png
    cp "$SPLASH_SRC" "$DEST/splash-2732x2732.png"
    cp "$SPLASH_SRC" "$DEST/splash-2732x2732-1.png"
    cp "$SPLASH_SRC" "$DEST/splash-2732x2732-2.png"
    echo "iOS splash replaced"
```

Background colour in capacitor.config.json: #6C5CE7
