# 🌐 Scaling Microservices Applications: Migration to Redis Enterprise on Google Cloud || GSP1177 🚀 [![Open Lab](https://img.shields.io/badge/Open-Lab-blue?style=flat)](https://www.cloudskillsboost.google/games/6512/labs/40877)

## ⚠️ Disclaimer ⚠️

<blockquote style="background-color: #fffbea; border-left: 6px solid #f7c948; padding: 1em; font-size: 15px; line-height: 1.5;">
  <strong>Educational Purpose Only:</strong> This script and guide are provided for the educational purposes to help you understand the lab services and boost your career. Before using the script, please open and review it to familiarize yourself with Google Cloud services.
  <br><br>
  <strong>Terms Compliance:</strong> Always ensure compliance with Qwiklabs' terms of service and YouTube's community guidelines. The aim is to enhance your learning experience — not to circumvent it.
</blockquote>

---

<div style="padding: 15px; margin: 10px 0;">

## ℹ️Perforn below 2 tasks only when you get `timeout error` else simply run the script

### Open `Editor` in cloud shell

<h3>
  Navigate- terraform/ modules/ gke-cluster/ main.tf
</h3>
  
```bash
timeouts {
  create = "10m"
  update = "10m"
  delete = "10m"
}
```
### Create `providers.tf` in gcp-microservices-demo-quicklabs if not existed

```bash
provider "google" {
  project = var.gcp_project_id
  region  = var.gcp_region
}

```

---
## ☁️ Run in Cloud Shell:

```bash
curl -LO raw.githubusercontent.com/DrVelu/Arcade-Google-Cloud-Labs/refs/heads/main/Scaling%20Microservices%20Applications%3A%20Migration%20to%20Redis%20Enterprise%20on%20Google%20Cloud/DrVelu.sh
sudo chmod +x DrVelu.sh 
./DrVelu.sh
```

</div>

---

## 🎉 **Congratulations! Lab Completed Successfully!** 🏆  

<div align="center" style="padding: 5px;">
  <h3>📱 Join the DrVelu Community</h3>
  
  <a href="#">
    <img src="#" alt="YouTube Channel">
  </a>
  &nbsp;
  <a href="#">
    <img src="#" alt="LinkedIn">
</a>


</div>

---

<div align="center">
  <p style="font-size: 12px; color: #586069;">
    <em>This guide is provided for educational purposes. Always follow Qwiklabs terms of service and YouTube's community guidelines.</em>
  </p>
  <p style="font-size: 12px; color: #586069;">
    <em>Last updated: May 2025</em>
  </p>
</div>
