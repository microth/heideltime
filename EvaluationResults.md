

## Introduction ##

This page contains the evaluation results of version 1.8 of **HeidelTime**.

**Operating system**: Ubuntu Linux

**Java version**: 1.6.0\_33

**Locale**: en\_GB (unless given in the workflow description in ReproduceEvaluationResults)

**Tokenization and POS-Tagging**: TreeTaggerWrapper, [JVnTextProWrapper](JVnTextProWrapper.md) (Vietnamese corpora: JVnTextPro 2.0, Maxent model), [StanfordPOSTaggerWrapper](StanfordPOSTaggerWrapper.md) (Arabic corpora: Stanford POS Tagger 3.3.1, arabic.tagger model), HunPosTaggerWrapper (Croatian WikiWarsHR: HunPos 1.0, Croatian model from 09.05.2013)

### ACE Tern 2004 Training Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 95.0%         | 78.9%      | 86.2%       |
| **Extraction (strict)** | 86.5%         | 71.8%      | 78.5%       |
| **Normalization (value)** | 87.0%         | 87.5%      | 87.3%       |
| **Extraction & Normalization (lenient + VAL)** | 82.7%         | 68.7%      | 75.0%       |
| **Extraction & Normalization (strict + VAL)** | 77.8%         | 64.6%      | 70.6%       |

### AncientTimes Arabic ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 83.33%        | 74.26%     | 78.53%      |
| **Extraction (relaxed)** | 93.33%        | 83.17%     | 87.96%      |

  * **Attribute value F1**: 83.77%
  * **Attribute type F1**: 87.96%

### AncientTimes German ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 86.58%        | 70.88%     | 77.95%      |
| **Extraction (relaxed)** | 95.30%        | 78.02%     | 85.80%      |

  * **Attribute value F1**: 80.36%
  * **Attribute type F1**: 85.20%

### AncientTimes English ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 84.39%        | 74.92%     | 79.37%      |
| **Extraction (relaxed)** | 95.17%        | 84.49%     | 89.51%      |

  * **Attribute value F1**: 84.27%
  * **Attribute type F1**: 88.11%

### AncientTimes Spanish ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 80.85%        | 72.04%     | 76.19%      |
| **Extraction (relaxed)** | 96.28%        | 85.78%     | 90.73%      |

  * **Attribute value F1**: 85.71%
  * **Attribute type F1**: 88.22%

### AncientTimes French ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 88.93%        | 76.14%     | 82.04%      |
| **Extraction (relaxed)** | 98.36%        | 84.21%     | 90.74%      |

  * **Attribute value F1**: 89.60%
  * **Attribute type F1**: 90.74%

### AncientTimes Italian ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 79.73%        | 75.11%     | 77.30%      |
| **Extraction (relaxed)** | 91.20%        | 86.03%     | 88.54%      |

  * **Attribute value F1**: 79.55%
  * **Attribute type F1**: 85.84%

### AncientTimes Dutch ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 81.67%        | 78.40%     | 80.00%      |
| **Extraction (relaxed)** | 94.17%        | 90.40%     | 92.24%      |

  * **Attribute value F1**: 88.16%
  * **Attribute type F1**: 88.16%

### AncientTimes Vietnamese ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 87.27%        | 82.76%     | 84.96%      |
| **Extraction (relaxed)** | 97.27%        | 92.24%     | 94.69%      |

  * **Attribute value F1**: 92.04%
  * **Attribute type F1**: 93.81%

### ACE Tern 2005 Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 88.7%         | 75.4%      | 81.5%       |
| **Extraction (strict)** | 75.6%         | 64.2%      | 69.5%       |
| **Normalization (value)** | 73.7%         | 76.3%      | 75.0%       |
| **Extraction & Normalization (lenient + VAL)** | 65.4%         | 55.5%      | 60.1%       |
| **Extraction & Normalization (strict + VAL)** | 61.5%         | 52.2%      | 56.5%       |

### Arabic test-150 Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 80.2%         | 90.8%      | 85.2%       |
| **Extraction (strict)** | 64.9%         | 73.6%      | 69.0%       |

### Arabic test-50 Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 79.7%         | 90.4%      | 84.7%       |
| **Extraction (strict)** | 62.8%         | 71.3%      | 66.8%       |

### Arabic test-50-star Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 91.9%         | 91.3%      | 91.6%       |
| **Extraction (strict)** | 84.8%         | 84.2%      | 84.5%       |
| **Normalization (value)** | 91.9%         | 91.9%      | 91.9%       |
| **Extraction & Normalization (lenient + VAL)** | 84.5%         | 83.9%      | 84.2%       |
| **Extraction & Normalization (strict + VAL)** | 80.1%         | 79.5%      | 79.8%       |

