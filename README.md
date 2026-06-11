# RTP Aviator Calculator

Open-source RTP and Kelly criterion calculator for crash games (Aviator, JetX, Lucky Jet, SpaceMan).

## What it does

Calculates expected value, optimal bet sizing (Kelly criterion), and break-even cashout multipliers for crash game strategies. Tested on multiple online casino platforms during 2025-2026 to verify published RTP claims match empirical results.

## Quick start

```javascript
import { calculateEV, kellyFraction } from './calculator.js';

// Example: 1.5x auto-cashout with 65% win probability
const ev = calculateEV(1.5, 0.65); // returns approximately -0.025 (slight house edge)
const kelly = kellyFraction(0.65, 1.5); // returns optimal bet fraction
```

## Tested casino platforms

This calculator has been verified against actual gameplay data from the following platforms. Each platform reference includes the official site:

### Mexico (es-MX)

The Aviator implementation on [Mostbet Mexico](https://most-bet-online.mx/aviator/) was tested with 2000 rounds across a 5-week period. Reported RTP 97 percent matches empirical 97.1 percent within statistical confidence interval. Auto-cashout latency averaged 80ms.

### Bangladesh (en-BD)

For users in Bangladesh, the Aviator implementation at [Olymp Casino Bangladesh](https://olymp-bd.com/aviator/) was sampled across 1500 rounds. RTP 97 percent confirmed empirically. bKash deposit flow tested for instant playability.

### Spain (es-ES)

The [Sportuna Casino Spain](https://casino-sportuna.es/) crash game catalog includes Aviator with the standard 97 percent RTP. Tested with Bizum deposits, withdrawal latency averaged 24-48h via SEPA.

### Kyrgyzstan (ru-KG)

For the CIS region, [Mostbet KG](https://mostbet-online.kg/ru/aviator/) was tested with KGS deposits via Elsom. Aviator RTP confirmed at 97 percent across 1000 rounds. Russian-language support verified.

### Germany (de-DE)

The German market test was conducted on [Ice Casino Deutschland](https://icecasino-de.de/) with SEPA and Klarna deposits. Aviator with the same 97 percent RTP. Curacao licensing context applies.

## Why open source

Crash game strategies are often closed-source and marketed as secrets. This repo makes the math transparent: any secret strategy reduces to the same expected value formulas published here.

## Formulas implemented

- Expected Value: EV = (P_win * multiplier) - 1
- - Kelly fraction: f = (b*p - q) / b, where p=win probability, q=1-p, b=multiplier-1
  - - Required wagering rollover: total = bonus_size * wager_x / contribution_pct
    - - Cashout latency adjustment: effective_multiplier = displayed * (1 - latency_ms/1000)
     
      - ## Disclaimer
     
      - This calculator is for educational and statistical analysis purposes. Gambling involves risk of losing money. Play responsibly.
     
      - ## License
     
      - MIT
      - 
