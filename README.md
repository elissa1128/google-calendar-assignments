# Todo list
基於 Vue.js 的待辦事項清單

## 特點
- 串接 Google Calendar API 行事曆

## 瀏覽器支援程度
![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) 
Latest ✔
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
將可重複利用部分拆成組件

- 創建待辦事項的 CreateTodo 組件
- 顯示待辦事項用的 TodoItem 組件

### CreateTodo 組件
功能：新增

必填選項為時間及主題(待辦標題)
當摘要沒有填寫時，隱藏摘要顯示收合的功能
### TodoItem 組件
功能：摘要顯示的收合、編輯、刪除