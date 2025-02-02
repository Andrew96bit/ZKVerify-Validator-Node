## 1. Встановлення
Оновіть репозиторії та встановіть необхідні пакети:

```bash
sudo apt update && sudo apt install -y docker.io docker-compose jq sed
```

## 2. Додавання користувача та групи Docker
Додайте користувача до групи Docker:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

Створіть нового користувача для запуску ноди:

```bash
sudo useradd -m -s /bin/bash zkverify
sudo passwd zkverify
sudo usermod -aG docker zkverify
```

## 3. Перехід до користувача zkverify
Перейдіть під користувача zkverify:

```bash
su - zkverify
cd ~
```

## 4. Клонування репозиторію
Клонування репозиторію для ноди:

```bash
git clone https://github.com/zkverify/compose-zkverify-simplified.git
cd compose-zkverify-simplified
```

## 5. Запуск ініціалізаційного скрипту
Запустіть ініціалізаційний скрипт:

```bash
./scripts/init.sh
```

Під час налаштування виберіть наступні опції:

- 2 validator-node
- 1 testnet
- 1 yes (після цього створіть ім'я вашого валідатора)
- 2 no
- 2 no

## 6. Запуск ноди
Запустіть ноду:

```bash
./scripts/start.sh
```

Виберіть наступні опції запуску:

- 2 validator-node
- 1 testnet

Запустіть Docker Compose для тестової мережі:

```bash
docker compose -f /home/zkverify/compose-zkverify-simplified/deployments/validator-node/testnet/docker-compose.yml up -d
```

## 7. Перевірка логів
Щоб переглянути логи вашої ноди:

```bash
docker logs -f validator-node
```

## 8. Резервне копіювання гаманця
Збережіть секрети для резервного копіювання:

```bash
cat /home/zkverify/compose-zkverify-simplified/deployments/validator-node/testnet/configs/node/secrets/secret_phrase.dat
cat /home/zkverify/compose-zkverify-simplified/deployments/validator-node/testnet/configs/node/secrets/secret.json
```

## 9. Імпорт гаманця до Polkadot
Імпортуйте гаманець до Polkadot через офіційний сайт.

## 10. Отримання Faucet
Відвідайте [zkverify Faucet](https://zkverify-faucet.zkverify.io/) для отримання тестових монет.

## 11. Очікування синхронізації ноди
Чекайте, поки ваша нода синхронізується з мережею. Після цього ви зможете зареєструвати валідатор.

## 12. Перевірка валідатора
Перевірте ваш валідатор на [Testnet Telemetry](https://testnet-telemetry.zkverify.io/).
