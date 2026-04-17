# 🌐 Interacting with Vault Policies || GSP1004 🚀 [![Open Lab](https://img.shields.io/badge/Open-Lab-blue?style=flat)](https://www.skills.google/games/6959/labs/43212)

## ⚠️ Disclaimer ⚠️

<blockquote style="background-color: #fffbea; border-left: 6px solid #f7c948; padding: 1em; font-size: 15px; line-height: 1.5;">
  <strong>Educational Purpose Only:</strong> This script and guide are provided for the educational purposes to help you understand the lab services and boost your career. Before using the script, please open and review it to familiarize yourself with Google Cloud services.
  <br><br>
  <strong>Terms Compliance:</strong> Always ensure compliance with Qwiklabs' terms of service and YouTube's community guidelines. The aim is to enhance your learning experience — not to circumvent it.
</blockquote>

---

<div style="padding: 15px; margin: 10px 0;">

## ☁️ Run in Cloud Shell:

```bash
curl -LO raw.githubusercontent.com/DrVelu/Arcade-Google-Cloud-Labs/refs/heads/main/Interacting%20with%20Vault%20Policies/DrVelu1.sh
sudo chmod +x DrVelu1.sh 
./DrVelu1.sh
```

## ⚠️Open New Cloud Shell Tab

```bash
run() {
  echo -e "\n\033[1;36m▶ $*\033[0m"
  "$@"
  echo -e "\n\033[1;33mPress ENTER to continue...\033[0m"
  read
}

export VAULT_ADDR='http://127.0.0.1:8200'
run vault status
printf "\033[1;32mEnter Vault Token: \033[0m"
read -s ROOT_TOKEN
echo
run vault login token="$ROOT_TOKEN"
run vault secrets list
run vault auth enable userpass
run vault write auth/userpass/users/example-user password='password!'
run vault login -method=userpass username=example-user password='password!'
run vault secrets list
echo -e "\n\033[1;32mAll commands completed. Shell will stay open.\033[0m"
exec bash

```
## 👉Create Policy `demo-policy`
```bash
path "sys/mounts" {
    capabilities = ["read"]
}
```
## 👉Generated Token's Policies `demo-policy`

```bash
run() {
  echo -e "\n\033[1;36m▶ $*\033[0m"
  "$@"
  echo -e "\n\033[1;33mPress ENTER to continue...\033[0m"
  read
}

run vault secrets list
run vault login -method=userpass username=example-user password='password!'
run vault secrets list
printf "\033[1;32mEnter Vault Token: \033[0m"
read -s YOUR_TOKEN
echo
run vault token capabilities "$YOUR_TOKEN" sys/mounts
run vault token capabilities "$YOUR_TOKEN" sys/policies/acl
run vault policy list

```
## 👉Edit Policy `demo-policy`
```bash
path "sys/policies/acl" {
    capabilities = ["read", "list"]
}
```

```bash
run() {
  echo -e "\n\033[1;36m▶ $*\033[0m"
  "$@"
  echo -e "\n\033[1;33mPress ENTER to continue...\033[0m"
  read
}

run vault policy list
vault policy list > policies.txt
echo "policies.txt created"
run vault token capabilities "$YOUR_TOKEN" sys/policies/acl
vault token capabilities "$YOUR_TOKEN" sys/policies/acl > token_capabilities.txt
echo "token_capabilities.txt created"
export PROJECT_ID=$(gcloud config get-value project)
run gsutil cp policies.txt token_capabilities.txt "gs://$PROJECT_ID"
```


```bash
curl -LO raw.githubusercontent.com/DrVelu/Arcade-Google-Cloud-Labs/refs/heads/main/Interacting%20with%20Vault%20Policies/DrVelu2.sh
sudo chmod +x DrVelu2.sh 
./DrVelu2.sh
```

## 👉Create the admin policies: Watch Video

```bash
curl -LO raw.githubusercontent.com/DrVelu/Arcade-Google-Cloud-Labs/refs/heads/main/Interacting%20with%20Vault%20Policies/DrVelu3.sh
sudo chmod +x DrVelu3.sh 
./DrVelu3.sh
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
    <em>Last updated: December 2025</em>
  </p>
</div>
