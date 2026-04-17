# 🌐 Use Machine Learning APIs on Google Cloud: Challenge Lab || GSP329 🚀 [![Open Lab](https://img.shields.io/badge/Open-Lab-blue?style=flat)](https://www.cloudskillsboost.google/course_templates/630/labs/580206)

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
curl -LO raw.githubusercontent.com/DrVelu/Arcade-Google-Cloud-Labs/refs/heads/main/Use%20Machine%20Learning%20APIs%20on%20Google%20Cloud%3A%20Challenge%20Lab/DrVelu.sh
sudo chmod +x DrVelu.sh 
./DrVelu.sh
```
```bash
export PROJECT_ID=$(gcloud config get-value project)
export SA_EMAIL=$(gcloud iam service-accounts list --filter="NOT email ~ .*@developer.gserviceaccount.com" --format="value(email)" | head -n 1)

echo "Using Service Account: $SA_EMAIL"
```
```bash
export GOOGLE_APPLICATION_CREDENTIALS=$(pwd)/credentials.json
gsutil cp gs://$PROJECT_ID/analyze-images-v2.py .
```
 > TBD: Create a Vision API image object called image_object
```bash
image_object = vision.Image(content=file_content)
response = vision_client.text_detection(image=image_object)
```
 > TBD: According to the target language pass the description data to the translation API
```bash
translation = translate_client.translate(desc, target_language='en')
```
```bash
export PROJECT_ID=$(gcloud config get-value project)

gcloud projects add-iam-policy-binding $PROJECT_ID \
    --member="serviceAccount:$SA_EMAIL" \
    --role="roles/serviceusage.serviceUsageConsumer"
```
```bash
gcloud iam service-accounts keys create credentials.json \
    --iam-account=$SA_EMAIL

export GOOGLE_APPLICATION_CREDENTIALS=$(pwd)/credentials.json
python3 analyze-images-v2.py $PROJECT_ID $PROJECT_ID
```
```bash
bq query --use_legacy_sql=false \
'SELECT locale, COUNT(locale) as lcount 
FROM `image_classification_dataset.image_text_detail` 
GROUP BY locale 
ORDER BY lcount DESC'
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
