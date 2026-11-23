# 專案交接筆記（handoff.md）

> 最後更新：2026-11-23 21:03

## 一、 已完成項目
1. **系列企劃與 Book 1 腳本**：
   - 完成 [01_系列企劃書.md](01_系列企劃書.md)（8 冊螺旋式課綱、Mia & Pip 角色設定、3D 皮克斯畫風、互動網頁規格）。
   - 完成 [02_Book1_Hello_Pip_分鏡腳本.md](02_Book1_Hello_Pip_分鏡腳本.md)（24 頁互動分鏡）。
2. **Book 1《Hello, Pip!》3D 視覺與語音**：
   - 生成 3D 皮克斯畫風封面、角色設定圖與 7 張故事跨頁插畫，並裁切 `warmup_mia_pip.jpg` 與 `pip_sad.jpg` 等特寫圖。
   - 使用 `edge-tts` 生成全套 MP3（Mia=`en-US-AnaNeural`、Pip=`en-GB-MaisieNeural`、Mom=`en-US-JennyNeural`）。
   - 使用 Google Colab T4 GPU + **YuE 2（`m-a-p/YuE2-3B`, `low_vram=True`）** 生成 35.6 秒兒歌 `assets/audio/hello_pip_yue2.mp3`。
3. **互動網頁繪本與教學升級**：
   - 完成 `index.html`（系列書櫃首頁）與 `book1_hello_pip.html`（含 32px 大字體、翻頁自動朗讀、點圖片發音、TPR 動一動頁、隨機洗牌聽音小遊戲、YuE 2 兒歌播放器、有聲小詞典與家長導讀）。
4. **線上部署與工作流沉澱**：
   - 部署至 GitHub：`blueymch-star/mia-pip-english-picture-books`（`main` 分支）
   - GitHub Pages：https://blueymch-star.github.io/mia-pip-english-picture-books/
   - 已將整套流程存成全域技能 `english-picture-book-workflow`（`~/.gemini/config/skills/english-picture-book-workflow/SKILL.md`）。

---

## 二、 待辦與下一步
1. **補齊 Book 1 第 6 跨頁大圖（選用）**：先前 `scene_06_happy` 因圖片生成配額上限（429）暫以 `pip_happy.jpg` 彈跳畫面呈現，之後可補生成 3D 客廳吃餅乾大圖替換。
2. **製作 Book 2《Jump, Pip, Jump!》**：下次開工直接說「用英語繪本工作流製作 Book 2」即可依 SOP 接續製作。

---

## 三、 踩坑備忘
- **Colab GPU 選擇**：尖峰時段 `A100` / `L4` / `G4` 容易回傳 `Service Unavailable`；改用標準 `T4` 搭配 `YuE2-3B`（`low_vram=True`）即可穩定生成且無截斷，跑完記得執行 `colab stop -s <session>` 省下 compute units。
- **小一零基礎教學細節**：故事對話維持固定骨架（如統一用 `How are you, Pip?`）、字體設為 `32px`、小遊戲務必洗牌題目與選項位置防止背位置。
