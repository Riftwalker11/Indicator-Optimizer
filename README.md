# 🔬 Custom Trading Indicator Optimizer

A powerful, browser-based optimization tool for trading indicators. Test thousands of parameter combinations to find the best configurations for your trading strategy.

## ✨ Features

- **📊 CSV Data Upload** - Import your historical price data (OHLCV format)
- **🔧 Custom Indicators** - Write your own indicator logic in JavaScript
- **🎯 Parameter Optimization** - Test multiple parameter ranges simultaneously
- **📈 Built-in TA Library** - SMA, EMA, RSI, ATR, and more
- **💾 IndexedDB Storage** - Results saved locally in your browser
- **⚡ Fast Processing** - Optimized batch processing with progress tracking
- **🛑 Stop Anytime** - View results even if optimization is interrupted
- **📥 Export Results** - Download optimized parameters as CSV

## 🚀 Live Demo

**[Try it now](https://yourusername.github.io/trading-optimizer/)**

## 🎯 How It Works

1. **Upload CSV Data** - Requires columns: `open`, `high`, `low`, `close`, `volume`, `timestamp`
2. **Paste Indicator Code** - Write JavaScript function using built-in TA helpers
3. **Select Parameters** - Choose which parameters to optimize and set ranges
4. **Run Optimization** - Test all combinations (can handle millions!)
5. **View Results** - See top performers ranked by win rate

## 📝 Example Indicator
```javascript
function myIndicator(bars, params) {
  // @param fast_ma: 10, min: 5, max: 50, step: 5
  // @param slow_ma: 30, min: 20, max: 200, step: 10
  
  const fast = params.fast_ma || 10;
  const slow = params.slow_ma || 30;
  
  const fastMA = TA.sma(bars, 'close', fast);
  const slowMA = TA.sma(bars, 'close', slow);
  
  const signals = [];
  for (let i = 1; i < bars.length; i++) {
    if (!fastMA[i] || !slowMA[i]) continue;
    
    // Golden cross - buy signal
    if (fastMA[i] > slowMA[i] && fastMA[i-1] <= slowMA[i-1]) {
      signals.push({index: i, type: 'LONG', price: bars[i].close});
    }
    // Death cross - sell signal
    else if (fastMA[i] < slowMA[i] && fastMA[i-1] >= slowMA[i-1]) {
      signals.push({index: i, type: 'SHORT', price: bars[i].close});
    }
  }
  return signals;
}
```

## 🛠️ Available TA Functions

- `TA.sma(bars, field, period)` - Simple Moving Average
- `TA.ema(bars, field, period)` - Exponential Moving Average
- `TA.rsi(bars, field, period)` - Relative Strength Index
- `TA.atr(bars, period)` - Average True Range
- `TA.highest(bars, field, period)` - Highest value in period
- `TA.lowest(bars, field, period)` - Lowest value in period

## ⚙️ Customizable Settings

- **Win Threshold** - Define what percentage move counts as a win (0.15% - 5.0%)
- **Look Ahead Bars** - How many bars to search for best/worst moves (5-100)
- **Parameter Ranges** - Set min, max, and step for each parameter
- **Signal Filters** - Min/max signal count requirements (default: 8-150)

## 🎮 Trading Styles Supported

| Style | Win Threshold | Look Ahead Bars |
|-------|---------------|-----------------|
| Scalping | 0.10% - 0.25% | 5-10 bars |
| Day Trading | 0.50% - 1.00% | 20-30 bars |
| Swing Trading | 1.00% - 3.00% | 50-100 bars |
| Position Trading | 3.00%+ | 100+ bars |

## 💡 Tips for Best Results

1. **Start Small** - Test with limited parameter ranges first
2. **Use Comments** - Mark parameters with `// @param` for auto-detection
3. **Convert from PineScript** - Use the built-in conversion prompt helper
4. **Review Top Results** - Don't just pick #1, look for consistency
5. **Forward Test** - Always validate results on out-of-sample data

## 🔒 Privacy & Security

- **100% Client-Side** - All processing happens in your browser
- **No Data Uploaded** - Your CSV data never leaves your computer
- **Local Storage** - Results saved in IndexedDB (browser local storage)
- **No Tracking** - No analytics, cookies, or user tracking

## 🌟 Use Cases

- Optimize moving average crossover strategies
- Find best RSI overbought/oversold levels
- Test Bollinger Band squeeze parameters
- Discover optimal ATR multipliers for stops
- Validate indicator combinations
- Compare LONG vs SHORT parameter sets

## 🚧 Technical Details

- **Pure JavaScript** - No frameworks, just vanilla JS
- **IndexedDB** - Persistent storage for optimization results
- **Web Workers Ready** - Can be extended for parallel processing
- **PapaParse** - CSV parsing library (only dependency)
- **Memory Efficient** - Generator-based config creation

## 📊 Performance

- Tests **50-100 configs/second** (depends on indicator complexity)
- Can handle **millions of combinations**
- Only saves **70%+ win rate** results to conserve storage
- Batch processing with progress tracking

## 🤝 Contributing

Found a bug or want to add features? Contributions welcome!

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📜 License

MIT License - Free to use, modify, and distribute

## ⚠️ Disclaimer

This tool is for educational and research purposes only. Past performance does not guarantee future results. Always do your own research and never risk more than you can afford to lose.

## 💬 Support

Having issues? Check out the examples in the app or open an issue on GitHub.

---

**Built with ❤️ for traders who love to optimize**
```

---

## 🏷️ Repository Topics/Tags

When setting up your GitHub repo, add these topics (helps people find it):
```
trading
optimizer
technical-analysis
indicators
backtesting
javascript
trading-strategy
algorithmic-trading
parameter-optimization
trading-tools
stock-market
crypto-trading
forex
browser-based
client-side
