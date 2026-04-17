# 🌐 Looker Functions and Operators || GSP857 🚀 [![Open Lab](https://img.shields.io/badge/Open-Lab-blue?style=flat)](https://www.skills.google/games/6879/labs/42739)

## ⚠️ Disclaimer ⚠️

<blockquote style="background-color: #fffbea; border-left: 6px solid #f7c948; padding: 1em; font-size: 15px; line-height: 1.5;">
  <strong>Educational Purpose Only:</strong> This script and guide are provided for the educational purposes to help you understand the lab services and boost your career. Before using the script, please open and review it to familiarize yourself with Google Cloud services.
  <br><br>
  <strong>Terms Compliance:</strong> Always ensure compliance with Qwiklabs' terms of service and YouTube's community guidelines. The aim is to enhance your learning experience — not to circumvent it.
</blockquote>

---

<div style="padding: 15px; margin: 10px 0;">

## Look-1 `Pivot dimensions`:

```bash
# Place in `faa` model
explore: +flights {
  query: DrVelu-1{
      dimensions: [depart_week, distance_tiered]
      measures: [count]
      filters: [flights.depart_date: "2003"]
    }
  }
```
Title the Look `Flight Count by Departure Week and Distance Tier`

## Look-2 Reorder columns and remove fields
```bash
# Place in `faa` model
explore: +flights {
  query: DrVelu-2{
      dimensions: [aircraft_origin.state]
      measures: [percent_cancelled]
      filters: [flights.depart_date: "2000"]
    }
  }
```
Title the Look `Percent of Flights Cancelled by State in 2000`

## Look-3 Update Use table calculations to calculate simple percentages
```bash
# Place in `faa` model
explore: +flights {
    query: DrVelu-3{
      dimensions: [aircraft_origin.state]
      measures: [cancelled_count, count]
      filters: [flights.depart_date: "2004"]
    }
}
```
```bash
${flights.cancelled_count}/${flights.count}
```
Title the Look `Percent of Flights Cancelled by Aircraft Origin 2004`

## Look-4 Use table calculations to calculate percentages of a total
```bash
# Place in `faa` model
explore: +flights {
    query: DrVelu-4{
      dimensions: [carriers.name]
      measures: [total_distance]
    }
}
```
```bash
${flights.total_distance}/${flights.total_distance:total}
```
Title the Look `Percent of Total Distance Flown by Carrier`

## Look-5 Use functions in table calculations
```bash
# Place in `faa` model
explore: +flights {
    query: DrVelu-5{
      dimensions: [depart_year, distance_tiered]
      measures: [count]
      filters: [flights.depart_date: "after 2000/01/01"]
    }
}
```
```bash
(${flights.count}-pivot_offset(${flights.count}, -1))/pivot_offset(${flights.count}, -1)
```
Title the Look `YoY Percent Change in Flights flown by Distance, 2000-Present`

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
    <em>Last updated: November 2025</em>
  </p>
</div>
