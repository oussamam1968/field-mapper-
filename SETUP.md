# AGOL Field Mapper web app: setup

The app is two files: `index.html` (the tool) and `oauth-callback.html` (finishes sign-in).
Your data never leaves ArcGIS. The page runs in each user's browser and talks to ArcGIS Online directly.

## 1. Put the two files on an HTTPS address

**Option A: GitHub Pages (free)**
1. Sign in to github.com and create a new repository, for example `field-mapper` (Public).
2. **Add file → Upload files**: upload `index.html` and `oauth-callback.html`, then **Commit changes**.
3. **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main`, folder `/ (root)`, **Save**.
4. After a minute the app is at `https://YOUR-GITHUB-NAME.github.io/field-mapper/`.

The repository is public, but it holds no passwords or data. The Client ID is not a secret.

**Option B: NPA web server**
Ask IT to copy both files into one folder served over HTTPS, for example `https://gis.npaid.org/field-mapper/`.

## 2. Register the app in ArcGIS Online (once, about 2 minutes)

1. In npaid.maps.arcgis.com go to **Content → New item → Developer credentials → OAuth 2.0 credentials**.
2. Redirect URLs: add both addresses (use your real address from step 1):
   - `https://YOUR-GITHUB-NAME.github.io/field-mapper/`
   - `https://YOUR-GITHUB-NAME.github.io/field-mapper/oauth-callback.html`
3. Title it "AGOL Field Mapper" and save. On the item page, copy the **Client ID**.

## 3. Put the Client ID in the app

Open `index.html` in Notepad. Near the top, replace `PASTE_YOUR_CLIENT_ID_HERE` with the Client ID.
Upload the changed `index.html` again (GitHub: open the file → pencil icon → paste, or upload over it).

## 4. Test it

Open the app address, click **Sign in to ArcGIS** (allow the pop-up), choose your layers and run a **Preview**.
Without a Client ID, or with `?demo=1` at the end of the address, the app opens in demo mode with sample layers.

## 5. Add it to Experience Builder

1. Open your experience, add an **Embed** widget and choose **By URL**.
2. Paste the app address and stretch the widget to fill the page.
3. Save and publish. Sign-in opens in a pop-up window, so users must allow pop-ups for the site.

## Another portal (for example UNMAS)

In a layer box choose **Another ArcGIS portal**, enter `https://ims.unmas.org/portal` and click **Connect**.
- With no App ID, a username/password window appears. This works for built-in portal accounts only.
- For company logins (SSO), register the app on that portal too (same steps as section 2, done in the UNMAS portal) and paste its Client ID in the box.
- If the portal only works inside the UNMAS network or VPN, it can be used only from computers on that network.

## Notes

- Saved mappings are kept in the browser. Use **Export file** and **Import file** to share them or move them to another computer.
- Each user needs edit rights on the target layer, and on the source layer if they mark records as sent.
- No Notebooks licence is needed.