### Arabic test-50-star Corpus evaluated with TE3-Tools ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 80.99%        | 80.99%     | 80.99%      |
| **Extraction (relaxed)** | 90.91%        | 90.91%     | 90.91%      |

  * **Attribute value F1**: 82.23%
  * **Attribute type F1**: 84.76%

### I-CAB Test Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 92.7%         | 81.5%      | 86.8%       |
| **Extraction (strict)** | 64.1%         | 56.4%      | 60.0%       |
| **Normalization (value)** | 75.4%         | 78.1%      | 76.7%       |
| **Extraction & Normalization (lenient + VAL)** | 69.9%         | 61.5%      | 65.4%       |
| **Extraction & Normalization (strict + VAL)** | 51.2%         | 45.0%      | 47.9%       |

### TempEval2 Evaluation Corpus ###

| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 88.0%         | 86.0%      | 87.0%       |

  * **Attribute type**: 96.0%
  * **Attribute value**: 86.0%

### TempEval2 Spanish Evaluation Corpus ###

The Spanish TempEval2 Evaluation Corpus is essentially the same as TempEval 3 version further down in this document, but with some improvements, so please refer to that as it also uses our preferred evaluation method.

### TempEval2 Italian Evaluation Corpus ###

| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 93.1%         | 89.6%      | 91.3%       |

  * **Attribute type**: 98.0%
  * **Attribute value**: 94.0%

### TempEval 2 Italian Training Corpus evaluated with TE3-Tools ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 73.30%        | 88.72%     | 80.28%      |
| **Extraction (relaxed)** | 77.41%        | 93.69%     | 84.78%      |

  * **Attribute value F1**: 76.64%
  * **Attribute type F1**: 82.18%

### TempEval 2 Italian Test Corpus evaluated with TE3-Tools ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 77.93%        | 89.68%     | 83.39%      |
| **Extraction (relaxed)** | 83.45%        | 96.03%     | 89.30%      |

  * **Attribute value F1**: 81.18%
  * **Attribute type F1**: 85.61%

### TempEval 2 Chinese Original + CLEAN + IMPROVED Training Corpora ###
Original:
| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 96.0%         | 93.6%      | 94.8%       |

  * **Attribute type**: 93.0%
  * **Attribute value**: 80.0%
CLEAN:
| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 80.1%         | 95.4%      | 87.0%       |

  * **Attribute type**: 95.0%
  * **Attribute value**: 91.0%
IMPROVED:
| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 97.4%         | 95.3%      | 96.4%       |

  * **Attribute type**: 95.0%
  * **Attribute value**: 92.0%

### TempEval 2 Chinese Original + CLEAN + IMPROVED Evaluation Corpora ###
Original:
| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 93.8%         | 87.5%      | 90.5%       |

  * **Attribute type**: 93.0%
  * **Attribute value**: 70.0%
CLEAN:
| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 62.4%         | 91.8%      | 74.3%       |

  * **Attribute type**: 96.0%
  * **Attribute value**: 89.0%
IMPROVED:
| **Precision** | **Recall** | **F-Score** |
|:--------------|:-----------|:------------|
| 95.8%         | 89.3%      | 92.4%       |

  * **Attribute type**: 96.0%
  * **Attribute value**: 86.0%

### TimeBank 1.2 Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 92.0%         | 91.6%      | 91.8%       |
| **Extraction (strict)** | 86.0%         | 85.6%      | 85.8%       |
| **Normalization (value)** | 87.6%         | 87.6%      | 87.6%       |
| **Extraction & Normalization (lenient + VAL)** | 80.5%         | 80.2%      | 80.4%       |
| **Extraction & Normalization (strict + VAL)** | 76.6%         | 76.2%      | 76.4%       |

### WikiWars Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 95.8%         | 85.4%      | 90.3%       |
| **Extraction (strict)** | 88.2%         | 78.6%      | 83.1%       |
| **Normalization (value)** | 89.5%         | 90.1%      | 89.8%       |
| **Extraction & Normalization (lenient + VAL)** | 85.8%         | 76.4%      | 80.8%       |
| **Extraction & Normalization (strict + VAL)** | 81.1%         | 72.3%      | 76.4%       |

