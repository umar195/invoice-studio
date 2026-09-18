# Invoice Studio — GitHub se APK

Apne computer pe Android Studio ya SDK kuch install karne ki zaroorat nahi. Files GitHub pe rakho, GitHub apne server pe APK bana kar de dega.

## Kya hoga

Har baar jab tum files push karoge, GitHub Actions khud APK bana dega. 5–8 minute lagte hain. APK Actions page se download ho jati hai.

App **poori offline** hai — saara code APK ke andar hai, koi website load nahi hoti.

---

## Step 1 — repo banao

1. GitHub pe jao → **New repository**
2. Naam kuch bhi, jaise `invoice-studio`. Public ya private, dono theek.
3. **Create repository**

## Step 2 — files upload karo

Sab se aasan tareeqa browser se:

1. Repo page pe **Add file → Upload files**
2. Is folder ke andar ki **saari cheezein** drag karo:
   - `package.json`
   - `capacitor.config.json`
   - `www/` (poora folder)
   - `resources/` (poora folder)
   - `.github/` (poora folder — **ye sab se zaroori hai**)
3. **Commit changes**

> `.github` folder chhup sakta hai. Agar drag karne pe wo upload na ho, to GitHub pe **Add file → Create new file** dabao aur naam ke khane mein ye likho:
> `.github/workflows/build-apk.yml`
> phir `build-apk.yml` ka poora content paste kar do.

## Step 3 — build dekho

1. Repo ke upar **Actions** tab kholo
2. "Build APK" chal raha hoga (peela circle). Ho jaye to hara tick aa jayega.
3. Us run pe click karo → neeche **Artifacts** → **invoice-studio-apk** download karo
4. Zip khol lo, andar `app-debug.apk` hai

Agar build na chale to **Actions → I understand my workflows, go ahead and enable them** dabana parta hai (naye repos mein ek dafa).

## Step 4 — phone pe install

APK phone mein bhejo (WhatsApp, Drive, USB — kuch bhi). File kholo → "Unknown sources" allow karo → Install.

---

## App ka naam / ID badalna

`capacitor.config.json` mein:

```json
{
  "appId": "com.hassan.invoices",
  "appName": "Invoice Studio"
}
```

`appId` har app ka alag hona chahiye, format `com.kuchbhi.naam` rakho. Ek dafa decide karke chhor do — badalne pe phone isay nayi app samajhta hai aur purana data alag reh jata hai.

## Icon badalna

`resources/icon.png` ko apni 1024x1024 PNG se replace kar do. Baqi sab sizes GitHub khud bana leta hai.

## App update karna

`www/index.html` badlo → commit karo → Actions dobara APK bana dega → phone pe purani ke upar install kar do (data bacha rahega, kyunki appId wahi hai).

---

## Ye APK "debug" kyun hai?

Debug APK phone pe seedha install ho jati hai, bas. Ye Play Store ke liye nahi hai — Play Store ke liye release build aur apni signing key chahiye hoti hai.

Agar aage chal kar Play Store pe daalna ho to bata dena, workflow mein signing key wala hissa add ho jayega.

---

## Data ka masla

Phone wali app aur desktop wali file ka data **alag** rehta hai — dono ka apna storage hai.

Dono jagah same invoices chahiye to Settings mein **Download backup file** / **Restore from file** use karo.
