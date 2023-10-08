# EcsAutoStartAndStop

## 概要

ECSサービスを自動起動・停止するEventBridge ScheculderのCFnテンプレート。

#### 自動起動の仕組み
- EventBridge Schedulerが指定された時間になったらをUpdateService APIを実行し、指定のタスク起動数に変更する。

#### 自動停止の仕組み
- EventBridge Schedulerが指定された時間になったらをUpdateService APIを実行し、タスク起動数を0に変更する。

## EventBridge Schedulerの作成手順

### [EventBridge.yml](eventbridge/EventBridge.yml)からスタックを作成する。

#### オプション
CAPABILITY_IAMを指定する

#### パラメータ
| パラメータ名 | 説明 | 例 | 
| ---- | ---- | ---- | 
| StartServiceCron | 自動起動の開始時間(cron式) | StartServiceCron |
| StopServiceCron | 自動停止の開始時間(cron式) | StartServiceCron |
| ClusterName | 自動起動・停止対象のECS Cluster名 | test-app-claster |
| ServiceName | 自動起動・停止対象のECS Service名 | ecs-service |
| DesiredCount | タスク起動数 | 2 |


## サンプルECS作成手順

### [ECR.yml](aws/ecs-sample/ecs/ECR.yml)からECRを作成する。

### docker/配下のファイルからnginxイメージを作成し、ECRにプッシュする。

### ecs-sample/配下のymlから以下の順にスタックをし、ECSを起動する。
1. [VPC-Subnet.yml](aws/ecs-sample/network/VPC-Subnet.yml)
2. [RouteTable.yml](aws/ecs-sample/network/RouteTable.yml)
3. [SecurityGroup.yml](aws/ecs-sample/security/SecurityGroup.yml)
4. [VpcEndpoint.yml](aws/ecs-sample/network/VpcEndpoint.yml)
5. [ECS-Task.yml](aws/ecs-sample/ecs/ECS-Task.yml)
6. [ALB.yml](aws/ecs-sample/alb/ALB.yml)
7. [ECS-Service.yml](aws/ecs-sample/ecs/ECS-Service.yml)


