# Android_test
Тестовое задание для Android разработчиков

Условие: реализовать тестовое одноэкранное мобильное приложение.

Требования к технологиям:
- java
- архитектура MVP, можно использовать Moxy для паттерента
- Для хранения моделей использовать db Realm

Требования к внешнему виду:
- Соблюсти структуру таблицы (отступы и цвет не важен)
- В шапке должен быть аватар и название клуба
- Полоса с текстовыми названиями ТТД не важна, необходимо вывести
значения параметров в таблицу в том порядке в
котором они приходят с сервера
- В таблице слева список матчей. Информация в ячейке:
название клуба соперника, счет, дата.
- В таблице справаколичественные значения ТТД
*плашка в среднем не нужна

Общие требования:
- Любой клуб из базы Инстат (уточнить ID клуба у HR
менеджера)
- Количество матчей в рассматриваемом периоде минимум 30
(дату подобрать самому)
- Таблица с количественными показателями ТТД должна скролиться
вправо(влево) для отображения полного списка
- Значения в таблице с количественными показателями ТТД
после первого входа в приложение должны сохраняться

Критерии оценивания:
- Чистый и читаемый код
- Соблюдены принципы ООП
- Для разработки таблицы использовать RecycleView или другую технологию, что бы не
жрало память если в таблице будет 500 и более линий
- Соблюдены требования к технологиям (!)
- Приложение соответствует “общим требованиям”

Описание методов для получения данных:
Для получения данных о запросе нужно провести следующую
процедуру:
Отправить POST запрос на url
https://service.instatfootball.com/ws.php c телом запроса:
{
"server": "instatfootball.com",
"base": "basketball",
"login": "mobile_app",
"pass": "***",
"proc": "scout_match_players_stat", // название процедуры
"disable_json_escaping":1,
"params": {
"_p_match_id":"395225"
}

1. Метод получения данных о клубе
{
"server": "instatfootball.com",
"base":"pg_football",
"login": "mobile_app",
"pass": "QyMhQz5Xbhh77Lcn",
"proc":"scout_team_inf",
"disable_json_escaping": 1,
"params": {
"_p_team_id":"151"
}

}
2. Метод получения данных о матчах клуба за
определенный период
{
"server": "instatfootball.com",
"base":"pg_football",
"login": "mobile_app",
"pass": "QyMhQz5Xbhh77Lcn",
"proc":"scout_team_match_period_1",
"disable_json_escaping": 1,
"params": {
"_p_team_id":28706,
"_p_date_from": "2017-01-01",
"_p_date_to": "2017-11-29",
"_p_limit": 5,
"_p_offset": 0
}
}

3. Метод получения данных о ТТД клуба в матчах
за определенный период

Здесь запрашиваем ТТД к матчам запрошенным во 2 методе
{
"server": "instatfootball.com",
"base":"pg_football",
"login": "mobile_app",
"pass": "QyMhQz5Xbhh77Lcn",
"proc":"scout_team_matches_stat",
"disable_json_escaping": 1,
"params": {
"_p_team_id":3,
"_p_match_arr": "{1298222,1179212,1309067,1179203,1179195}"
}}


Результат на github.com/bitbucket.com (открытый репозиторий) и ссылку на почту.
