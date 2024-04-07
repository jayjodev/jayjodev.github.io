---
title: "Resolving the 'zsh: command not found: go' Error on macOS After Installing Go with Brew"

author: Jay Jo
date: 2024-04-07 00:00:00 +09:00
categories: [ai]
tags: [ai]
---

# PyTorch를 이용한 AI 모델 학습 환경 설정

PyTorch는 딥러닝 모델을 구축하고 학습시키기 위한 인기 있는 라이브러리 중 하나입니다. 모델 학습 속도를 높이기 위해 GPU를 사용하는 것이 일반적이며, PyTorch는 NVIDIA GPU를 사용할 때 CUDA를 활용합니다. 최근에는 Apple Silicon(M1/M2/M3 칩)을 사용하는 Mac에서 Metal Performance Shaders(MPS) 백엔드를 사용할 수도 있게 되었습니다. 여기서는 PyTorch를 사용하여 현재 시스템에서 사용 가능한 최적의 장치를 자동으로 선택하고 사용하는 방법을 소개합니다.

## 코드 설명

```python
import torch

device = "cuda" if torch.cuda.is_available() else "mps" if torch.backends.mps.is_available() else "cpu"
print("Using device:", device)
```

라이브러리 임포트: 우선, PyTorch 라이브러리를 임포트합니다. 이 코드는 torch라는 이름으로 PyTorch 라이브러리에 접근할 수 있게 합니다.
장치 결정: torch.cuda.is_available() 함수는 시스템에 CUDA를 사용할 수 있는 NVIDIA GPU가 있는지 확인합니다. 이 함수가 True를 반환하면, device 변수는 "cuda"로 설정됩니다. 만약 CUDA를 사용할 수 있는 GPU가 없고, Apple Silicon 기반의 시스템에서 실행 중이며 MPS가 사용 가능하면, torch.backends.mps.is_available() 함수가 True를 반환하여 device는 "mps"로 설정됩니다.

두 조건 모두 해당하지 않으면, device는 "cpu"로 설정됩니다.
* 장치 출력: 선택된 장치가 어떤 것인지 사용자에게 알리기 위해 print 함수를 사용합니다. 이는 코드를 실행하는 사람이 현재 어떤 장치를 사용하고 있는지 명확하게 인식할 수 있게 해줍니다.

실행 결과
* NVIDIA GPU가 있는 시스템: Using device: cuda
* Apple Silicon 기반 시스템: Using device: mps

GPU가 없는 시스템 또는 다른 유형의 GPU: Using device: cpu
이 코드 스니펫은 PyTorch 기반의 AI 모델을 개발할 때 초기 설정 단계에서 매우 유용합니다. 각 사용자의 환경에 맞게 최적의 장치를 자동으로 선택하여 효율적인 모델 학습을 도모할 수 있게 합니다.

활용 예시
```
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset, random_split

# 장치 설정
device = "cuda" if torch.cuda.is_available() else "mps" if torch.backends.mps.is_available() else "cpu"

# 간단한 데이터셋 생성
X = torch.randn(100, 10)  # 100개의 데이터 포인트, 각각 10개의 특성을 가짐
y = torch.randint(0, 2, (100,))  # 0 또는 1의 값을 가지는 100개의 레이블

# 전체 데이터셋을 생성
dataset = TensorDataset(X, y)

# 데이터를 학습 세트와 평가 세트로 분할
train_size = int(0.8 * len(dataset))
test_size = len(dataset) - train_size
train_dataset, test_dataset = random_split(dataset, [train_size, test_size])

# DataLoader를 사용하여 데이터 로더 생성
train_loader = DataLoader(train_dataset, batch_size=10, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=10, shuffle=False)

# 신경망 모델 정의
class SimpleNet(nn.Module):
    def __init__(self):
        super(SimpleNet, self).__init__()
        self.fc1 = nn.Linear(10, 5)
        self.fc2 = nn.Linear(5, 2)

    def forward(self, x):
        x = torch.relu(self.fc1(x))
        x = self.fc2(x)
        return x

# 모델, 손실 함수, 최적화 함수 초기화 및 장치 설정
model = SimpleNet().to(device)
criterion = nn.CrossEntropyLoss()
optimizer = optim.SGD(model.parameters(), lr=0.01)

# 모델 학습
model.train()
for epoch in range(10):
    for inputs, labels in train_loader:
        inputs, labels = inputs.to(device), labels.to(device)
        optimizer.zero_grad()
        outputs = model(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()

# 모델 평가
model.eval()
correct = 0
total = 0
with torch.no_grad():
    for inputs, labels in test_loader:
        inputs, labels = inputs.to(device), labels.to(device)
        outputs = model(inputs)
        _, predicted = torch.max(outputs.data, 1)
        total += labels.size(0)
        correct += (predicted == labels).sum().item()

accuracy = correct / total
print(f'Accuracy: {accuracy * 100}%')
```

