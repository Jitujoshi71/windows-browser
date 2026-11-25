# Windows Desktop in Browser

GitHub Actions par ek Windows machine chalao aur uska desktop **seedha browser me** kholo — koi Remote Desktop app, koi Tailscale install nahi chahiye.

Kaise kaam karta hai: **TightVNC** desktop serve karta hai → **noVNC** use web page bana deta hai → **Cloudflare Tunnel** use ek public `https://*.trycloudflare.com` link deta hai. Link kholo, Connect dabao, password daalo — desktop saamne.

## Setup (ek baar)

1. Repo ke **Settings → Secrets and variables → Actions → New repository secret** me jao.
2. Naam: `VNC_PASSWORD`, value: apna password — **6 se 8 characters, sirf letters aur digits** (VNC sirf pehle 8 characters use karta hai).
3. Bas. Password kabhi code me ya kisi ko share mat karo.

## Chalana

1. Repo ke **Actions** tab me jao → **Windows Desktop in Browser** workflow → **Run workflow**.
2. 1–2 minute me run ke **Summary** page par aur logs me link aa jayega — kuch is tarah:
   `https://abc-def-123.trycloudflare.com/vnc.html?autoconnect=true&resize=scale`
3. Link browser me (phone ya laptop, koi bhi) kholo → **Connect** dabao → `VNC_PASSWORD` daalo.

## Yaad rakhne wali baatein

- **6 ghante ki limit:** machine zyada se zyada 6 ghante chalti hai, phir run apne aap band ho jata hai. Dobara chalane par **naya link** banta hai.
- **Free minutes:** GitHub free account me mahine ke 2,000 Actions minutes milte hain. Windows runner 2x rate par chalta hai, to ek poora 6-ghante ka run lagbhag **720 minutes** khata hai.
- **Security:** link har run par random banta hai, aur desktop sirf `VNC_PASSWORD` se khulta hai. Link kisi ke saath share mat karo, aur is password ko apne kisi important account ke password jaisa mat rakho — VNC ka password system purana aur kamzor hai, ye sirf is temporary machine ke liye hai.
- **Data save nahi hota:** run khatam hote hi machine delete ho jati hai. Jo file chahiye, use run chalte hue download kar lo.
- Workflow khud bhi check karta hai: VNC login test pass hue bina link nahi banta, to dead link milne ka chance nahi.

## Iske jaisa purana repo

[`Jitujoshi71/windows`](https://github.com/Jitujoshi71/windows) — wahi Windows machine, par Remote Desktop app + Tailscale se khulti hai. Ye repo usi ka browser wala version hai.
