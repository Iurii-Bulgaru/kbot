# kbo
Ось описаний процес для створення, запуску та перевірки бота в Telegram з використанням мови програмування Go та бібліотеки gopkg.in/telebot.v3, а також створення файлу README та завантаження коду на GitHub:

Крок 1: Написання функції-обробника повідомлень

// Handle incoming messages
func handleMessage(bot *telebot.Bot) {
    // Set up a handler for incoming text messages
    bot.Handle(telebot.OnText, func(m telebot.Context) error {
        // Extract the text of the incoming message
        text := m.Text()

        // Process the incoming message
        switch text {
        case "/start":
            // Respond to the /start command
            err := bot.Send(m.Sender(), "Hello! I'm your bot.")
            if err != nil {
                return err
            }
        default:
            // Respond to other text messages
            err := bot.Send(m.Sender(), "I received your message: "+text)
            if err != nil {
                return err
            }
        }

        // Return nil to indicate that the message was handled successfully
        return nil
    })
}
-----------------------------------------------------------------------------
Крок 2: Запуск та перевірка бота

func main() {
    // Ініціалізуємо та запускаємо бота
    bot, err := telebot.NewBot(telebot.Settings{
        Token:  "YOUR_TELEGRAM_BOT_TOKEN_HERE",
    })
    if err != nil {
        log.Fatal(err)
    }

    // Викликаємо функцію обробника повідомлень
    handleMessage(bot)

    // Починаємо отримувати повідомлення
    bot.Start()
}
----------------------------------------------------------------
Крок 3: Створення файлу README

Склонувати репозиторій:
1) git clone https://github.com/Iurii-Bulgaru/kbot
2) cd <назва_директорії>
3) Встановити необхідні залежності: go mod tidy
4) Запустити бота:  go run main.go
5) Приклади використання команд:
           Початок роботи з ботом:

Відкрийте діалог з ботом у Telegram.
Напишіть /start.
Відправка повідомлення:

Напишіть будь-яке повідомлення (текст) у діалозі з ботом.
Бот відповість вам зі своїм відповідним повідомленням.
https://t.me/IuriiBu_bot 







