# 🌐 Encrypt a Persistent Disk with a Customer-Supplied Key 🚀 [![Open Lab](https://img.shields.io/badge/Open-Lab-blue?style=flat)](https://www.skills.google/games/7008/labs/43562)

## ⚠️ Disclaimer ⚠️

<blockquote style="background-color: #fffbea; border-left: 6px solid #f7c948; padding: 1em; font-size: 15px; line-height: 1.5;">
  <strong>Educational Purpose Only:</strong> This script and guide are provided for the educational purposes to help you understand the lab services and boost your career.Before using the script, please open and review it to familiarize yourself with Google Cloud services.
  <br><br>
  <strong>Terms Compliance:</strong> Always ensure compliance with Qwiklabs' terms of service and YouTube's community guidelines. The aim is to enhance your learningexperience — not to circumvent it.
</blockquote>

---

<div style="padding: 15px; margin: 10px 0;">

<img src="https://media1.tenor.com/m/79-NWuqFZ28AAAAd/welcome-bhaisahab-ye-kis-line-me-aa-gaye-aap.gif" >

## ☁️ Run in Cloud Shell:

```bash
export PROJECT_ID=$(gcloud config get-value project) ZONE=$(gcloud compute instances list --limit=1 --format="value(zone)") VM_NAME=$(gcloud compute instances list --limit=1 --format="value(name)") BASE64_KEY=$(head -c 32 /dev/urandom | base64)
gcloud compute disks create csek-encrypted-disk --size=200GB --zone=$ZONE --csek-key-file=<(echo "[{\"uri\": \"https://www.googleapis.com/compute/v1/projects/$PROJECT_ID/zones/$ZONE/disks/csek-encrypted-disk\", \"key\": \"$BASE64_KEY\", \"key-type\": \"raw\"}]")
gcloud compute instances attach-disk $VM_NAME --disk=csek-encrypted-disk --zone=$ZONE --csek-key-file=<(echo "[{\"uri\": \"https://www.googleapis.com/compute/v1/projects/$PROJECT_ID/zones/$ZONE/disks/csek-encrypted-disk\", \"key\": \"$BASE64_KEY\", \"key-type\": \"raw\"}]")
## Thala For A Reason😂
```

</div>

---
## 🎉 **Congratulations! Lab Completed Successfully!** 🏆

<div style="text-align:center; padding: 10px 0; max-width: 640px; margin: 0 auto;">
  <h3 style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin-bottom: 14px;">📱 Join the DrVelu Community</h3>
  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="YouTube Channel">
  </a>
  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="LinkedIn Profile">
  </a>
  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="Telegram Channel">
  </a>
  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="Instagram Profile">
  </a>
</div>

---

<div align="center">
  <p style="font-size: 12px; color: #586069;">
    <em>This guide is provided for educational purposes. Always follow Qwiklabs terms of service and YouTube's community guidelines.</em>
  </p>
  <p style="font-size: 12px; color: #586069;">
    <em>Last updated: January 2026</em>
  </p>
</div>
