# Canolia Assets & Content Update Guide (လမ်းညွှန်ချက်)

ဤဖိုင်သည် Canolia Kodomo App အတွက် အသစ်ပြင်ဆင်ထားသော စာလုံးပေါင်းများ၊ သဒ္ဒါရှင်းလင်းချက်များ၊ ရုပ်ပြဇာတ်ကွက်များနှင့် ဒေတာဘေ့စ်များကို အင်တာနက်မှတစ်ဆင့် Over-The-Air (OTA) အလိုအလျောက် Update ပြုလုပ်နည်း အပြည့်အစုံ လမ်းညွှန်ချက် ဖြစ်ပါသည်။

---

## ၁။ အခြေအနေ ၃ မျိုး (Three Update Scenarios)

| အခြေအနေ | ပြုလုပ်ပုံ | User ဘက်မှ Download ဆွဲရမည့် Size |
|---|---|---|
| **Scenario A: ဖိုင် ၁ ခုတည်း အသေးစားပြင်ဆင်ခြင်း (Granular Single-File Patch)** <br> *(ဉပမာ- `n4_lesson_52.json` စာလုံးပေါင်း/သဒ္ဒါပြင်ခြင်း)* | ပြင်ထားသော json ဖိုင်ကို `patches/` အောက်သို့ ထည့်ပြီး `version.json` တွင် `updated_files` ၌ ထည့်ပေးခြင်း | **~20 KB - ~60 KB သာ** (၉၉% ဒေတာ သက်သာသည်) |
| **Scenario B: N4 ကာတွန်းရုပ်ပြ အသစ်များ လဲလှယ်ခြင်း (Illustration Pack Update)** <br> *(ကာတွန်းပုံအသစ်များ ထည့်သွင်းခြင်း)* | WebP zip အသစ်ကို Release တင်ပြီး `version.json` တွင် `n4_images_version` တိုးပေးခြင်း | **~3 MB** |
| **Scenario C: ဒေတာဘေ့စ်တစ်ခုလုံး ဗားရှင်းအသစ် လဲလှယ်ခြင်း (Major Content Release)** <br> *(သင်ခန်းစာ အသစ်များစွာ ထပ်တိုးခြင်း)* | `content.seed` အသစ်ကို Release တင်ပြီး `version.json` တွင် `content_version` တိုးပေးခြင်း | **~7.6 MB** |

---

## ၂။ Scenario A: JSON ဖိုင် တစ်ခုတည်း သီးသန့် Update လုပ်နည်း (အသုံးအများဆုံး)

ဉပမာ- `n4_lesson_52.json` (သို့မဟုတ် `speaking.json` သို့မဟုတ် `beginnervocabulary.json`) ထဲတွင် စာလုံးပေါင်း မှားယွင်းမှု သို့မဟုတ် သဒ္ဒါရှင်းလင်းချက် အသစ်တစ်ခု ပြင်ဆင်လိုက်သည်ဆိုပါစို့။

### အဆင့် ၁: ပြင်ဆင်ထားသော ဖိုင်ကို `patches/` ထဲ ကူးထည့်ပါ
```bash
# ပြင်ပြီးသား json ဖိုင်ကို canolia-assets/patches/ အောက်သို့ ကူးထည့်ပါ
copy "C:\Users\EBPMyanmar\AndroidStudioProjects\Canolia-Kodomo\app\shared\src\commonMain\seedJson\n4_lesson_52.json" "C:\Users\EBPMyanmar\AndroidStudioProjects\canolia-assets\patches\n4_lesson_52.json"
```

### အဆင့် ၂: `version.json` တွင် `updated_files` ကို ဖြည့်စွက်ပါ
`version.json` ဖိုင်ကို ဖွင့်ပြီး အောက်ပါအတိုင်း ထည့်ပေးပါ (version ကို လက်ရှိထက် +1 တိုးပါ၊ ဉပမာ version: 2):

