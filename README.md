# Canolia Assets

Official downloadable offline asset packages for the **Canolia Kodomo** Japanese learning app.

## Available Offline Packs

| Pack | Content | Format | Size | Download |
|---|---|---|---|---|
| **N4 Illustrations Pack** | Minna No Nihongo N4 Lesson Illustrations (211 cartoon images) | WebP | 5.43 MB | [Download ZIP](n4_offline_pack.zip) |
| **N4 Textbook Scans Pack** *(Optional)* | Minna No Nihongo N4 Original Textbook Page Scans (310 pages) | WebP | 25.27 MB | [Download ZIP](n4_scans_pack.zip) |

### Releases & OTA Updates
- Download assets from the [GitHub Releases](https://github.com/mimi22-oss/canolia-assets/releases) tab.
- For complete instructions on how to push granular JSON patches or update illustrations and original pages, see [HOW_TO_UPDATE.md](HOW_TO_UPDATE.md).
- Original full-resolution textbook PNG scans are also tracked in [`original_pages/by_lesson/`](original_pages/by_lesson/).

---

## 🧹 Local Cache ရှင်းလင်းနည်း (Clearing Local App Cache)

App တွင်းသို့ အသစ် download ဆွဲယူမှုများကို ပြန်လည်စမ်းသပ်ရန် သို့မဟုတ် စက်တွင်း သိမ်းဆည်းထားသော cache ပုံများကို ရှင်းလင်းရန် အောက်ပါ command များဖြင့် ဖျက်နိုင်ပါသည်-

### Windows (PowerShell)
```powershell
# ၁။ Download ဆွဲထားသော ရုပ်ပြနှင့် စာအုပ်စကင် packs အားလုံးကို ရှင်းလင်းရန်:
Remove-Item -Path "$HOME\.canolia-kodomo\packs" -Recurse -Force

# သို့မဟုတ် သီးသန့် တစ်ခုချင်းစီ ရှင်းလင်းရန်:
Remove-Item -Path "$HOME\.canolia-kodomo\packs\n4" -Recurse -Force        # ကာတွန်းရုပ်ပြ pack သာ ရှင်းရန်
Remove-Item -Path "$HOME\.canolia-kodomo\packs\n4_scans" -Recurse -Force  # မူရင်းစာအုပ်စကင် pack သာ ရှင်းရန်

# ၂။ App Cache အားလုံး (JSON overrides အပါအဝင်) လုံးဝရှင်းလင်းရန်:
Remove-Item -Path "$HOME\.canolia-kodomo" -Recurse -Force
```

### Windows (Command Prompt - CMD)
```cmd
rmdir /s /q "%USERPROFILE%\.canolia-kodomo\packs"
```

### macOS / Linux
```bash
# Download ဆွဲထားသော pack များ ရှင်းလင်းရန်
rm -rf ~/.canolia-kodomo/packs

# Cache အားလုံး လုံးဝရှင်းလင်းရန်
rm -rf ~/.canolia-kodomo
```

### Android
Settings -> Apps -> **Canolia Kodomo** -> Storage -> **Clear Storage / Clear Cache** ပြုလုပ်နိုင်ပါသည်။

