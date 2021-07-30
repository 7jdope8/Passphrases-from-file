## Описание:
Простой скрипт для перебора текстового файла с паролями и поиске адресов с положительным балансом. 
Программа проверяет как сжатые, так и несжатые адреса с помощью [bit](https://github.com/ofek/bit) библиотеки. (нужен интернет)
Удобно прогонять свежие базы паролей. В базе не должно быть каракулей, квадратиков и т.п. - выдаст ошибку.


### Быстрый старт
Для использования скрипта вам понадобится Python3.x

Используемые библиотеки: [tqdm](https://github.com/tqdm/tqdm) и [bit](https://github.com/ofek/bit). Вы можете установить оба с помощью pip.

```
pip install tqdm
pip install bit
```

Проверить, работает ли скрипт, и показать справку
```
python brutecointxt.py -h
```


## Параметры запуска:

```
brutecointxt.py [-h] -t TEXT_FILE [-l] [-u] [-r] [-n]

-h, --help            show this help message and exit
  -t TEXT_FILE, --txt TEXT_FILE
                        Text file (UTF-8 encoding) with passphrases. Each line
                        containting one example. (example: passphrases.txt)
  -l, --lowercase       Additional check for lowercased version of passphrases
  -u, --uppercase       Additional check for uppercased version of passphrases
  -r, --reverse         Additional check for reversed version of passphrases
  -n, --no-uncomp       Do not check uncompressed version of addresses
```

## Пример использования:
```
python brutecointxt.py -t passphrases.txt > output.txt
```

Я рекомендую перенаправить вывод в файл, как указано выше, чтобы избежать потери полосы загрузки.
Пустой файл просто означает, что адреса с доступным балансом не найдены.

Если вы хотите дополнительно проверить строчные, прописные и обратные версии парольных фраз (это будет медленнее)
```
python brutecointxt.py -l -u -r -t passphrases.txt > output.txt
```

Если вы хотите проверять только сжатые адреса (это будет быстрее) 
```
python brutecointxt.py -n passphrases.txt > output.txt
```

## Пример вывода для параметров по умолчанию
```

Passphrase:  bitcoin is awesome
Private key hex:  23d4a09295be678b21a5f1dceae1f634a69c1b41775f680ebf8165266471401b
Private key wif:  KxRMt7KypfEsLNSikhxTPYepDMBizHNmH5Bii3wssgesxrkHNJg6
Compressed address:  1JRW4d8vHZseMEtYbgJ7MwPG1TasHUUVNq
Uncompressed address:  14NWDXkQwcGN1Pd9fboL8npVynD5SfyJAE
Balance:  1.11

Passphrase:  Bitcoin is awesome123
Private key hex:  fba656d058d6808ddfccc19adda92ec19a4dd0ec465cedb252fb1edcd426f049
Private key wif:  L5etHr5JZE7BN9MVCJ67nn2teaFSVFjdXugDkdBiThct9KjRDfGw
Compressed address:  1Ef4TwFNkPtbdRjmyZ5P4ExcgpA5pK5T4e
Uncompressed address:  13msVisdxKsFDUjo59R77AAthynWqqKUmP
Balance:  2.22

```

## Пример вывода для опции -n (только сжатый адрес)
```

Passphrase:  bitcoin is awesome
Private key hex:  23d4a09295be678b21a5f1dceae1f634a69c1b41775f680ebf8165266471401b
Private key wif:  KxRMt7KypfEsLNSikhxTPYepDMBizHNmH5Bii3wssgesxrkHNJg6
Compressed address:  1JRW4d8vHZseMEtYbgJ7MwPG1TasHUUVNq
Balance:  0.0

Passphrase:  Bitcoin is awesome123
Private key hex:  fba656d058d6808ddfccc19adda92ec19a4dd0ec465cedb252fb1edcd426f049
Private key wif:  L5etHr5JZE7BN9MVCJ67nn2teaFSVFjdXugDkdBiThct9KjRDfGw
Compressed address:  1Ef4TwFNkPtbdRjmyZ5P4ExcgpA5pK5T4e
Balance:  0.0


```
## Donation
- BTC: bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9
