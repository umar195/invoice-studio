# Invoice Studio APK (Roman Urdu Guide)

Yeh repo GitHub Actions se **debug/test APK** banata hai aur Defender scan ke baad verified artifact deta hai.

## APK kaise milegi

1. **Actions** tab kholo.
2. Latest **Build and Verify APK** run open karo.
3. Sirf tab use karo jab run green ho aur artifact me:
   - `invoice-studio-apk-verified`
4. Artifact ke andar:
   - `app-debug.apk`
   - `app-debug.apk.sha256`
   - `invoice-studio-apk.zip`

## Install (Android)

1. ZIP extract karo.
2. `app-debug.apk` phone me copy karo.
3. Install ke waqt agar unknown source permission aaye to browser/files app ke liye allow karo.
4. App update karte waqt **same appId** (`com.hassan.invoices`) rakho, warna data alag app me chala jayega.

## Security aur scan notes

- Yeh build automated checks se guzarta hai:
  - deterministic install (`npm ci` + lockfile)
  - runtime dependency audit
  - APK asset provenance checks
  - Windows Defender scan (APK + ZIP + extracted assets)
- **Koi bhi APK 100% safe guarantee nahi hoti.**
- Antivirus bypass, allowlist, ya scan disable karna recommend nahi hai.

## Agar Defender phir bhi detect kare

1. File ko force-install mat karo.
2. Workflow ka `invoice-studio-scan-evidence` artifact download karo.
3. Agar clean provenance ke bawajood detection repeat ho, Microsoft Security Intelligence submission next step ho sakta hai:  
   https://www.microsoft.com/en-us/wdsi/filesubmission
4. Submission se pehle team/user approval lo; bina approval external upload na karo.

## Local backup/data

App localStorage key `invoice-studio-v2` use karti hai.  
Settings me backup export/import se invoices migrate ki ja sakti hain.
