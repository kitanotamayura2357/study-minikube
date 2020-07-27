# study-minikube

Kubernetes, Minikubeについての学習を記録する


参考  
https://kubernetes.io/ja/docs/tasks/tools/install-kubectl/  
https://kubernetes.io/ja/docs/tasks/tools/install-minikube/

OS:Mac


## macOSへkubectlをインストールする

### curlを使用してmacOSへkubectlのバイナリをインストールする

ダウンロード
```
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
```
kubectlバイナリを実行可能にする
```
chmod +x ./kubectl
```

バイナリをPATHの中に移動させてください。
```
mv ./kubectl /usr/local/bin/kubectl
```

### Homebrewを使用してmacOSへインストールする

インストールコマンドを実行
```
brew install kubectl 
```

インストールしたバージョンが最新であることを確認
```
kubectl version --client
```

## Minikubeのインストール

仮想化がmacOSでサポートされているかどうかを確認
```
sysctl -a | grep -E --color 'machdep.cpu.features|VMX'
```
出力にVMXが表示されている場合（色付けされているはずです）、VT-x機能がマシンで有効になっています。


ハイパーバイザーのインストール 
以下のいずれかのハイパーバイザーをインストールする  
- HyperKit
- VirtualBox
- VMware Fusion


バーチャルボックスのインストール

https://pc-karuma.net/mac-virtualbox-install/



Minikubeのインストール

```
brew install minikube
```

### インストールの確認

ハイパーバイザーとMinikube両方のインストール成功を確認するため、以下のコマンドをローカルKubernetesクラスターを起動するために実行
```
minikube start --vm-driver=<driver_name>
```
<driver_name>はインストールしたハイパーバイザーの名前を小文字で入力（virtualboxなど）


minikube startが完了した場合、次のコマンドを実行してクラスターの状態を確認
```
minikube status
```

クラスターが起動している場合は以下のようになる  

```
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

クラスターの停止

```
minikube stop
```

停止している時には以下のようになる

```
minikube
type: Control Plane
host: Stopped
kubelet: Stopped
apiserver: Stopped
kubeconfig: Stopped
```

### ローカル状態のクリーンアップ 


ローカル状態のminikubeをクリアする
```
minikube delete
```



## Minikubeを使用してローカル環境でKubernetesを動かす


Minikubeを起動する
```
$ minikube start
```

```
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10
```

```
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```

## kubectlの任意の設定 

### シェルの自動補完を有効にする

#### bashのアップグレード 

bashのバージョンが4.1以降の使用を前提とする.
バージョンの確認

```
echo $BASH_VERSION
```

バージョンアップ
```
brew install bash
```

以下あとで。。。
https://kubernetes.io/ja/docs/tasks/tools/install-kubectl/#install-kubectl-on-macosを参照する

