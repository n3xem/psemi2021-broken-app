# psemi2021-broken-app
## インストール方法

1. 下記のコマンドでPython 3.9.7がインストールされていることを確認する（されていない場合はインストール）
```bash
$ python -V
```

2. このリポジトリをcloneし、リポジトリのディレクトリに移動する

3. 仮想環境を作る（推奨）
```bash
$ python -m venv env
$ env/bin/acitivate # アクティベート
```

4. 使用するパッケージをインストール
```
$ pip install -r requirements.txt
```

5. psemi2021_app_a/get_random_secret_key.py を実行して、出力された文字列を控えておく。

6. psemi2021_app_a/local_settings.py を作成し、以下のコードを入力する。`# ここにget_random_secret_key.py の出力を貼り付ける` には、 get_random_secret_key.py を実行した後に出た出力を貼り付ける。
```python
import os
from pathlib import Path
BASE_DIR = Path(__file__).resolve().parent.parent
# ここにget_random_secret_key.py の出力を貼り付ける
DEBUG = True


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

7.  `$ python manage.py migrate` を実行する

8.  `$ python manage.py createsuperuser` を実行し、ユーザ名とパスワードを設定する（管理者ユーザとして、adminダッシュボードにログインするときに用いる。）
