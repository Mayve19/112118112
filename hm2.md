# 專案分析

## 1. 任務資料

以下是從圖3-27中提取並結構化的任務清單，包含任務編號、說明、需時（天）以及前置任務：

```
|   任務編號 | 說明     |   需時(天) | 前置任務   |
|-------:|:-------|--------:|:-------|
|      1 | 研擬計畫   |       1 | -      |
|      2 | 任務分配   |       4 | 1      |
|      3 | 取得硬體   |      17 | 1      |
|      4 | 程式開發   |      70 | 2      |
|      5 | 安裝硬體   |      10 | 3      |
|      6 | 程式測試   |      30 | 4      |
|      7 | 撰寫使用手冊 |      25 | 5      |
|      8 | 轉換檔案   |      20 | 5      |
|      9 | 系統測試   |      25 | 6      |
|     10 | 使用者訓練  |      20 | 7,8    |
|     11 | 使用者測試  |      25 | 9,10   |
```

## 2. 關鍵路徑分析 (PERT/CPM)

關鍵路徑法（Critical Path Method, CPM）用於分析專案活動、識別關鍵路徑，並確定專案的最短完成時間。以下是詳細的關鍵路徑分析結果：

```
|   任務編號 | 說明     |   需時(天) | 前置任務   |   最早開始(ES) |   最早完成(EF) |   最晚開始(LS) |   最晚完成(LF) |   浮時(Slack) | 是否關鍵路徑   |
|-------:|:-------|--------:|:-------|-----------:|-----------:|-----------:|-----------:|------------:|:---------|
|      1 | 研擬計畫   |       1 | -      |          0 |          1 |          0 |          1 |           0 | 是        |
|      2 | 任務分配   |       4 | 1      |          1 |          5 |          1 |          5 |           0 | 是        |
|      3 | 取得硬體   |      17 | 1      |          1 |         18 |         58 |         75 |          57 | 否        |
|      4 | 程式開發   |      70 | 2      |          5 |         75 |          5 |         75 |           0 | 是        |
|      5 | 安裝硬體   |      10 | 3      |         18 |         28 |         75 |         85 |          57 | 否        |
|      6 | 程式測試   |      30 | 4      |         75 |        105 |         75 |        105 |           0 | 是        |
|      7 | 撰寫使用手冊 |      25 | 5      |         28 |         53 |         85 |        110 |          57 | 否        |
|      8 | 轉換檔案   |      20 | 5      |         28 |         48 |         90 |        110 |          62 | 否        |
|      9 | 系統測試   |      25 | 6      |        105 |        130 |        105 |        130 |           0 | 是        |
|     10 | 使用者訓練  |      20 | 7,8    |         53 |         73 |        110 |        130 |          57 | 否        |
|     11 | 使用者測試  |      25 | 9,10   |        130 |        155 |        130 |        155 |           0 | 是        |
```

**專案總工期**: 155 天

**關鍵路徑**: 研擬計畫 -> 任務分配 -> 程式開發 -> 程式測試 -> 系統測試 -> 使用者測試

## 3. PERT/CPM 網路圖

以下是根據任務資料生成的PERT/CPM網路圖。圖中以紅色粗體標示的任務為關鍵路徑上的活動。

![PERT/CPM 網路圖](https://private-us-east-1.manuscdn.com/sessionFile/DsiGAMsiGs7ePM2RPYZJ6n/sandbox/c9Rn9xcCvIh1GquLemS2j1-images_1759285570516_na1fn_L2hvbWUvdWJ1bnR1L3BlcnRfY3BtX2RpYWdyYW0.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvRHNpR0FNc2lHczdlUE0yUlBZWko2bi9zYW5kYm94L2M5Um45eGNDdkloMUdxdUxlbVMyajEtaW1hZ2VzXzE3NTkyODU1NzA1MTZfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwzQmxjblJmWTNCdFgyUnBZV2R5WVcwLnBuZyIsIkNvbmRpdGlvbiI6eyJEYXRlTGVzc1RoYW4iOnsiQVdTOkVwb2NoVGltZSI6MTc5ODc2MTYwMH19fV19&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=h0cO5IqdtWVSOQQBq5-jXnmh~yAUpngvTQj4JM90H1j18IJXsNWUG7A3B7Tas0J~g4yBXhEU3y2UqEGkcn-DXmGXrGYM1Qs-iXk0nJZNzTM2Ujm1ujqF0JGAkc0jERKq46L09tsqenMgLVJkj0j~2J3pvUytREhJhkw51~FKWCGVIWLQ-GvcHgZEtaqjrh4ZnnyhkjOnMWOqnn3supOqGRp~tU97qs0UvjiL~hVjNiT34I6X7Vjk56Bdzfd79dplOLhNXFOE6hNYlzYL87TDsvE-RCytgBXf4~i5SOYvjqST4v02OTUdtyWjmEg5YwKgmsqY32zS0AWy~OXHuhZ7LQ__)

## 4. 甘特圖

甘特圖提供了一個視覺化的專案時間表，顯示了每個任務的開始和結束日期，以及它們的持續時間。關鍵路徑上的任務在此圖中也特別標示出來。

![甘特圖](https://private-us-east-1.manuscdn.com/sessionFile/DsiGAMsiGs7ePM2RPYZJ6n/sandbox/c9Rn9xcCvIh1GquLemS2j1-images_1759285570518_na1fn_L2hvbWUvdWJ1bnR1L2dhbnR0X2NoYXJ0.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvRHNpR0FNc2lHczdlUE0yUlBZWko2bi9zYW5kYm94L2M5Um45eGNDdkloMUdxdUxlbVMyajEtaW1hZ2VzXzE3NTkyODU1NzA1MThfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyZGhiblIwWDJOb1lYSjAucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=pJSlk9nZOySZPvhLowniMk6XlXgvW-8QM4WAV0ZwUbDhyaazbXRtSQ0EclL7drYTvKeshMPjDBfXXDrSsgpKYWvjOVaEBLwfWHjYSIa6x0M6uTKqnu7XmfGa4XKKHBtDM9oLDvbviggllcP-qf~r14d5iSaN1jWXXBm5jz9AeUsqIRnUEcbQMmlQth8~ZfMw04gfiRYpa3xqnM1sYpwJbb~8442g3nlylio2xR6iRalwgdvNObx8hDTJu6QFPjpn69Isv2BgCuABLC~XVploeIrvfco-fsXIgxDV~xIMeUo3ATCT4th8NfQ~hc55Y3Ow-9f8YTljKw1F2I7QJr~uHg__)

