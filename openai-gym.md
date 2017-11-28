# OpenAI Gym

## 概要

- 強化学習アルゴリズムのデモの実装を提供する Python ライブラリ。

## 特徴

- 多種多様なデモルーチンが用意されている。
  - 倒立振子, 車の山登り問題, ...
  - 各デモルーチンは Environment と呼ばれる。
- どのデモも同じ要領で組み込める（はず）。
  - 各 Environment は統一したインタフェイスで実装されている。
  ```
  import gym
  env = gym.make('CartPole-v0') # 使いたい Environment を名前で指定する
  env.reset()
  for _ in range(1000):
    env.render()
    env.step(env.action_space.sample()) # take a random action
  ```
- デモは GUI プログラムとして動作する。
  - 描画処理も併せて実装されている。

## インストール

- 最小インストールと完全インストールがある。
- 完全インストールには、依存パッケージのインストールが必要になる。
  ```
  # 手順（最小インストール）
  git clone https://github.com/openai/gym
  cd gym
  pip install -e .
  ```
  ```
  # 手順（完全インストール）
  brew install cmake boost boost-python sdl2 swig wget
  git clone https://github.com/openai/gym
  cd gym
  pip install -e '.[all]'
  ```

## リソース

- [gym/README.rst at master · openai/gym](https://github.com/openai/gym/blob/master/README.rst)
- [OpenAI Gym (docs)](https://gym.openai.com/docs/)
