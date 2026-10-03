# Hearth: hosting and connection guide

## What is ready

Hearth 1.0 is a standalone website. No installation, build tools, or paid server is needed for its existing features. The supplied `hearth-release/index.html` contains the app; `.nojekyll` is a hosting helper. The site has not yet been published.

| Feature | Available in this release | Setup |
|---|---|---|
| Four layouts, clock | Working | Open the site |
| Shopping, notes, personal planner | Working, saved in this browser | Enter your own items |
| Kitchen timer | Working, visual alert | Keep page open and display awake |
| Weather | Live request with unavailable state | Set city; internet needed |
| Photos | Local upload and slideshow | Select photos on the device |
| Local music | Browser audio playback | Select audio files each session |
| Spotify | Official embedded player | Paste a supported Spotify link |
| Google Calendar | Shortcut only | Sign into Calendar separately |
| Ring | Shortcut; no video embedded | Native Family Hub widget for supported cameras |
| SmartThings and fridge temperatures | Demo values, no device commands | Additional authenticated integration needed |

## 1. Publish the dashboard

Default route: GitHub Pages. If you already have hosting, upload `index.html` to its web root instead.

1. Download and unzip `Hearth_Ready_To_Host.zip`.
2. Sign into [GitHub](https://github.com/). Create a repository named `hearth-dashboard`, enable a README, and choose **Public** for GitHub Free.
3. Open the repository and choose **Add file → Upload files**. Upload `index.html` from `hearth-release` directly into the repository root. Do not upload the ZIP itself or put the HTML inside another folder. The included `.nojekyll` file can also be uploaded; it may be hidden in your file picker.
4. Commit the files to `main`.
5. Open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/(root)`, then save.
6. Wait for deployment, then use **Visit site**. The address will resemble `https://YOUR-USERNAME.github.io/hearth-dashboard/`.
7. Open the published HTTPS address on your computer first. Enable **Enforce HTTPS** in Pages settings if available.

The source and website are public. Upload only the supplied application files; never upload personal-photo exports or account credentials. Photos, lists, and notes entered through Hearth stay in that browser’s storage; they do not become repository files. The default display name and city in the HTML are visible publicly.

Sources: [GitHub Pages setup](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site), [publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site), [HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https).

## 2. Open it on the refrigerator

1. Connect the fridge to Wi-Fi.
2. Open its Internet/browser app, if available on your firmware.
3. Enter the published HTTPS address, including `/hearth-dashboard/`.
4. Bookmark it using the browser’s available controls. If the browser offers a home-screen shortcut, you can use it; availability has not been verified on your fridge.
5. Test Today, Memories, Home, and Kitchen. Add a shopping item, reload, and confirm it remains.
6. Try a five-minute timer, photo selection, and audio playback.

Hearth runs inside the browser. It does not replace Samsung’s operating system, automatically start at boot, or guarantee an always-on screen. Browser support, media access, sleep behavior, and touch layout still need testing on your actual refrigerator.

## 3. Connect weather

1. Tap the gear at the top right.
2. Enter your display name and a city such as `McKinney, Texas`.
3. Tap **Save & close**. Weather is requested on initial page load and after a city change.
4. In Kitchen or Home, tap **Update** to refresh it later.
5. A successful request shows a live-weather label in those views. If it fails, Hearth shows a dash and an unavailable message, rather than a made-up temperature.

No API key is needed for Open-Meteo’s free noncommercial service. Check spelling, internet access, and whether the fridge browser can reach the service if weather fails. The current release does not automatically refresh weather on a schedule; use Update or reload.

Sources: [Open-Meteo location lookup](https://open-meteo.com/en/docs/geocoding-api), [usage terms and pricing](https://open-meteo.com/en/pricing).

## 4. Set up music

### Spotify

1. Open Spotify on your computer or phone.
2. Open a playlist, album, or track, then use **Share → Copy link**.
3. Open Hearth on the fridge, tap the gear, and paste the full `https://open.spotify.com/playlist/...` link into the Spotify field. A `spotify.link` short link must be expanded to its destination first.
4. Save, open **Kitchen**, and find the embedded player inside the Music card.
5. Tap Play. Login, playback availability, and browser support are governed by Spotify. This is an embed, not Spotify Connect control.

If the embedded player cannot play on the fridge, try the Spotify shortcut or Samsung’s available native music app. [Spotify embeds](https://developer.spotify.com/documentation/embeds) support interactive playback; encrypted-media problems can depend on the browser ([troubleshooting](https://developer.spotify.com/documentation/embeds/tutorials/troubleshooting)).

### Your own audio

Tap **Add music**, select supported audio files, and use the playback controls. Files must be accessible through the fridge browser’s file picker. They are not uploaded to a server and must be selected again after reopening the page.

## 5. Add photos and family information

1. Open **Memories → Add your photos**, or **Add photos** in another view.
2. Select a small set of photos accessible on that device. The app accepts up to 16 per selection and ignores files of 15 MB or larger. A new selection replaces the existing collection.
3. Test previous, next, and pause. Photos are resized before browser storage; storage may still fill up.
4. Enter shopping items in Today or Kitchen; check them off when bought.
5. Use **Your day** to enter a time and plan. This is a manually maintained list: it does not reset at midnight or sync with Google Calendar.
6. Add a note in Memories or Kitchen.

The laptop, phone, and fridge each have separate browser storage. Your existing local-file data will not automatically transfer to the new HTTPS site. Clearing site data removes saved content. Samsung’s native photo upload does not automatically feed Hearth’s custom slideshow. If the fridge file picker cannot access photos, shared photo storage is a separate feature to build.

## 6. Set up Ring on Family Hub

This connects Samsung’s native experience, not the video panel inside Hearth.

1. Confirm the doorbell works in the Ring app.
2. Use the same Samsung account in SmartThings on your phone and on the refrigerator.
3. In SmartThings, check **Add device** for your Ring model/integration and follow the available account-linking flow. Availability depends on the camera model, region, and software.
4. On Family Hub, add or open **SmartThings Video** or the available Ring widget.
5. If the supported camera appears, tap it to test live video.
6. Keep Hearth bookmarked for the dashboard and use the native widget for camera viewing.

If the camera does not appear, check model compatibility before proceeding. Hearth’s Open Ring button opens Ring’s website; it does not establish a camera connection. Samsung documents same-account camera access through the [SmartThings Video widget](https://www.samsung.com/us/support/answer/ANS10001626/).

## 7. Prepare real SmartThings temperatures

### What you can do now

1. Open SmartThings on your phone and confirm the refrigerator appears.
2. Add your thermostats or temperature sensors using the supported manufacturer integration.
3. Confirm that each device exposes a real temperature reading in SmartThings.
4. Name them clearly, such as Downstairs and Upstairs.
5. Use Samsung’s native SmartThings widget for current device access while the custom connection is built.

### What still needs to be built for Hearth

The included website has no Connect SmartThings button or backend. Its temperature buttons change demo targets only.

The next implementation needs: an authenticated backend; a SmartThings Service Integration using OAuth; a sign-in/account-linking flow; secure token storage and refresh; device discovery and mapping; and read-only temperature retrieval into Hearth. Device controls can follow after readings are verified. Exact callback URLs depend on the chosen backend host, so do not register guessed URLs now.

Do not paste a SmartThings token into the public HTML. Newly created personal access tokens expire after 24 hours; ongoing access should use a Service Integration. Sources: [authorization](https://developer.smartthings.com/docs/getting-started/authorization-and-permissions), [OAuth architecture](https://developer.smartthings.com/docs/service-integrations/architecture-and-auth-flow).

## 8. Google Calendar

The Calendar shortcut works now by opening Google Calendar. Events do not appear automatically in Your day.

To add private events to Hearth, the next implementation must enable the Calendar API in a Google Cloud project, configure OAuth consent and a web client, register the actual hosted origins/callbacks, obtain your consent for read-only calendar access, and render selected calendars. A persistent fridge display may benefit from a backend to manage sessions and token refresh. Do not make your family calendar public to work around authentication.

These are the integration prerequisites, not steps that activate an existing feature in this release. [Google’s official JavaScript quickstart](https://developers.google.com/workspace/calendar/api/quickstart/js) explains the API and authorization setup.

## 9. Updates and troubleshooting

- **404 after publishing:** confirm `index.html` is at the selected publishing root and the deployment succeeded.
- **Old version:** reload the page after deployment. Avoid clearing browser storage unless you are prepared to lose saved photos and lists.
- **Lists missing on another device:** expected; cross-device sync is not built yet.
- **No weather:** check the city and network, then tap Update.
- **Timer alert delayed:** the browser may suspend in the background or while the screen sleeps; use a native alarm for timing that must work when Hearth is closed.
- **Temperature unchanged in your home:** current controls are explicitly demo-only.
- **Update the website:** upload the replacement `index.html` at the same path and commit. Keeping the same website address preserves the browser-storage location.

Recommended order: publish Hearth → verify it on the fridge → configure weather and music → verify devices in SmartThings → build the selected private-account integration.
