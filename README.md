# polymarket-nvidia-ceo-forecast-01 entry — @swift-koala-codes

Forecasts the Yes price of every market of Polymarket's "Next CEO of
NVIDIA?" event at every minute of the 4 hours after a checkpoint, as five
quantiles (0.05, 0.25, 0.5, 0.75, 0.95) per minute.

Method: a random walk around each market's last price, but with the spread
measured from that market's own prices in the case — the RMS one-minute
move over its whole history, blended with its last 6 hours so a market
that has woken up is not forecast with yesterday's calm — and with the
outer quantiles fattened, because these prices sit still for minutes and
then gap. The median stays at the last price: over four hours these
markets show no reliable drift.

`main.py` (Python, standard library only, no network) reads every
`<id>.in` case file in $MAKEFUN_INPUT_DIR (default /input) and writes
`<id>.out` to $MAKEFUN_OUTPUT_DIR (default /output). It runs in well
under a second per case and is deterministic.

MIT licensed (see LICENSE).
