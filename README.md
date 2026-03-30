Ada 👍 — dan gue kasih yang **paling simpel & anti ribet (1 jalur lurus)**
Tanpa mikir banyak config.

---

# 🚀 🔥 CARA PALING MUDAH MIGRASI VPS

## 🧠 Intinya cuma 3 langkah:

```bash
UPLOAD → EXTRACT → RUN
```

---

# 🥇 STEP BY STEP (versi paling gampang)

## ✅ 1. Buat VPS baru

* beli VPS baru (AWS / DO / dll)
* login SSH (pakai terminal atau WinSCP)

---

## ✅ 2. Upload file backup (yang tadi)

Di WinSCP:
👉 drag file:

```bash
openclaw-backup.tar.gz
``

ke:

```bash
/home/ubuntu/
```

---

## ✅ 3. Extract (ini kunci)

Di VPS baru:

```bash
cd ~
tar -xzvf openclaw-backup.tar.gz
```

👉 otomatis jadi:

```bash
~/.openclaw/
```

---

## ✅ 4. Fix permission (WAJIB)

```bash
sudo chown -R ubuntu:ubuntu ~/.openclaw
```

---

## ✅ 5. Install OpenClaw (kalau belum ada)

Kalau belum install:

```bash
curl -fsSL https://... (script install openclaw kamu)
```

(atau pakai cara install yang dulu kamu pakai)

---

## ✅ 6. Jalankan

```bash
openclaw start
```

atau:

```bash
openclaw gateway
```

---

# 🎯 SELESAI 🎉

👉 agent kamu langsung hidup lagi
👉 memory, config, semua balik

---

# ⚠️ Hal yang sering bikin gagal

## ❌ 1. API KEY hilang

Cek:

```bash
nano ~/.openclaw/openclaw.json
```

---

## ❌ 2. Port belum dibuka

* buka port 22 (SSH)
* kalau pakai API → buka juga port lain

---

## ❌ 3. Belum install dependency

Kadang perlu:

```bash
npm install
```

atau

```bash
pip install -r requirements.txt
```

---

# 🔥 BONUS (cara super cepat ala pro)

Kalau mau lebih simpel lagi:

👉 di VPS baru langsung:

```bash
scp openclaw-backup.tar.gz ubuntu@IP:/home/ubuntu/
```

---

# 💡 INTINYA

👉 kamu gak perlu setup ulang dari nol
👉 cukup pindahin folder:

```bash
~/.openclaw
```

---

# 🚀 NEXT LEVEL (kalau mau)

Urutannya begini:

**install OpenClaw dulu, baru upload backup, baru restore backup.**

Jangan restore dulu sebelum OpenClaw terpasang.

Ini step-by-step yang aman.

## 1. Siapkan VPS baru

Login ke VPS baru dulu.

```bash
ssh ubuntu@IP_VPS_BARU
```

Kalau perlu update:

```bash
sudo apt update && sudo apt upgrade -y
```

## 2. Install OpenClaw di VPS baru

Pakai cara install yang dulu kamu pakai.

Kalau installer minta:

* model
* API key
* Telegram token

isi saja dulu seperlunya. Itu cuma config awal sementara.

Setelah install selesai, cek dulu command OpenClaw sudah ada. Misalnya:

```bash
which openclaw
```

atau kalau setup kamu pakai gateway:

```bash
which openclaw-gateway
```

## 3. Stop OpenClaw dulu

Sebelum restore backup, matikan dulu service-nya supaya file config tidak bentrok.

Kalau ada command stop:

```bash
openclaw stop
```

Kalau pakai service systemd, biasanya:

```bash
sudo systemctl stop openclaw
```

Kalau nama servicenya beda, nanti sesuaikan.

## 4. Upload file backup ke VPS baru

Di laptop kamu, buka WinSCP dan connect ke **VPS baru**.

Masuk ke folder kanan:

```bash
/home/ubuntu/
```

Lalu dari kiri, drag file ini ke kanan:

```bash
openclaw-backup.tar.gz
```

Jadi ya, **file backup harus dipindahkan dulu ke VPS baru** sebelum kamu jalankan perintah extract.

## 5. Cek file backup sudah masuk

Di terminal VPS baru:

```bash
cd ~
ls -lh
```

Pastikan ada file:

```bash
openclaw-backup.tar.gz
```

## 6. Hapus config sementara bawaan install

Baru sekarang jalankan:

```bash
rm -rf ~/.openclaw
```

Ini menghapus config sementara hasil install awal.

## 7. Extract backup kamu

Lalu jalankan:

```bash
tar -xzvf openclaw-backup.tar.gz -C ~/
```

Ini akan membuat kembali folder:

```bash
~/.openclaw
```

## 8. Rapikan permission

Jalankan:

```bash
sudo chown -R ubuntu:ubuntu ~/.openclaw
```

## 9. Jalankan OpenClaw lagi

Sekarang start lagi.

Kalau pakai command:

```bash
openclaw start
```

Kalau pakai service:

```bash
sudo systemctl start openclaw
```

## 10. Cek apakah sudah jalan

Cek status:

```bash
openclaw status
```

atau:

```bash
ps aux | grep openclaw
```

## 11. Tes bot Telegram

Coba chat bot kamu. Kalau config dari backup terbaca dengan benar, biasanya langsung hidup lagi.

---

Jadi urutan pendeknya:

1. login ke VPS baru
2. install OpenClaw
3. stop OpenClaw
4. upload `openclaw-backup.tar.gz` ke `/home/ubuntu/`
5. hapus `~/.openclaw`
6. extract backup
7. set permission
8. start lagi OpenClaw

---

Supaya lebih gampang, ini versi copy-paste setelah file backup sudah ter-upload ke VPS baru:

```bash
cd ~
ls -lh
rm -rf ~/.openclaw
tar -xzvf openclaw-backup.tar.gz -C ~/
sudo chown -R ubuntu:ubuntu ~/.openclaw
```

Setelah itu start lagi OpenClaw.

Kalau kamu mau, kirim cara install OpenClaw yang kamu pakai di VPS lama, nanti gue urutin lagi versi yang benar-benar cocok sama setup kamu.

