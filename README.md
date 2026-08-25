# Reversi (Android APK con GitHub Actions)

Juego Reversi original de [99fk/reversi-html](https://github.com/99fk/reversi-html) (GPL-3.0),
adaptado con botón de **pantalla completa** (web y nativo/inmersivo en Android) y empaquetado
como app Android con **Capacitor**. Incluye ícono y splash screen propios.

## Estructura
- `www/index.html` — el juego (HTML/CSS/JS puro).
- `android/` — proyecto nativo Android generado por Capacitor.
- `assets/` — logo (`logo.svg`) y splash (`splash.svg`) fuente.
- `.github/workflows/build-apk.yml` — compila el APK automáticamente.

## Cómo generar el APK

1. Sube este proyecto a un repositorio en GitHub (rama `main`).
2. Ve a la pestaña **Actions** del repo → el workflow "Build Android APK" corre solo,
   o dispáralo manualmente con "Run workflow".
3. Cuando termine (unos 3-5 min), descarga el APK desde:
   - **Artifacts** del run (`reversi-debug-apk`), o
   - **Releases**, donde se publica automáticamente en cada push a `main`.

## Comandos locales (opcional)

```bash
npm install
npx cap sync android
cd android && ./gradlew assembleDebug
```

El APK queda en `android/app/build/outputs/apk/debug/app-debug.apk`.

## Notas
- El APK generado es **debug** (sin firmar para producción). Para publicarlo en Play Store
  hay que generar un `keystore` y firmarlo (`assembleRelease` + firma).
- `appId`: `com.fatih.reversi` — cambialo en `capacitor.config.json` si lo vas a publicar
  bajo tu propio nombre de paquete.
