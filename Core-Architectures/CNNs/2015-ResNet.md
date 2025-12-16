# Deep Residual Learning for Image Recognition (ResNet)

- **論文連結**: [arXiv:1512.03385](https://arxiv.org/abs/1512.03385)
- **程式碼連結**: [PyTorch Official](https://pytorch.org/hub/pytorch_vision_resnet/)
- **發表會議/年份**: CVPR 2016 (Best Paper Award)
- **作者/機構**: Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun | Microsoft Research Asia-
- **關鍵字**: #Deep-Learning #CNN #Architecture #Backbone

---

## 1. TL;DR (一句話總結)
> 這篇論文提出了 **Residual Learning (殘差學習)** 架構，透過「捷徑 (Shortcut Connection)」讓神經網路可以疊得非常深（從 19 層突破到 152 層），解決了深層網路難以訓練的問題。

## 2. Problem & Motivation (問題與動機)
* **過去的方法有什麼缺點？**
    * 以前大家發現，當網路疊得太深（比如超過 20 層）時，準確率反而會下降（Degradation problem）。這不是因為過擬合 (Overfitting)，而是因為梯度消失 (Gradient Vanishing)，導致模型學不動了。
* **這篇論文想解決什麼核心痛點？**
    * 如何在加深網路層數的同時，還能保證模型容易訓練且準確率提升？

## 3. Method (方法與架構)
* **核心架構 (Residual Block)**:
    * 作者引入了一個概念：$H(x) = F(x) + x$
    * 「殘差」- 我們不讓網路直接學「怎麼把輸入轉成輸出」，而是改成學「這個轉換比原本輸入多了多少。
      舉例：如果你要學會從 2 變成 5，你其實只要知道增加了 +3。不是從頭學 5 是什麼，而是學 5 比 2 多了什麼！訓練起來更簡單、更快、更準。
    * **$x$ (Identity Mapping)**：就是那條「捷徑」，直接把輸入訊號傳到後面。
    * **$F(x)$ (Residual)**：模型只需要學習「輸入跟輸出之間的差異（殘差）」，這比直接學習完整的輸出容易得多。
* **為什麼有效？**：就像是讓模型「走後門」，如果深層的層數是多餘的，模型可以把 $F(x)$ 設為 0，這樣就退化成淺層網路，保證至少不會變差。

## 4. Experiments & Results (實驗結果)
* **Dataset**: ImageNet, CIFAR-10
* **Metrics**: Top-1 Error
* **結果**: ResNet-152 在 ImageNet 上達到了 3.57% 的錯誤率，超越了人類辨識能力，並且橫掃了當年的 ILSVRC 冠軍。

## 5
