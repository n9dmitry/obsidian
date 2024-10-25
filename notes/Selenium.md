```

import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Ваш логин и пароль
login = "lebedevworking"
password = "2574533Dk"

# Настройка драйвера
driver = webdriver.Chrome()

try:
    # Открываем страницу авторизации
    driver.get(
        'https://passport.yandex.ru/auth?mode=add-user&retpath=https%3A%2F%2Fmusic.yandex.ru%2Fsettings%3Ffrom-passport&origin=music_menu-add-user')

    # Вводим логин
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.NAME, 'login'))
    ).send_keys(login)

    # Нажимаем кнопку "Войти"
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.XPATH, '//*[@id="passp:sign-in"]'))
    ).click()

    # Вводим пароль
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.NAME, 'passwd'))
    ).send_keys(password)

    # Нажимаем кнопку "Продолжить"
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.XPATH, "//button[@id='passp:submit']"))
    ).click()

    # Ожидание перехода на страницу после авторизации
    WebDriverWait(driver, 10).until(
        EC.url_contains("https://music.yandex.ru")
    )

    # Получаем текущий URL, который содержит токен
    current_url = driver.current_url
    print("Текущий URL:", current_url)

    # Извлечение токена из URL
    if "access_token=" in current_url:
        token = current_url.split("access_token=")[1].split("&")[0]
        print("Токен Yandex Music:", token)
    else:
        print("Токен не найден в URL.")

except Exception as e:
    print("Ошибка:", e)
finally:
    driver.quit()  # Закрываем браузер

```




[[Python]]