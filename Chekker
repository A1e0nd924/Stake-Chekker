from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
import time

# 🔧 Настройки
URL = "https://stake.krd"

# Заменить на свои куки (имя и значение из браузера)
cookies = [
    {"name": "session", "value": "96e3731aa0476ae598003b6b4698d9a56f362d4c8e014264e9da54bf0de3fe4f6a30d59bfdd225073cf83b56b0fbcfeb", "domain": "stake.krd"},
{name": "__cf_bm", "value": "bKUg_6mUhBDUYfjI23MsRLTMI3Mxbn1aikmEs4idXY4-1748064347-1.0.1.1-DHHeSEloQg0Bc88rj.FdckwYVafLEryBH2aq2M0lrTr5PEtENimqatqVBA1br4DNMHIHi5rk4NHHStig1g.ZRea99Jcp5M0R_xqnLyJsrW4", "domain": "stake.krd"},
{name": "cf_clearance", "value": "TZaoqKnP61AtZSXhxpCilIfpT_TNhUSNr.BmyXO3xv4-1747947936-1.2.1.1-OuPzixhWRMeaQC5onWOsgPJM2AxZQHw94sY0aM4z5sDJm9IJj75uZEWXjoyQnasPZdHZ8WKYW37cyA7oFN_YVyB32jHNX1CcRv4ATmd8D7qOknIx20rdJHWeFnG5D7kWboqcMWZEmHJl3JsBZMck4FrbLOZ_mL2l6ij7zN0htLejq7izjyrTef9kaZkRMgH2vckWCBOX4lZTn_QkqvB2WGN6PPDkZtGeniTnNElw5Z92JEVfjY4uiH3jyTNH3Oev8CQ1dIWbeObyaHAbg8vBjKfzcq5ug9zxKAuBBJLps8ifTj4r.pjJ4e5.VbwsFns3hvJdLC2jXTQJFqP9XKjLsLGbPAzUeLlbF4OIx7a_tDQ0b6o.iFXiegjZLOcUwH4B", "domain": "stake.krd"},
]

# Настройка браузера
options = Options()
options.add_argument("--headless")  # Без окна браузера
driver = webdriver.Chrome(options=options)

# Открываем сайт
driver.get(URL)
time.sleep(3)

# Устанавливаем куки
for cookie in cookies:
    driver.add_cookie(cookie)

# Перезагружаем с авторизацией
driver.get(URL)
time.sleep(5)

# Проверка дождя
try:
    rain_element = driver.find_element(By.CLASS_NAME, "rain-info")
    print("💧 Дождь активен!")
    print("Текст:", rain_element.text)
except:
    print("❌ Дождь недоступен или скрыт")

# Проверка доступа к чату
try:
    chat_input = driver.find_element(By.CLASS_NAME, "chat-input")
    if chat_input.is_enabled():
        print("✅ Чат доступен — мут отсутствует")
    else:
        print("🚫 Чат отключен — возможно, ты в муте")
except:
    print("⚠️ Чат не найден — возможно, требуется полная авторизация")

driver.quit()
