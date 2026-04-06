---
title:"贏家的詛咒"
categories: [stats]
tags: [pvalue]
---
-不要只相信一次的 RCT（尤其是單一中心、人數少的）
https://www.facebook.com/share/p/1EgJmj6iZ3/?mibextid=wwXIfr

收縮估計
Evaluating a shrinkage estimator for the treatment effect in clinical trials 23
https://onlinelibrary.wiley.com/doi/10.1002/sim.9992
R code: https://guhstats.blogspot.com/2024/01/a-new-look-at-p-values-for-randomized.html

請注意觀察性研究的統計檢定力、95% 信賴區間包含真值的機率、再現性、訊號雜訊比都比 RCT 低很多；效果量高估的程度、正負符號的錯誤率都比 RCT 高很多。原因是：非隨機抽樣、選擇性偏差、低樣本數、無法消除干擾因子等。

用 https://egon.stats.ucl.ac.uk/projects/ACCEPT/ 評估虛無假設為真的機率。

常見的統計錯誤
https://m.facebook.com/story.php?story_fbid=10231405766995769&id=1484893288&mibextid=cr9u03

贏家的詛咒（高估效果量）
https://www.facebook.com/1484893288/posts/10227723788148599/?mibextid=cr9u03

低統計檢定力的研究比較容易有假陰性（第二型錯誤）的結果，也比較容易有假陽性（第一型錯誤）的結果
https://www.facebook.com/1484893288/posts/10224572172840186/?mibextid=cr9u03

A New Look at p-Values for Randomized Clinical Trials 23
http://www.stat.columbia.edu/~gelman/research/published/pval_RCTs_rev3.pdf
治療效果 b 的標準常態（z）分布：z=(b-x̄)/sem, z 分布的平均值是 0、sd 是 1，z= ±1.96 時的 p=0.05，sem=sd/√n。SNR=true effect/sem=z value + z 分布的 noise, p=2Φ(-|z|), power=Φ(-1.96-SNR)+1-Φ(1.96-SNR); 標準常態累積機率 Φ: pnorm(x)
由 23551 篇 Cochrane 系統性文獻回顧的 RCT 及其模擬研究中發現平均的統計檢定力是 13%（只有 12% 的統計檢定力是 80%），因此有高的假陽性、假陰性。原因可能是真的效果量很低、人數不足。

假設的真值 β、β 的估計值 b、b 的標準誤 s，當 SNR=2.8 (3.24) 時，統計檢定力是 0.8 (0.9)。

z=b/s, SNR=β/s
b= β+N(0, s), z= SNR+N(0, s)

1. p ≥ 0.05: 平均高估效果量 20%，另一個再現性研究發現 p ≥ 0.05 且正負符號一致的機率是 57% (1-0.13/0.3)。95% 信賴區間包含真值的機率平均是 97%，正負符號的錯誤率是 30%。

2. p < 0.05: 平均高估效果量 29%，另一個再現性研究發現 p < 0.05 且正負符號一致的機率是 60%。95% 信賴區間包含真值的機率平均是 90%，正負符號的錯誤率是 2%。

p=0.01-0.05 時：平均高估效果量 56%，至少高估效果量 5%，1/4 高估效果量 180%，另一個再現性研究發現 p < 0.05 且正負符號一致的機率是 37%。95% 信賴區間包含真值的機率是 90%，正負符號的錯誤率是 5%。

p=0.005-0.01 時，平均高估效果量 40%，至少高估效果量 4%，1/4 高估效果量 125%，另一個再現性研究發現 p < 0.05 且正負符號一致的機率是 48%。95% 信賴區間包含真值的機率是 87%，正負符號的錯誤率是 2%。

p=0.001-0.005 時，平均高估效果量 35%，至少高估效果量 4%，1/4 高估效果量 95%，另一個再現性研究發現 p < 0.05 且正負符號一致的機率是 58%。95% 信賴區間包含真值的機率是 87%，正負符號的錯誤率是 1%。

p<0.001 時，平均高估效果量 16%，至少高估效果量 0%，1/4 高估效果量 44%，另一個再現性研究發現 p < 0.05 且正負符號一致的機率是 86%。95% 信賴區間包含真值的機率是 89%，正負符號的錯誤率是 0%。

z=估計的效果量平均值/標準誤

在系統性文獻回顧中，z 值的分布是 4 個訊號雜訊比（真的效果量平均值/標準誤）分布 +標準誤的混合。

假設效果量平均值=0，而且沒有偏差（系統性誤差），那麼 z 值的分布就是一個標準常態分布：± 1z (1.96) 內的雙尾檢定 p 值都是 ≥ 0.05 的，而訊號雜訊比的絕對值則是呈現半常態分布（只有正值的常態分布）。

假設雙尾檢定的第一型錯誤率 α 是 0.05:
• 如果 RCT 的統計檢定力是 0.2，那麼效果量就是 1.1 個標準誤。
• 如果 RCT 的統計檢定力是 0.5，那麼效果量就是 1.96 個標準誤。
• 如果 RCT 的統計檢定力是 0.8，那麼效果量就是 2.8 個標準誤。
• 如果統計檢定力是 0.9，那麼效果量就是 3.2 個標準誤。

Bayesian moving from defense to offense: “I really think it’s kind of irresponsible now not to use the information from all those thousands of medical trials that came before. Is that very radical?” 23
https://statmodeling.stat.columbia.edu/2023/12/23/bayesians-moving-from-defense-to-offense-i-really-think-its-kind-of-irresponsible-now-not-to-use-the-information-from-all-those-thousands-of-medical-trials-that-came-before-is-that-very/

Explaining that line, “Bayesians moving from defense to offense” 23
https://statmodeling.stat.columbia.edu/2023/12/24/explaining-that-line-bayesians-moving-from-defense-to-offense/
