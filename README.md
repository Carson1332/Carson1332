# Carson1332 · Seesen

我是 Carson，一個寫程式的人。做過量化交易，也在銀行做過 machine learning，現在在做 **Seesen**。

我一直相信 AI 是一種「以小見大，由微致遠」的東西：一個很小的訊號、一次很細的觀察，順著數據往下走，常常能看見遠處正在發生的變化。量化和金融讓我習慣了這種視角——市場裡真正重要的東西，往往藏在噪音裡、藏在微小的價差裡、藏在一條還沒被人讀懂的數據流裡。

Seesen 想做的，就是把這種「從細微處看見全局」的能力，沉澱成可以複用、可以分享的東西。
# see small, sense big

它服務的是一個很樸素的需求：**少看一點噪音，把注意力留給真正值得看的變化。**

🌐 官網：[seesen.tech](https://seesen.tech) ｜ 合作：business@seesen.tech

---

## 我在做的事

### ai_fin_daily · 讓 AI 幫你讀懂每天的市場

資訊太多不是問題，看不過來才是。

ai_fin_daily 每天美股收盤後，自動把當天的行情、板塊輪動和市場情緒收斂成一份繁體中文的市場敘事，推送到 Telegram。流程是 Finnhub 抓行情 → 18 支板塊 ETF 計分板加大盤儀表和情緒指標 → AI生成七節白話敘事 → Telegram 推送並歸檔成 Markdown，整套排程跑在 GitHub Actions 上，每天自動執行。

如果你也每天被市場資訊淹沒，這套東西可以直接照搬。clone 下來、填四個 API key，就能有一份自己的每日市場日報，成本大約每天 $0.005。少刷一點，看得更準一點。

[ai_fin_daily](https://github.com/Carson1332/ai_fin_daily)

### ml-denoising · 把深度學習從數學層面親手實現一遍

很多深度學習教學看完，`nn.Conv2d` 和 `nn.MultiheadAttention` 還是像黑盒。

ml-denoising 是在 MNIST 上的四個 end-to-end 實驗，全部塞在單一個 Colab notebook 裡跑通：CNN 訓練與超參數探索（98.48%）、U-Net 圖像去噪（test MSE 0.00698），以及**不靠 PyTorch 黑盒、從零手寫的 CNN 與 Vision Transformer**——手刻卷積、池化、self-attention。重點不是刷分，而是把卷積和注意力機制拆到只剩矩陣乘法和 softmax，徹底搞懂它們為什麼能 work。

打開 Colab 直接 Run all 就能跑，不用配環境。想真正搞懂原理，而不只是會調 API，可以從這裡開始。

[ml-denoising](https://github.com/Carson1332/ml-denoising)

### funding_arbs · 從微小的價差裡找機會，也記錄回測怎麼騙人

funding_arbs 是圍繞永續合約資金費率（funding rate）做的套利研究與策略框架，跨 Binance、Bybit、OKX，從數據、費率計算到回測，記錄了一條完整的路徑：從一個失敗的均值回歸基線，到能用的順勢 carry 策略，再到雙向引擎。

但它最有價值的部分，是一次很老實的事後復盤。早期那些漂亮的 Sharpe > 6 數字，是怎麼一步步被揪出時間戳對齊 bug、費用算錯、機會成本漏算、路徑依賴和肥尾分佈這五個坑，最後修正到一個現實的 **Sharpe 1.97**。

如果你也在做策略回測，這份 README 與其說是炫耀成果，不如說是一份「回測為什麼會騙人」的教材，那五個坑幾乎個個都是常見陷阱，值得對照自己的代碼檢查一遍。

[funding_arbs](https://github.com/Carson1332/funding_arbs)

### BinanceSec · 看得清，是因為先把數據接得穩

上面那些研究都得站在乾淨的數據上，BinanceSec 就是這個地基。

它是一個基於 WebSocket 的 Binance 期貨實時數據捕獲系統，同時吃 aggTrade 和 depth 流，維護一個帶序列校驗的本地訂單簿，把原始 diff、定期快照、衍生指標和偵測事件都寫進 MySQL，還有一套離線 replay 來驗證捕到的數據能不能完整重建當時的盤口。目標是 7×24 穩定運行的市場數據層。

如果你要自己接交易所實時數據，這裡有一份可以參考的「正確做法」：怎麼處理斷線重連與序列缺口、為什麼價格要用 `DECIMAL(18,8)` 而不是 `FLOAT`、批量寫入怎麼設計、以及怎麼用 replay 證明你的數據沒丟。

[BinanceSec](https://github.com/Carson1332/BinanceSec)

---

## 把「看見」分享出去

研究做出來，還要講得出去。我會把 AI 和量化的實踐，變成更多人能看懂的內容：在 Instagram 持續更新 AI 影音，也在 Seesen Community 分享項目和實測過程。

對我來說，這不是另一個方向，而是同一件事的另一條腿：**先做出來，再講給更多人聽。**

📷 Instagram（AI 影音）：[ai reels and tvc](https://www.instagram.com/researchbycarson/reels/)

---

## 我相信的幾件事

**先做出來，再談方法。** 我不太相信隔空判斷一個策略或模型好不好用，也不太信光看排行榜。它得接入真實的數據和真實的市場，能跑、能驗證、能省下或賺到一點什麼，才算過了第一關。

**從細微處看見全局。** 這是 Seesen 的底層哲學，也是量化的本質。微小的、被忽略的訊號，往往是最有價值的那一個。

**工作流值得被保存。** 一次回測會過期，一段行情會結束，但被驗證過的方法可以留下來，被複用、被修改，也可以交給程式繼續跑。

---

## 這個倉庫是什麼

這裡既是我的 GitHub Profile，也是 Seesen 這個 portfolio 的入口。

對第一次打開這個主頁的人，它介紹我是誰、我在做什麼、有哪些項目可以拿去用。對已經認識 Seesen 的人，它會記錄這條 AI Finance、AI Models 和 Quant Research 的主線接下來要長成什麼樣。

我做過量化，也做過銀行的 ML，這兩段經歷讓我越來越確定一件事：真正的優勢不在於你掌握了多少工具，而在於你能不能從噪音裡，比別人早一點看見那個正在發生的變化。Seesen 接下來想做的，就是把這種能力做成可複用、可分享的東西——不只是我自己用得上，而是普通人拿到之後，也能真的多看懂一點、多做成一點。

永遠保持好奇。一起以小見大，由微致遠。

---

## 找到我

- 🌐 Seesen：[seesen.tech](https://seesen.tech)
- 📧 合作 / 交流：business@seesen.tech
- 📷 Instagram（AI 影音）：[ai reels and tvc](https://www.instagram.com/carson.w_1024/reels/)

---

⭐ 如果這些項目對你有幫助，歡迎 Star。
