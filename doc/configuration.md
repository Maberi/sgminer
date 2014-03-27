# Configuration and command-line options

*Work in progress!*


## Config-file and CLI options

### algorithm

Allows choosing between the few mining algorithms for incompatible
cryptocurrencies.

*Argument:* string

*Default:* `scrypt`

*Supported:*

* `adaptive-n-factor` - Vertcoin-style adaptive N-factor scrypt.
  N-factor defaults to 11. Aliases: `adaptive-nfactor` (to be removed
  in future versions) and `nscrypt`.
* `scrypt` - Litecoin-style static N-factor scrypt.
* everything else - currently defaults to `scrypt`, subject to change
  without warning.


### nfactor

Overrides the default scrypt parameter N, specified as the factor of 2
(`N = 2^nfactor`).

*Argument:* whole number (>1).

*Default:* depends on `algorithm`; otherwise `10`.


### gridseed-options

GC3355-specific options can be specified via --gridseed-options or "gridseed-options" in the configuration file as a comma-separated list of sub-options:

baud - miner baud rate (default 115200)
freq - a choice of 250/400/450/500/550/600/650/700/750/800/850/900/950/1000
pll_r, pll_f, pll_od - fine-grained frequency tuning; see below
chips - number of chips per device (default 5)
per_chip_stats - print per-chip nonce generations and hardware failures
If pll_r/pll_f/pll_od are specified, freq is ignored, and calculated as follows:

Fin = 25
Fref = int(Fin / (pll_r + 1))
Fvco = int(Fref * (pll_f + 1))
Fout = int(Fvco / (1 << pll_od))
freq = Fout


## CLI-only options

*TODO*
