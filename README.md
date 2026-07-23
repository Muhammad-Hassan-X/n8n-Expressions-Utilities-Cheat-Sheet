# 📘 n8n Expressions & Utilities Cheat Sheet

This document contains the most useful expressions, JavaScript snippets, IDs, timestamps, and helper commands that can be reused across all n8n workflows.

---

# 📅 Date & Time

## Current Date & Time (Pakistan)

```javascript
{{ $now.setZone('Asia/Karachi').toFormat('dd MMM yyyy, hh:mm a') }}
```

Output

```
23 Jul 2026, 09:30 PM
```

---

## ISO Timestamp

```javascript
{{ $now.toISO() }}
```

Output

```
2026-07-23T16:30:25.562+05:00
```

---

## Readable Date

```javascript
{{ $now.toFormat('dd MMM yyyy') }}
```

Output

```
23 Jul 2026
```

---

## Readable Time

```javascript
{{ $now.toFormat('hh:mm a') }}
```

Output

```
09:30 PM
```

---

## 24 Hour Time

```javascript
{{ $now.toFormat('HH:mm:ss') }}
```

Output

```
21:30:20
```

---

## Day Name

```javascript
{{ $now.toFormat('cccc') }}
```

Output

```
Thursday
```

---

## Month Name

```javascript
{{ $now.toFormat('LLLL') }}
```

Output

```
July
```

---

## Unix Timestamp

```javascript
{{ Math.floor(Date.now() / 1000) }}
```

Output

```
1784823002
```

---

# 🆔 Random IDs

## Random Workflow ID

```javascript
ID-{{ Math.random().toString(36).substring(2,10) }}
```

Output

```
ID-f82jd9qa
```

---

## Long Random ID

```javascript
ID-{{ Math.random().toString(36).substring(2,10) }}-{{ Math.random().toString(36).substring(2,10) }}
```

Output

```
ID-g83jh2kd-a83jsh91
```

---

## UUID (Code Node)

```javascript
crypto.randomUUID()
```

Output

```
8dba0f7d-c1d2-4dd1-b8f5-65d41f807b51
```

---

# 🔢 Numbers

## Random Number

```javascript
{{ Math.floor(Math.random()*10000) }}
```

---

## Random 6 Digit Number

```javascript
{{ Math.floor(100000 + Math.random()*900000) }}
```

Output

```
582194
```

---

# 🔤 String Helpers

## Uppercase

```javascript
{{ $json.name.toUpperCase() }}
```

---

## Lowercase

```javascript
{{ $json.name.toLowerCase() }}
```

---

## Trim Spaces

```javascript
{{ $json.name.trim() }}
```

---

## Replace Text

```javascript
{{ $json.title.replace('AI','Automation') }}
```

---

# 📄 JSON Helpers

## Entire JSON

```javascript
{{ JSON.stringify($json) }}
```

---

## Pretty JSON

```javascript
{{ JSON.stringify($json,null,2) }}
```

---

## Parse JSON

```javascript
{{ JSON.parse($json.response) }}
```

---

# 📂 Previous Node Data

## Whole JSON

```javascript
{{ $('Merge').item.json }}
```

---

## Specific Field

```javascript
{{ $('Merge').item.json.Content }}
```

---

## Nested Field

```javascript
{{ $('Merge').item.json.value.document }}
```

---

# 🌐 Current Workflow

## Workflow Name

```javascript
{{ $workflow.name }}
```

---

## Workflow ID

```javascript
{{ $workflow.id }}
```

---

# ⚙️ Execution

## Execution ID

```javascript
{{ $execution.id }}
```

---

## Execution Mode

```javascript
{{ $execution.mode }}
```

---

# 📝 Discord Embed Fields

## Workflow

```javascript
{{ $workflow.name }}
```

---

## Status

```javascript
Success
```

---

## Current Time

```javascript
{{ $now.setZone('Asia/Karachi').toFormat('dd MMM yyyy, hh:mm a') }}
```

---

## Execution ID

```javascript
{{ $execution.id }}
```

---

## Random Event ID

```javascript
ID-{{ Math.random().toString(36).substring(2,10) }}
```

---

# 🔗 Useful LinkedIn Values

## Person URN

```
urn:li:person:YOUR_PERSON_ID
```

---

## Document URN

```
urn:li:document:YOUR_DOCUMENT_ID
```

---

## Organization URN

```
urn:li:organization:YOUR_ORG_ID
```

---

# 📚 HTTP Headers

## LinkedIn API

```
LinkedIn-Version: 202601
Content-Type: application/json
```

---

## PDF Upload

```
Content-Type: application/pdf
```

---

# 🔐 Common Authorization

Bearer Token

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

---

API Key

```
Authorization: YOUR_API_KEY
```

---

# 📌 Cron Expressions

## Every Day at Midnight

```
0 0 * * *
```

---

## Every Hour

```
0 * * * *
```

---

## Every 30 Minutes

```
*/30 * * * *
```

---

## Every Monday at 9 AM

```
0 9 * * 1
```

---

# 🚀 Useful JavaScript (Code Node)

## Generate UUID

```javascript
return [{
  json:{
    id: crypto.randomUUID()
  }
}]
```

---

## Current Timestamp

```javascript
return [{
  json:{
    timestamp: Date.now()
  }
}]
```

---

## Random ID

```javascript
return [{
  json:{
    id:"ID-"+Math.random().toString(36).substring(2,10)
  }
}]
```

---

## Success Response

```javascript
return [{
  json:{
    success:true,
    message:"Workflow completed successfully."
  }
}]
```

---

# 📌 Common Status Values

```
Success
Failed
Running
Completed
Cancelled
Warning
Retrying
Published
Draft
Archived
```

---

# 🎨 Discord Colors

## Green

```
5763719
```

## Red

```
15548997
```

## Blue

```
3447003
```

## Yellow

```
16776960
```

## Orange

```
15105570
```

## Purple

```
10181046
```

---

# 💡 Best Practice

For every production workflow, include:

- Workflow Name
- Execution ID
- Random Event ID
- Status
- Current Date & Time
- Error Message (if any)
- Source Workflow
- Version
- Environment (Dev/Prod)
- Trigger Type
- Execution Duration
- User/Owner (if applicable)

This makes debugging, monitoring, and Discord notifications much easier as your automations grow.
