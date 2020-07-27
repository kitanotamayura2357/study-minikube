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

