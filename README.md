# go_backend_project
# Тестовое задание на позицию Junior Backend Developer

### **Используемые инструменты**

Для выполнения этого задания необходимо использовать следующие технологии:

- Go,
- PostgreSQL,
- Docker
  
# Дополнительные технологии
- Используем GORM библиотеку
- Используем Gin Framework
- bcrypt пакет
- jwt-go библиотека
- godotenv для переменных окружения для файла .env
  
# .env файл
Файл с переменными окружения
 - PORT = 3000
# Описание функций   
Функция func LoadEnvVariables(), загружает переменные из файла .env Помещаем эту функцию в функцию func init(), она вызывается перед функцией main
Затем создаем gin приложение с помощью функции gin.Default()

# Подключение к базе данных
Подключаемся к функции func ConnectToDb(). Тут пока ошибка, так как не удается подключиться к базе данных.

# Создаем модель приложения

Для модели  используем структуру, с полями email и пароль(password):
type User struct
{
	gorm.Model
	Email string `gorm:"unique"`
	Password string
}
Подсоединяем модель к базе данных через функцию func SyncDatabase(), так же помещаем её в функцию init().

# Функция регистрации func Signup(c *gin.Context)
В функции мы получем пару email/пароль(password). После этого мы хэшируем пароль, затем создаем пользователя(user) и после этого ответ.
В структуре body мы сохраним email/password который мы получим -> var body struct.
Хешируем пароль с помощью функции bctypt, передаем пароль(password) hash, err := bcrypt.GenerateFromPassword([]byte(body.Password), 10)
И в конце создаем пользователя на основе полученной пары(email/password) с помощью функции
user := User{Email:body.Email, Password:string(hash)}

В фнукции main посылаем запрос POST
r.POST("/singup", Signup)
# Результат работы

Результат должен быть представлен в виде исходного кода на GitHub. 
