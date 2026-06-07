# ⚔ КИБЕР-ГОЙДА: ОНЛАЙН

Онлайн-версия карточной игры для 2 игроков на разных устройствах через Firebase.

---

## Как задеплоить (5 минут)

### 1. Создай Firebase проект

1. Зайди на [firebase.google.com](https://firebase.google.com) → **Get started**
2. Создай новый проект (название любое)
3. Зайди в **Project Settings** (шестерёнка) → **General** → листай вниз
4. В разделе **Your apps** нажми **</>** (Web)
5. Введи имя приложения → **Register app**
6. Скопируй объект `firebaseConfig`

### 2. Вставь конфиг в index.html

Открой `index.html`, найди строку:

```js
const FIREBASE_CONFIG = {
  apiKey:            "ВСТАВЬ_apiKey",
  ...
```

И замени все `"ВСТАВЬ_..."` на реальные значения из Firebase.

### 3. Включи Realtime Database

1. В Firebase консоли → **Build** → **Realtime Database**
2. **Create database** → выбери регион (любой ближайший)
3. Начни в **test mode** (разрешить чтение/запись всем)
4. Скопируй URL базы (вида `https://ИМЯ-default-rtdb.firebaseio.com/`)
   и вставь его в `databaseURL` в конфиге

### 4. Залей на GitHub Pages

```bash
git init
git add .
git commit -m "goyda online"
git branch -M main
git remote add origin https://github.com/ТВОЙ_НИК/goyda-online.git
git push -u origin main
```

Потом в настройках репозитория → **Pages** → Source: `main`, папка `/root` → **Save**.

Через ~2 минуты игра будет на `https://ТВОЙ_НИК.github.io/goyda-online/`

---

## Как играть онлайн

1. Один игрок нажимает **СОЗДАТЬ КОМНАТУ** — получает 6-буквенный код
2. Скидывает код другу
3. Второй вводит код и нажимает **ВОЙТИ**
4. Игра начинается автоматически

---

## Правила Database (Firebase)

В тестовом режиме правила уже разрешают всё. Для продакшна можно ограничить:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```
