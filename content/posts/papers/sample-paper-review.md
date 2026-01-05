---
title: "Sample Paper Review"
date: 2025-12-16T13:10:03Z
draft: false
categories: ["papers"]
tags: ["deep learning", "computer vision"]

# 논문 정보
paper:
  title: "Attention is All You Need"
  authors: ["Vaswani et al."]
  venue: "NeurIPS"
  year: 2017
  arxiv_id: "1706.03762"
  url: "https://arxiv.org/abs/1706.03762"

# AI 친화적 메타데이터
difficulty: "intermediate"
summary: "Transformer 아키텍처를 제안한 획기적인 논문"
keywords: ["transformer", "attention", "sequence-to-sequence"]
---

## 논문 정보

- **Title**: Attention is All You Need
- **Authors**: Vaswani et al.
- **Venue**: NeurIPS 2017
- **Year**: 2017
- **Link**: https://arxiv.org/abs/1706.03762

## 핵심 요약

이 논문은 RNN이나 CNN 없이 오직 attention 메커니즘만을 사용하는 Transformer 아키텍처를 제안합니다. Self-attention을 통해 시퀀스의 모든 위치를 병렬로 처리할 수 있어 학습 속도가 빠르고, 긴 의존성을 효과적으로 학습할 수 있습니다.

## 주요 내용

### 문제 정의

기존 RNN 기반 모델은 순차적 처리로 인해 병렬화가 어렵고, 긴 시퀀스에서 의존성 학습이 어려웠습니다.

### 제안 방법

Multi-head self-attention과 position-wise feed-forward 네트워크로 구성된 encoder-decoder 구조를 제안했습니다.

### 실험 결과

기계 번역 태스크에서 SOTA를 달성하면서도 학습 시간을 크게 단축했습니다.

## 개인 평가

### 장점

병렬 처리가 가능하여 학습 효율이 높고, 현대 NLP의 기반이 되었습니다.

### 한계

긴 시퀀스에서 메모리 사용량이 많아질 수 있습니다.

### 적용 가능성

NLP뿐만 아니라 비전, 음성 등 다양한 도메인에 적용 가능합니다.

## 관련 자료

- [Original Paper](https://arxiv.org/abs/1706.03762)
- [Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
