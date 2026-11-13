# GafiPresence

A clean Windows desktop editor for custom Discord Rich Presence. Built as a standalone Electron app and kept separate from the GafiSpeak source code.

## Features

- Live Discord-style preview while editing.
- Configurable activity name, details, state and activity type.
- Large and small image keys, hover tooltips and up to two buttons.
- Official Rocket League, Minecraft and Fortnite wordmark logos in the game gallery, plus original Gafi backgrounds. Selecting a game fills its image key automatically and uses the public logo image URL.
- Desktop shortcut creation/update on first portable launch, using the GafiPresence application icon.
- Elapsed timer with no artificial 24-hour cap.
- Elapsed-time and countdown modes.
- Built-in original SVG artwork gallery.
- Upload local PNG, JPG, WEBP and GIF files for previews and local asset management.
- Save multiple presets, import/export JSON and choose an accent colour.
- Discord RPC connection status, reconnect and clear-presence controls.
- Windows portable build through GitHub Actions.

## Requirements

- Windows 10/11 x64.
- Discord desktop app open and signed in.
- A Discord application created in the Developer Portal. Copy its Application ID into Settings.
- Node.js 22.12 or newer for development.

## Run from source

\`\`\`powershell
cd GafiPresence
npm install
npm start
\`\`\`

## Build a Windows portable executable

\`\`\`powershell
npm install
npm run build:win
\`\`\`

The portable executable is written to \`dist/\`.

## Set up Discord Rich Presence

1. Open the [Discord Developer Portal](https://discord.com/developers/applications).
2. Create or select an application.
3. Copy its Application ID into **Settings → Discord Application ID** in GafiPresence.
4. The built-in presets (Rocket League, Minecraft, Fortnite, Aurora, Grid and Circuit) are ready to use. The three game entries display official game logos. Selecting a game fills its key and, when Discord is connected, immediately updates the presence. Preset cards now apply the activity directly instead of only loading it into the editor. The built-in game logos use public HTTPS image URLs; an internet connection is required.
5. For your own images, open **Rich Presence → Art Assets** in that application, upload the image, give it a key, then enter that exact key in the Large Image or Small Image field. Alternatively, enter a publicly accessible HTTPS image URL. External HTTPS image URLs are supported by Discord Rich Presence for both large and small images.
6. Keep the Discord desktop app open and press **Connect**, then **Apply presence**.

### Important: local uploads vs Discord assets

An image uploaded from your computer is stored locally by GafiPresence and is available in the editor preview. The local file path itself cannot be sent to Discord. For a custom upload, use **Transferir Large PNG** or **Transferir Small PNG**, upload that PNG to your Discord application's Rich Presence Art Assets and enter its asset key. The included game and Gafi backgrounds are different: they use public HTTPS URLs and therefore work without a manual upload.

The app keeps the local preview path and the Discord asset key as separate values so the preview never implies an image was published when it was not.

### Game logo sources and attribution

- Rocket League logo: Psyonix, via Wikimedia Commons, licensed CC BY-SA 4.0. Source: https://commons.wikimedia.org/wiki/File:Rocket_League_logo.svg
- Minecraft logo: Mojang Studios, via Wikimedia Commons. Source: https://commons.wikimedia.org/wiki/File:Minecraft_Logo-en.svg
- Fortnite logo: Epic Games, via Wikimedia Commons. Source: https://commons.wikimedia.org/wiki/File:FortniteLogo.svg

Game names and logos remain the property of their respective owners. GafiPresence is an independent fan-made utility and is not affiliated with or endorsed by these publishers.

## Game logo sources and attribution

- Rocket League logo: Psyonix, via Wikimedia Commons, CC BY-SA 4.0: https://commons.wikimedia.org/wiki/File:Rocket_League_logo.svg
- Minecraft logo: Mojang Studios, via Wikimedia Commons: https://commons.wikimedia.org/wiki/File:Minecraft_Logo-en.svg
- Fortnite logo: Epic Games, via Wikimedia Commons: https://commons.wikimedia.org/wiki/File:FortniteLogo.svg

Game names and logos remain the property of their respective owners. GafiPresence is an independent fan-made utility and is not affiliated with or endorsed by these publishers.

## Rich Presence limits

- Discord displays the application name from the registered Discord application.
- Details and State are limited to 128 characters each.
- A maximum of two custom buttons is supported.
- Button URLs must be valid HTTP or HTTPS links.
- Elapsed and countdown timers use JavaScript `Date` values, serialized by the RPC library as Unix timestamps in milliseconds.
- RPC is local to the Discord desktop client. This is not a bot and does not require a bot token.

## Local data and privacy

Settings, saved presets and uploaded preview images are stored in the current Windows user's Electron user-data directory. The app does not need a Discord bot token and does not send your local images to a GafiPresence server. Import/export files are ordinary JSON.
