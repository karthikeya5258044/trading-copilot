Trading Copilot 📈

An AI-powered decision-support system for stock trading that goes beyond simple price prediction — it detects market regimes, flags anomalies, mines hidden behavioral patterns, and generates human-readable trading advice.


Currently built and validated on US equities (AAPL, TSLA, MSFT, GOOGL). Indian stock market (NSE) support is planned as the next milestone — see Roadmap.




What it does

Most trading signal projects stop at "train a model, print BUY/SELL." Trading Copilot goes further — it combines supervised learning, unsupervised pattern discovery, and anomaly detection into a single pipeline that outputs a plain-English market report, similar to what a research analyst might hand you each morning.

Example output:

═══════════════════════════════════════════════════════
   MARKET ANALYSIS REPORT — AAPL
   Date  : 2026-05-15
   Price : $300.23
═══════════════════════════════════════════════════════

📊 TODAY'S PRICE BEHAVIOUR
  Close Price    : $300.23
  Daily Return   : -1.2%  → Strong down day
  Volume Ratio   : 1.8x normal  → Above average volume — confirms price move

📉 TECHNICAL INDICATOR READINGS
  RSI  : 88.4  →  OVERBOUGHT — stock has risen too fast. Pullback likely.
  MACD : 9.52  →  Bullish but momentum is fading. Watch closely.

🏛️  MARKET REGIME ANALYSIS
  Current Regime : ⚠️ Volatile Confusion
  What to do     : Be very cautious. Reduce position size. Wait for clarity.

🔍 ANOMALY DETECTION
  ✓ Today is a NORMAL day — no anomaly detected.

✓ Both models AGREE — strong signal: SELL ✗


Pipeline

1. Data Collection    → Stock price API (OHLCV data, multi-ticker)
2. EDA                → Return distributions, volatility trends, 
                         correlation heatmaps, candlestick visualization
3. Feature Engineering→ RSI, MACD, Bollinger Bands, moving averages 
                         (7/21/50-day), momentum, lag features, volume ratios
4. Classification     → Random Forest + XGBoost predicting BUY / HOLD / SELL
5. Market Intelligence→ KMeans regime detection (Bull Momentum, Bear Pressure, 
                         Sideways Calm, Volatile Confusion)
                       → Isolation Forest + DBSCAN anomaly detection
                       → Apriori association rule mining (hidden indicator 
                         combinations that precede BUY/SELL signals)
6. Reporting          → Human-readable console report combining all signals
7. Dashboard          → Power BI visualization layer (in progress)


Tech Stack

CategoryToolsData & StoragePython, Pandas, NumPy, SQLAlchemy, SQLiteVisualizationMatplotlib, Seaborn, mplfinanceMachine LearningScikit-learn (Random Forest, KMeans, Isolation Forest, DBSCAN, PCA), XGBoostClass ImbalanceSMOTE (imbalanced-learn)Pattern Miningmlxtend (Apriori, Association Rules)Dashboard (in progress)Power BI


Sample Results


Trained on 2,700+ trading days across 4 tickers (2020–2026)
Feature set of 23 technical indicators per prediction
Random Forest: ~43% accuracy | XGBoost: ~49% accuracy on 3-class BUY/HOLD/SELL classification


Honest note on model performance: because HOLD dominates the signal distribution (~74% of days), raw accuracy isn't the most meaningful metric here — the models are currently better at flagging risk context (regime + anomalies) than nailing precise directional calls. Improving BUY/SELL precision via better labeling thresholds and additional features is an active area of iteration.


Roadmap


 Power BI dashboard for interactive signal visualization
 Extend to Indian equities (NSE/BSE) via yfinance .NS tickers
 Improve BUY/SELL precision (currently HOLD-biased due to class imbalance)
 Backtesting module to simulate strategy P&L over time
 Live data refresh instead of static historical pull


