
# 環境建置步驟記錄

## MacOS

### 需安裝的工具
1. Homebrew

#### 安裝 Homebrew
1. 參考：[官方網站](https://brew.sh/zh-tw/)
2. 需要在 ~/.zshrc 加入環境變數
   ```sh
   export PATH="/opt/homebrew/bin:$PATH"
   ```

## Python

### 需安裝與設定的工具
1. pyenv
2. virtualenv

### 每個工具的設定步驟

#### 1. 安裝 pyenv
- 參考:[官方GitHub](https://github.com/pyenv/pyenv?tab=readme-ov-file#homebrew-in-macos)
- 安裝 python：
  ```sh
  pyenv install -l # 看可安裝的版本有哪些
  ```
  ```sh
  pyenv install 3.12 # 進行安裝
  ```
- 設定環境變數

#### 2. 安裝 virtualenv
- 啟用 python 環境：
  ```sh
  pyenv shell 3.12
  ```
- 使用 pip 安裝 virtualenv：
    ```sh
    pip install virtualenv
    ```
- 安裝 pyenv-virtualenv [參考] (https://github.com/pyenv/pyenv-virtualenv)：
  ```sh
  git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
  ```
  ```sh
  echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
  ```
- 建立一個新的虛擬環境：
    ```sh
    virtualenv myenv
    ```
- 啟動虛擬環境：
    ```sh
    source myenv/bin/activate
    ```

#### 3. 第三方套件問題解決
- pymssql 
  - symbol not found in flat namespace '_bcp_batch'
    ```sh
    brew install FreeTDS 
    export LDFLAGS="-L/opt/homebrew/lib -L/opt/homebrew/opt/openssl/lib"
    export CFLAGS="-I/opt/homebrew/include"
    export CPPFLAGS="-I/opt/homebrew/opt/openssl@3/include"
    pip uninstall pymssql -y
    pip install pymssql==2.2.8 --no-binary :all:
    ```

## JAVA

### 需安裝與設定的工具
1. JDK (Java Development Kit)
2. Maven
3. IDE (如 IntelliJ IDEA 或 Eclipse)

### 每個工具的設定步驟

#### 1. 安裝 JDK
- 從 [Adoptium](https://adoptium.net/) 下載並安裝 17 版 Java
- OS 選 MacOS, M 系列晶片選 aarch64
- 安裝完成後，使用以下指令確認安裝是否成功：
    ```sh
    java -version
    ```

#### 2. 安裝 Maven
- 安裝指令
  ```sh
  brew install maven
  ```
- 安裝完成後，使用以下指令確認安裝是否成功：
    ```sh
    mvn -version
    ```