```json
{
  "content_version": 1,
  "content_seed_url": "https://github.com/mimi22-oss/canolia-assets/releases/download/v1.0.0/content.seed",
  "content_seed_size": 7996014,
  "n4_images_version": 1,
  "n4_images_url": "https://github.com/mimi22-oss/canolia-assets/releases/download/v1.0.0/n4_offline_pack.zip",
  "n4_images_size": 3224881,
  "updated_at": "2026-10-06",
  "notes_mm": "Lesson 52 စာလုံးပေါင်းနှင့် ရှင်းလင်းချက် ပြင်ဆင်ထားပါသည်။",
  "notes_en": "Updated Lesson 52 grammar explanations and typo fixes.",
  "updated_files": [
    {
      "file_name": "n4_lesson_52.json",
      "url": "https://raw.githubusercontent.com/mimi22-oss/canolia-assets/main/patches/n4_lesson_52.json",
      "version": 2,
      "size": 42000,
      "description_mm": "Lesson 52 သဒ္ဒါရှင်းလင်းချက်နှင့် စာလုံးပေါင်း အမှားပြင်ဆင်ချက်",
      "description_en": "Lesson 52 grammar explanation and typo fixes"
    }
  ]
}
```

> **မှတ်ချက်:** `url` ကို ချန်ထားခဲ့ပါကလည်း App မှ `https://raw.githubusercontent.com/mimi22-oss/canolia-assets/main/patches/{file_name}` သို့ အလိုအလျောက် ချိတ်ဆက် ဒေါင်းလုဒ် ဆွဲပေးပါသည်။

### အဆင့် ၃: Git Commit & Push ပြုလုပ်ပါ
```bash
cd C:\Users\EBPMyanmar\AndroidStudioProjects\canolia-assets
git add patches/ version.json
git commit -m "update: add patch for n4_lesson_52.json v2"
git push origin main
```
✅ **ပြီးပါပြီ!** App သုံးစွဲသူများသည် Settings Screen သို့မဟုတ် Textbook Screen တွင် "⚡ ပြင်ဆင်ထားသော ဖိုင်သာ ရယူမည် (~42 KB)" ဆိုသည့် ခလုတ်ကို တွေ့မြင်ရပြီး စက္ကန့်ပိုင်းအတွင်း Update ရရှိသွားပါမည်။

---

## ၃။ Scenario B: N4 ကာတွန်းရုပ်ပြ အသစ်များ (WebP Pack) Update လုပ်နည်း

1. `Canolia-Kodomo` root တွင် ရုပ်ပြဇာတ်ကွက် zip ထုတ်ပါ:
   ```bash
   python scripts/build_n4_offline_pack.py
   ```
2. ထွက်လာသော `dist/n4_offline_pack.zip` ကို `canolia-assets` တွင် release တင်ပါ သို့မဟုတ် commit ပြုလုပ်ပါ။
3. `version.json` တွင် `n4_images_version` ကို လက်ရှိထက် ၁ တိုးပါ:
   ```json
   "n4_images_version": 2,
   "n4_images_url": "https://github.com/mimi22-oss/canolia-assets/releases/download/v1.0.0/n4_offline_pack.zip"
   ```
4. Git commit & push ပြုလုပ်ပါ။
✅ App တွင် "✨ N4 ရုပ်ပုံအသစ်များ ထွက်ရှိပါသည် (v2)" ဟု Banner ပေါ်လာပါမည်။

---

## ၄။ Scenario C: ဒေတာဘေ့စ်တစ်ခုလုံး ဗားရှင်းအသစ် လဲလှယ်ခြင်း (Major Version)

1. `content.seed` ကို အသစ်ထုတ်လုပ်ပါ:
   ```bash
   ./gradlew :app:shared:generateContentSeed
   ```
2. ထွက်လာသော `content.seed` ကို `scripts/publish_github_release.py` သုံး၍ Release သို့ တင်ပါ။
3. `version.json` တွင် `content_version` ကို ၁ တိုးပါ:
   ```json
   "content_version": 2,
   "content_seed_url": "https://github.com/mimi22-oss/canolia-assets/releases/download/v2.0.0/content.seed"
   ```
4. Git commit & push ပြုလုပ်ပါ။

---

## ၅။ စက်တွင်း သိမ်းဆည်းသည့် တည်နေရာများ (Storage Directory Layout)

- **Desktop (Windows/Mac/Linux)**:
  `~/.canolia-kodomo/overrides/`
  - `overrides/n4_lesson_52.json` (ဒေါင်းလုဒ်ဆွဲထားသော patched file)
  - `overrides/n4_lesson_52.json.version` (ဗားရှင်းမှတ်တမ်းဖိုင်)
  - `packs/n4/` (WebP ရုပ်ပြပုံများ)
- **Android**:
  `context.filesDir/overrides/`
  - `overrides/n4_lesson_52.json`
  - `overrides/n4_lesson_52.json.version`
  - `packs/n4/` (WebP ရုပ်ပြပုံများ)
- **iOS**:
  `NSDocumentDirectory/overrides/`
