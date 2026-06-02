# EDA TCL Script Generator

> 適用於數位 IC 設計的 Synopsys EDA 工具 TCL 腳本產生器

## 功能特色

- **按鈕化操作**：點選自然語言按鈕即可產生對應 TCL 指令，不需要記憶指令語法
- **路徑自動帶入**：填入專案路徑後，所有指令自動替換為實際路徑
- **多工具支援**：涵蓋 Synopsys 完整 EDA 流程的六個主要工具
- **即時預覽**：按鈕上顯示 TCL 指令預覽，點選後立即加入腳本
- **一鍵下載**：產生完成後直接下載 `.tcl` 檔案，可直接在 EDA 工具中執行

## 支援工具

| 工具 | 用途 | 涵蓋功能 |
|------|------|---------|
| **Design Compiler (DC)** | RTL 邏輯綜合 | 讀取 RTL、設定 Library、時序約束、compile_ultra、報告、輸出網表 |
| **PrimeTime (PT)** | 靜態時序分析 | 讀取網表/SPEF、create_clock、setup/hold 報告、ECO |
| **IC Compiler II (ICC2)** | 自動佈局佈線 | Floorplan、Power Ring、Place、CTS、Route、輸出 GDS |
| **VCS** | 功能/門階模擬 | 編譯 RTL/Netlist、執行模擬、迴歸測試、覆蓋率報告 |
| **Formality** | 形式等效驗證 | 讀取 RTL/網表、執行驗證、診斷不等效點 |
| **SpyGlass** | Lint / CDC / RDC | Lint 分析、跨時鐘域、重置域檢查、Waiver 管理 |

## 使用方式

### 線上使用
直接用瀏覽器開啟 `index.html`，無需安裝任何套件。

### 本地部署
```bash
# 直接開啟 HTML 檔案
open index.html
```

### Cloudflare Workers 部署
```bash
npm install
npx wrangler deploy
```

## 操作流程

1. **選擇工具** — 點選頂部的工具標籤（DC / PT / ICC2 / VCS / Formality / SpyGlass）
2. **填入路徑** — 在左側填入專案的實際路徑與參數
3. **點選指令** — 在中間點選需要的功能按鈕
4. **查看腳本** — 右側即時顯示產生的 TCL 腳本
5. **下載使用** — 點「下載 .tcl」取得腳本，在 EDA 工具中直接執行

## 指令覆蓋範圍

### Design Compiler
- 環境設定：target library、link library、多核心並行
- 讀取設計：Verilog / SystemVerilog / VHDL RTL
- 時序約束：create_clock、input/output delay、false path、multicycle path
- 綜合：compile_ultra、incremental compile
- 報告：timing / area / power / QoR / constraint violations
- 輸出：Verilog netlist / DDC / SDC / SDF

### PrimeTime
- 讀取：verilog netlist、SDC、SPEF 寄生參數
- 分析：check_timing、propagated clock、operating conditions
- 報告：setup/hold timing、WNS/TNS、clock skew、constraint violations
- 輸出：SAIF、ECO fixing script

### IC Compiler II
- 建立設計：create_lib、read_verilog、link_block
- Floorplan：initialize_floorplan、power ring、stripe、well tap
- Placement：place_opt、legalize
- CTS：clock_opt、clock QoR 報告
- Routing：route_auto、route_opt、DRC check
- 輸出：GDS、final netlist、SPEF、SDC

### VCS
- 編譯：RTL 行為模擬、Gate-level + SDF 反標模擬
- 執行：基本模擬、隨機 seed、批次迴歸測試
- 覆蓋率：line/cond/branch coverage 收集與報告

### Formality
- 讀取：參考設計（RTL）、實作網表
- 驗證：match + verify 形式等效性檢查
- 除錯：failing points 診斷

### SpyGlass
- Lint：RTL 代碼品質檢查
- CDC：跨時鐘域同步問題分析
- RDC：重置域交叉問題分析
- Waiver：問題豁免管理

## 技術架構

- 純 HTML / CSS / JavaScript，無框架依賴
- 單一 HTML 檔案，可離線使用
- 支援部署到 Cloudflare Workers / Pages

## 授權

MIT License
