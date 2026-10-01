# -<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>主題一：通膨衝擊與實質薪資/就業型態研究報告</title>
    <!-- Chart.js 畫圖函式庫 -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary-color: #1a365d;
            --secondary-color: #2b6cb0;
            --accent-color: #e53e3e;
            --bg-color: #f7fafc;
            --card-bg: #ffffff;
            --text-color: #2d3748;
            --border-color: #e2e8f0;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--bg-color);
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        header {
            background-color: var(--primary-color);
            color: white;
            padding: 2rem;
            border-radius: 8px;
            margin-bottom: 2rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        header h1 {
            margin: 0 0 10px 0;
            font-size: 1.8rem;
        }

        header p {
            margin: 0;
            opacity: 0.9;
            font-size: 0.95rem;
        }

        .card {
            background: var(--card-bg);
            padding: 1.8rem;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            margin-bottom: 1.5rem;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
        }

        h2 {
            color: var(--primary-color);
            border-bottom: 2px solid var(--secondary-color);
            padding-bottom: 0.5rem;
            margin-top: 0;
        }

        h3 {
            color: var(--secondary-color);
            margin-top: 1.2rem;
        }

        ul {
            padding-left: 1.2rem;
        }

        li {
            margin-bottom: 0.5rem;
        }

        .chart-container {
            position: relative;
            margin-top: 1.5rem;
            height: 350px;
            width: 100%;
        }

        .code-block {
            background-color: #1e1e1e;
            color: #d4d4d4;
            padding: 1rem;
            border-radius: 6px;
            overflow-x: auto;
            font-family: "Consolas", "Courier New", monospace;
            font-size: 0.88rem;
        }

        .badge {
            background-color: #ebf8ff;
            color: #2b6cb0;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.85rem;
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- 頁頭資訊 -->
    <header>
        <h1>專題研究：通膨衝擊與實質薪資/就業型態</h1>
        <p>淡江大學《人工智慧與經濟研究報告》專題 | 數據來源：AREMOS 台灣經濟資料庫</p>
    </header>

    <!-- 1. 專題研究題目 -->
    <section class="card">
        <h2>1. 專題研究題目</h2>
        <ul>
            <li><strong>題目 A（動態計量導向）：</strong><br>
                《實質購買力剝蝕與勞動供給反應：台灣 CPI 通膨衝擊對產業薪資結構及青年就業型態之動態傳導（VAR-VECM 模型實證）》
            </li>
            <li><strong>題目 B（AI 前瞻預測導向）：</strong><br>
                《名目薪資追趕通膨衝擊的時滯效應：基於 AREMOS 巨量經濟數據與 LSTM 神經網絡之預測與因果分析》
            </li>
        </ul>
    </section>

    <!-- 2. 研究假說與經濟學理傳導機制 -->
    <section class="card">
        <h2>2. 研究假說與經濟學理傳導機制</h2>
        
        <h3>研究假說 (Hypotheses)</h3>
        <ul>
            <li><strong>H<sub>1a</sub>：</strong> 通膨衝擊（特別是外食費與房租 CPI）對非技術性與服務業名目薪資具有顯著的<strong>調整滯後性（Adjustment Lag）</strong>，導致短期內實質薪資負成長。</li>
            <li><strong>H<sub>1b</sub>：</strong> 實質薪資遭受侵蝕會迫使青年勞工轉向高彈性、高工時或非典型就業（如兼職、外送），以填補短期生活資金缺口。</li>
        </ul>

        <h3>經濟學理傳導機制</h3>
        <ul>
            <li><strong>名目工資僵硬性 (Nominal Wage Rigidity)：</strong> 薪資契約多為定期簽訂，無法即時隨通膨快速向上調升；物價上漲等同於降低實質工資，破壞勞動市場均衡。</li>
            <li><strong>勞動供給的收入效應 (Income Effect in Labor Supply)：</strong> 當實質購買力顯著下降時，個人為維持基本消費水平，會增加勞動供給時數或尋找副業，帶動非典型就業率上升。</li>
        </ul>
    </section>

    <!-- 3. 資料視覺化圖表建議與實作 -->
    <section class="card">
        <h2>3. 資料視覺化圖表實作</h2>
        <p>以下展示本研究建議採用之圖表樣式（以模擬數據呈現）：</p>

        <h3>(1) 雙 Y 軸圖：CPI 通膨率 vs 實質薪資成長率</h3>
        <p>觀察名目薪資年增率追趕物價之時滯，以及實質薪資受侵蝕的時間區段。</p>
        <div class="chart-container">
            <canvas id="dualYChart"></canvas>
        </div>

        <h3 style="margin-top: 2.5rem;">(2) 脈衝響應圖 (IRF Concept)：CPI 衝擊對實質薪資之動態軌跡</h3>
        <p>模擬給予 CPI +1 個標準差衝擊後，未來 12 個月實質薪資變化的動態響應趨勢。</p>
        <div class="chart-container">
            <canvas id="irfChart"></canvas>
        </div>
    </section>

    <!-- 4. AREMOS 變數對接說明 -->
    <section class="card">
        <h2>4. AREMOS 資料庫對接指標說明</h2>
        <ul>
            <li><span class="badge">CPI</span> 消費者物價總指數</li>
            <li><span class="badge">CPI_FOOD</span> 外食費指數 / <span class="badge">CPI_SHELTER</span> 房租類指數</li>
            <li><span class="badge">NRE_SAL</span> 工業及服務業受僱員工總薪資</li>
            <li><span class="badge">NRE_SAL_SER</span> 服務業薪資 / <span class="badge">PART_TIME</span> 非典型/兼職就業人數</li>
        </ul>
    </section>

</div>

<script>
    // 1. 雙 Y 軸圖表
    const ctx1 = document.getElementById('dualYChart').getContext('2d');
    new Chart(ctx1, {
        type: 'line',
        data: {
            labels: ['Q1', 'Q2', 'Q3', 'Q4', 'Q1(T+1)', 'Q2(T+1)', 'Q3(T+1)', 'Q4(T+1)'],
            datasets: [
                {
                    label: 'CPI 年增率 (%) [左軸]',
                    data: [1.2, 1.8, 2.5, 3.1, 2.8, 2.2, 1.9, 1.5],
                    borderColor: '#e53e3e',
                    backgroundColor: 'rgba(229, 62, 62, 0.1)',
                    yAxisID: 'y1',
                    tension: 0.3
                },
                {
                    label: '實質薪資成長率 (%) [右軸]',
                    data: [1.5, 0.8, -0.5, -1.2, -0.8, 0.2, 0.6, 1.1],
                    borderColor: '#2b6cb0',
                    borderDash: [5, 5],
                    yAxisID: 'y2',
                    tension: 0.3
                }
            ]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            scales: {
                y1: {
                    type: 'linear',
                    position: 'left',
                    title: { display: true, text: 'CPI 年增率 (%)' }
                },
                y2: {
                    type: 'linear',
                    position: 'right',
                    title: { display: true, text: '實質薪資成長率 (%)' },
                    grid: { drawOnChartArea: false }
                }
            }
        }
    });

    // 2. 脈衝響應圖 (IRF)
    const ctx2 = document.getElementById('irfChart').getContext('2d');
    new Chart(ctx2, {
        type: 'line',
        data: {
            labels: ['M0', 'M1', 'M2', 'M3', 'M4', 'M5', 'M6', 'M7', 'M8', 'M9', 'M10', 'M11', 'M12'],
            datasets: [
                {
                    label: '實質薪資脈衝響應軌跡',
                    data: [0, -0.15, -0.38, -0.45, -0.32, -0.20, -0.10, -0.05, -0.02, 0.00, 0.01, 0.00, 0.00],
                    borderColor: '#2b6cb0',
                    backgroundColor: 'rgba(43, 108, 176, 0.1)',
                    fill: true,
                    tension: 0.3
                },
                {
                    label: '95% 信賴區間上限',
                    data: [0, -0.05, -0.20, -0.25, -0.15, -0.05, 0.05, 0.08, 0.08, 0.08, 0.07, 0.05, 0.03],
                    borderColor: '#cbd5e0',
                    borderDash: [2, 2],
                    fill: false,
                    pointRadius: 0
                },
                {
                    label: '95% 信賴區間下限',
                    data: [0, -0.25, -0.56, -0.65, -0.49, -0.35, -0.25, -0.18, -0.12, -0.08, -0.05, -0.05, -0.03],
                    borderColor: '#cbd5e0',
                    borderDash: [2, 2],
                    fill: '-1',
                    backgroundColor: 'rgba(203, 213, 224, 0.2)',
                    pointRadius: 0
                }
            ]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: {
                    labels: {
                        filter: item => item.text !== '95% 信賴區間下限' // 簡化圖例顯示
                    }
                }
            },
            scales: {
                y: {
                    title: { display: true, text: '標準差變動量' }
                },
                x: {
                    title: { display: true, text: '衝擊發生後月份 (Period)' }
                }
            }
        }
    });
</script>

</body>
</html>
