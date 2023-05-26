# Встановлення та налаштування додатку в ArgoCD

## Передумови

Для початку необхідно розгорнути кластер та авторизуватися в ArgoCD Dashboard відповідно до [цієї процедури](./POC.md).

## Встановлення додатку

### Додавання додатку

1. Натиснути __Applications__
2. Натиснути __+ NEW APP__
3. Заповнити відповдні поля та натиснути __CREATE__

![Image](../res/mvp-new-app-demo.gif)

### Синхронізація додатку

Для синхронізації додатку необхідно натиснути SYNC. Після цього ArgoCD буде відстежувати зміни в стані додатку та синхронізувати із бажаним станом. Також будь-які зміни в віддаленому репозиторії будуть відстежені та враховані в деплойменті.

![Image](../res/mvp-sync-app-demo.gif)

## Перевірка роботи додатку

1. Додати локальний port forwarding

```bash
kubectl port-forward -n mvp svc/ambassador 8088:80
```

![Image](../res/mvp-svc-port-forward-demo.gif)

2. Відкрити нове вікно терміналу та перевірити роботу додатку

```bash
wget -O ./temp-img.png https://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Microsoft_Azure.svg/800px-Microsoft_Azure.svg.png && \
curl -F 'image=@./temp-img.png' localhost:8088/img/
```

![Image](../res/mvp-svc-test-demo.gif)

# Післяслово

Тепер система ArgoCD буде відстежувати зміни в додатку та застосовувати відповідні зміни для того, аби додаток відповідав бажаному стану.