### WikiWarsDE Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 98.9%         | 88.3%      | 93.3%       |
| **Extraction (strict)** | 93.0%         | 83.0%      | 87.7%       |
| **Normalization (value)** | 88.5%         | 88.5%      | 88.5%       |
| **Extraction & Normalization (lenient + VAL)** | 87.5%         | 78.1%      | 82.5%       |
| **Extraction & Normalization (strict + VAL)** | 83.5%         | 74.5%      | 78.7%       |

### WikiWarsVN Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 92.1%         | 97.8%      | 94.8%       |
| **Extraction (strict)** | 72.9%         | 77.4%      | 75.1%       |
| **Normalization (value)** | 95.0%         | 95.0%      | 95.0%       |
| **Extraction & Normalization (lenient + VAL)** | 87.5%         | 92.9%      | 90.1%       |
| **Extraction & Normalization (strict + VAL)** | 69.2%         | 73.5%      | 71.2%       |

### WikiWarsVN Corpus evaluated with TE3-Tools ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 94.09%        | 94.09%     | 94.04%      |
| **Extraction (relaxed)** | 98.18%        | 98.18%     | 98.18%      |

  * **Attribute value F1**: 91.36%
  * **Attribute type F1**: 93.64%

### WikiWarsHR Corpus evaluated with TE3-Tools ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 88.86%        | 86.78%     | 87.81%      |
| **Extraction (relaxed)** | 92.62%        | 90.46%     | 91.53%      |

  * **Attribute value F1**: 80.80%
  * **Attribute type F1**: 89.67%

### Time4SCI Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 95.9%         | 65.6%      | 77.9%       |
| **Extraction (strict)** | 90.0%         | 61.6%      | 73.1%       |
| **Normalization (value)** | 89.5%         | 89.5%      | 89.5%       |
| **Extraction & Normalization (lenient + VAL)** | 85.8%         | 58.8%      | 69.8%       |
| **Extraction & Normalization (strict + VAL)** | 80.4%         | 55.0%      | 65.3%       |

### Time4SMS Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (lenient)** | 99.4%         | 91.3%      | 95.2%       |
| **Extraction (strict)** | 98.2%         | 90.2%      | 94.1%       |
| **Normalization (value)** | 97.1%         | 97.1%      | 97.1%       |
| **Extraction & Normalization (lenient + VAL)** | 96.5%         | 88.7%      | 92.4%       |
| **Extraction & Normalization (strict + VAL)** | 96.1%         | 88.3%      | 92.1%       |

### TempEval 3 AQUAINT Training Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 80.31%        | 81.69%     | 80.99%      |
| **Extraction (relaxed)** | 91.00%        | 92.57%     | 91.78%      |

  * **Attribute value F1**: 72.95%
  * **Attribute type F1**: 83.39%

### TempEval 3 TimeBank Training Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 85.61%        | 84.23%     | 84.91%      |
| **Extraction (relaxed)** | 92.31%        | 90.83%     | 91.57%      |

  * **Attribute value F1**: 79.24%
  * **Attribute type F1**: 88.81%

### TempEval 3 trainT3 Spanish Training Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 90.83%        | 81.44%     | 85.88%      |
| **Extraction (relaxed)** | 96.33%        | 86.38%     | 91.08%      |

  * **Attribute value F1**: 84.14%
  * **Attribute type F1**: 89.54%

### TempEval 3 Platinum English Evaluation Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 83.85%        | 78.99%     | 81.34%      |
| **Extraction (relaxed)** | 93.08%        | 87.68%     | 90.30%      |

  * **Attribute value F1**: 77.61%
  * **Attribute type F1**: 82.09%

### TempEval 3 Spanish Evaluation Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 91.48%        | 80.90%     | 85.87%      |
| **Extraction (relaxed)** | 96.02%        | 84.92%     | 90.13%      |

  * **Attribute value F1**: 85.33%
  * **Attribute type F1**: 87.47%

### French TimeBank 1.1 Corpus ###

| | **Precision** | **Recall** | **F-Score** |
|:|:--------------|:-----------|:------------|
| **Extraction (strict)** | 86.81%        | 85.15%     | 85.99%      |
| **Extraction (relaxed)** | 91.85%        | 90.12%     | 90.97%      |

  * **Attribute value F1**: 73.63%
  * **Attribute type F1**: 82.66%

### EVALITA 2014 Test Corpus ###

| | **Recall** | **Precision** | **F-Score** | Type F1 | Value F1 |
|:|:-----------|:--------------|:------------|:--------|:---------|
| **Strict extraction/normalization** | 79.0%      | 85.1%         | 82.0%       | 78.5%   | 71.0%    |
| **Relaxed extraction/normalization** | 86.1%      | 92.7%         | 89.3%       | 84.0%   | 75.0%    |