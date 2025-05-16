# 🖥️ Terraformを用いたAWS EC2インフラ構築・公開手順サンプル（東京リージョン対応）

このリポジトリは、Terraformを使ってAWSの東京リージョン（ap-northeast-1）にシンプルなEC2インスタンス公開環境を構築するサンプルです。

VPC（Virtual Private Cloud／仮想ネットワーク）
　→ クラウド上に“自分専用のネットワーク空間”を作るため

パブリックサブネット
　→ インターネットからアクセス可能な領域（EC2配置先）を作るため

インターネットゲートウェイ（IGW）
　→ VPC内のサーバーがインターネットと通信できるようにするため

ルートテーブル
　→ サブネットからインターネットへの通信経路（ルート）を設定するため

セキュリティグループ（SG）
　→ サーバー（EC2）の通信をファイアウォールで制御し、必要なポート（SSH/HTTP）のみ許可するため

SSHキーペア
　→ EC2サーバーに安全にログイン（SSH接続）できるようにするため

EC2インスタンス
　→ 実際に動作するLinuxサーバー（クラウド上の仮想マシン）を立ち上げるため
---

## 📦 ディレクトリ構成

simple-ec2/
├── main.tf # メインインフラ定義（VPC, サブネット, SG, EC2など）
├── variables.tf # 変数定義ファイル
├── terraform.tfvars # 変数の実際の値
├── outputs.tf # 出力情報（EC2のパブリックIP等）
├── .gitignore # 管理除外ファイルリスト
└── README.md # このファイル

yaml
コピーする
編集する

---

## 🚀 構築手順

### 1. 事前準備

- AWS CLIのセットアップ（`aws configure`）
- Terraformインストール済み
- AWS上でキーペア作成済み（`terraform.tfvars`の`key_name`に登録名を記入）

### 2. デプロイ手順

```bash
terraform init
terraform plan -var-file="terraform.tfvars"
terraform apply -var-file="terraform.tfvars"
