# 🖥️ Simple EC2構築（Terraform / 東京リージョン）

このリポジトリは、Terraformを使ってAWSの東京リージョン（ap-northeast-1）にシンプルなEC2インスタンス公開環境を構築するサンプルです。

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