
# ターミナル

1. git clone https://github.com/TarouTanakaYokohama/uMy-foods.git
2. docker-compose build
3. docker-compose up -d
4. docker exec -it flutter bash
5. cd ${APP_CODE_PATH_CONTAINER} ; flutter create .
6. flutter run -d web-server --web-port=${WEB_SERVER_PORT} --web-hostname 0.0.0.0

# ブラウザで

- http://localhost:8888

# webデプロイ

1. docker-compose down
2. docker-compose build
3. firebase login --no-localhost
   1. 「? Allow Firebase to collect CLI usage and error reporting information? (Y/n)」に「Y」を入力
   2. URLをcontrolキーを押しながらクリックし、googleログインを実行
   3. 「? Paste authorization code here:」にブラウザに表示されたコードを入力
4. cd workspace/
5. firebase init
   1. 「Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys」にspaceキーを押しEnter
   2. 「Use an existing project」を選択しEnter
   3. 使用するプロジェクトを選択しEnter
   4. 「? What do you want to use as your public directory?」に「build/web」を入力
   5. 「? Configure as a single-page app (rewrite all urls to /index.html)?」に「N」を入力
   6. 「? Set up automatic builds and deploys with GitHub?(y/N)」に「N」を入力
   7. 「? File build/web/404.html already exists. Overwrite? (y/N)」に「N」を入力
   8. 「? File build/web/index.html already exists. Overwrite?」に「N」を入力
6. flutter create .
7. flutter build web --release --web-renderer html
8. firebase deploy

# 2回目以降デプロイする場合

- webデプロイの6から始めてください

# firebase initでエラーが起こった場合

- Error: Failed to list Firebase projects. See firebase-debug.log for more info.
  - firebase logout
  - webデプロイの3から始めてください
