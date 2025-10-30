# 📦 OTA Manifest Format

This manifest file defines available OTA updates for the system.  
It supports **unlimited updates**, each represented as a JSON object inside an array.

---

## 🧾 Example

```json
[
  {
    "download": "https://example.com/downloads/update_v1000.zip",
    "changelog": "<ul>\r\n  <li>- Update 1</li>\r\n  <li>- Update 2</li>\r\n</ul>",
    "md5": "",
    "title": "",
    "isTestBuild": false,
    "build": 3,
    "previousBuild": 2,
    "updateType": "zip",
    "linkType": "direct"
  },
  {
    "download": "8040c750-5206-4a14-8734-affc1c087e6d",
    "changelog": "<ul>\r\n  <li>- Update 1</li>\r\n  <li>- Update 2</li>\r\n</ul>",
    "md5": "",
    "title": "",
    "isTestBuild": false,
    "build": 2,
    "previousBuild": 1,
    "updateType": "zip",
    "linkType": "uploadnow"
  }
]
```

---

## 🧱 Field Description

| Field | Description | Example |
|--------|-------------|----------|
| `download` | Direct URL or UploadNow file UUID | `"https://example.com/update.zip"` / `"8040c750-5206-4a14-8734-affc1c087e6d"` |
| `changelog` | HTML changelog content (must be **escaped for JSON**) | `"<ul>\\r\\n  <li>- Update 1</li>\\r\\n  <li>- Update 2</li>\\r\\n</ul>"` |
| `md5` | Optional MD5 checksum of the update file | `"a1b2c3..."` |
| `title` | Title of the update (can be empty) | `"NEWROM v1.0.0"` |
| `isTestBuild` | Set to `true` if this is a test build | `false` |
| `build` | The build number of this update | `3` |
| `previousBuild` | The previous build number | `2` |
| `updateType` | Always `"zip"` for ZIP-based updates | `"zip"` |
| `linkType` | `"direct"` for direct download URLs or `"uploadnow"` for UUID-based links | `"direct"` / `"uploadnow"` |

---

## 🧩 Notes

- The `changelog` field **must be escaped for JSON** to prevent syntax errors.  
  Use this online tool: [https://bfotool.com/vi/json-escape-unescape](https://bfotool.com/vi/json-escape-unescape)
- You can include as many update objects as needed in the JSON array.
- The OTA updater will process entries in order, based on the `build` and `previousBuild` values.

---
