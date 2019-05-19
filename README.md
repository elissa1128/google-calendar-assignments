# Vue todo list
基於 Vue.js 的待辦事項清單

- 新增
- 編輯
- 刪除
- 可載入 Google Calendar API 行事曆 (get)

## 瀏覽器支援程度
![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) | 
--- | --- | --- | --- | --- | --- |
最新 ✔ | 最新 ✔ | 11 ✔ |

## 安裝與開發
使用 npm
```
# 安裝
npm install

# 開發
npm run dev

# 部署
npm run deploy
```

## 說明

### Google Calendar API 行事曆變更
替換 `Todo.vue` 參數即可變更行事曆
- `API_KEY`: Google Calendar API key
- `API_ID`: Google Calendar 的行事曆 id

### CreateTodo 組件
功能：新增

### TodoItem 組件
功能：摘要顯示的收合、編輯、刪除