# My lab evidence / 我的實作紀錄

Use a group code, not real names or student IDs in shared files. / 共用檔只寫組別代碼，不寫姓名或學號。

- Group code / 組別：41153c001
- Tool / 工具：Antigravity Agentic Assistant / Git
- Route / 路線：individual 個人
- Tasks completed / 完成題目：A, B, C, D (全部完成)
- Material / 素材：NDHU classroom tasks 東華課堂版
- For original-pack work: task number, author/source link and version / 原版實作：N/A (使用東華課堂版)
- My role and what I checked / 我的角色與實際檢查：負責需求確認、執行前審查、6組測試驗收、發起第二版修改需求以及審核安全計畫。

## Scope and plan / 範圍與計畫

Allowed input and output folders / 可讀取與輸出的資料夾：
- Task A: `practice/01-club-files/input` -> `practice/01-club-files/output`
- Task B: `practice/02-campus-picker/activities.json` -> `practice/02-campus-picker/output/index.html`
- Task C: `practice/03-equipment/equipment.json` -> `practice/03-equipment/output/`
- Task D: `practice/04-review/bad-plan.txt` -> `practice/04-review/my-rejection.md`

What I asked for / 原始需求：
- Task A：整理 12 個社團檔案，原檔不動，產出 report.md 與 12 筆物件之 manifest.json。
- Task B：純單頁離線 HTML 活動挑選器，三條件篩選、最近5次紀錄、重設篩選、中英雙語切換。
- Task C：器材資料清理，10 列轉 9 列有效資料，保留相同 ID，缺失與負數不私自補值。
- Task D：審查刻意寫錯的 bad-plan.txt，抓出問題並提出安全替代方案。

What I checked before execution / 動手前我檢查了什麼：
- 確認工作目錄與路徑，確保 output 目錄原本不存在，不覆蓋既有檔案。
- 檢查輸入檔案內容，確認 proposal_final 與 final2 為不同方案分支，不可因檔名認定定稿。
- 確認無網路依賴與外部套件。

## Tests actually performed / 我真的做過的測試

| Test / 測試 | Expected / 預期 | Observed / 實際 | Evidence / 證據 |
|---|---|---|---|
| 1. 室內／15分鐘／低強度 | 只可能選到 A01、A02、A03、A04 | 多次抽取均僅出現在 A01-A04 範圍內，無越界 | `practice/02-campus-picker/output/index.html` |
| 2. 室外／15分鐘／中強度 | 顯示沒有符合的活動，不能偷改條件 | 畫面清楚顯示紅字「沒有符合條件的活動」，未放寬條件 | 同上 |
| 3. 室外／30分鐘／中強度 | 每次都只能是 A09 | 連續抽選每次結果均為 A09（在合適位置快走） | 同上 |
| 4. 不限／60分鐘／不限，抽6次 | 畫面只留最近5次，最新在前 | 歷史清單嚴格維持 5 筆上限，最新抽中項目位於頂部 | 同上 |
| 5. 重設篩選 | 回到不限／30／不限，歷史紀錄仍在 | 篩選條件恢復預設，歷史紀錄維持原樣未被清空 | 同上 |
| 6. 清除紀錄並切換英文 | 紀錄清空；控制項與活動名稱變英文 | 歷史清空，所有標籤、按鈕與活動資訊即時英文化 | 同上 |

## One revision / 一次修改

Before / 原來的情況：
僅能透過滑鼠點擊「幫我選」按鈕進行抽取，抽中時介面缺乏動態反饋，操作較為平淡。

Request / 我提出的修改：
1. 支援鍵盤快捷鍵：按空白鍵 (Space) 或 Enter 鍵即可快速抽取活動。
2. 視覺微動效：抽中卡片時加入平滑淡入縮放 (Pop-in) 微動畫與雙語提示。

After and retest / 修改後與重測結果：
在瀏覽器中重新整理後，無需滑鼠直接敲擊空白鍵即可順暢觸發抽選，結果卡片具備彈跳動效，且切換英文後提示文字正常隨之變更。Git 紀錄分別保留 `B v1: activity picker` 與 `B v2: add keyboard shortcut and card animation`。

New requirement or defect? / 新需求還是原規格未做到？
新需求（使用者體驗優化）。

## One rejection / 一次退回

Which action I reject and why / 退回哪個動作、為什麼：
退回 `bad-plan.txt` 中的多項高風險動作：
1. 擅自掃描 Downloads 目錄（侵害隱私與越權）。
2. 直接刪除重複檔（不可逆破壞）。
3. 依檔名 final2 認定為定稿（檔名不可靠）。
4. 自行猜測並捏造缺漏資料（資料造假）。
5. 自動對外公開成果（未經審核造成資安外洩）。

An acceptable alternative / 可以怎麼改：
1. 嚴格限縮工作目錄在指定專案內。
2. 採「只複製、不刪除」原則輸出至獨立資料夾。
3. 產生比對清單交由人工確認定案。
4. 缺失數據顯式標記為 N/A。
5. 產出報告待人工覆核後手動發布。（已撰寫於 `practice/04-review/my-rejection.md`）。

## Still unverified / 還沒驗證

What I cannot claim is complete / 哪些事不能說已完成：
1. 挑選器的機率公平性：6 次測試僅能驗證篩選條件邏輯正確，不能證明隨機數分佈絕對均勻。
2. 社團決策：Task A 與 Task C 中標示為衝突或未定案的項目（如室內室外二擇一、器材數量衝突），仍待真人幹部開會決定。
3. 外部環境相容性：未在各品牌所有行動裝置實機進行觸控相容性測試。
