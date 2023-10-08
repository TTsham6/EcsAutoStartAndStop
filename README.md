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

### ecs-sample配下のymlから以下の順にスタックを作成する。
1. network/VPC-Subnet.yml
2. network/RouteTable.yml
3. security/SecurityGroup.yml
4. network/VpcEndpoint.yml
5. ecs/ECR.yml
6. ecs/ECS-Task.yml
7. alb/ALB.yml
8. ecs/ECS-Service.yml


