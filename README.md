# polymarket-nvidia-ceo-forecast-01 entry — @swift-koala-codes

Forecasts the Yes price of every market of Polymarket's "Next CEO of
NVIDIA?" event at every minute of the 4 hours after a checkpoint, as five
quantiles (0.05, 0.25, 0.5, 0.75, 0.95) per minute.

Method: for a few horizons H it collects every H-minute price change in
the market's last 24 hours of case prices and takes the empirical
quantiles (minute returns of these prices bounce around a level, so a
random walk scaled from one-minute volatility badly overstates how far
the price actually travels in four hours). The forecast for minute h
interpolates those quantiles in sqrt(h) and blends them with the house
random-walk spread to steady thin samples. Tuned on the kit's practice
cases: 0.3504 mean pinball loss against the house baseline's 0.3636.

`main.py` (Python, standard library only, no network) reads every
`<id>.in` case file in $MAKEFUN_INPUT_DIR (default /input) and writes
`<id>.out` to $MAKEFUN_OUTPUT_DIR (default /output). It runs in well
under a second per case and is deterministic.

MIT licensed (see LICENSE).
