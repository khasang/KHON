#KHON -- Обезжиренная альтернатива JSON
**В среднем на 50% короче, чем JSON.**  

При этом читабельность значительно выше.  
#Этимология
Khasang Object Notation (от JSON -- JavaScript Object Notation)  
Хон -- обработка абразивным бруском.  
#Цель
Обточим JSON, уберем все лишнее, категорически уменьшим объем передаваемого текста, но оставим максимальную читабельность
#Сравнение KHON, JSON, XML
##Первый пример
###KHON
*Символов с пробелами: 181*
```
person
  firstName Иван
  lastName Иванов
  address
    streetAddress Московское ш., 101, кв.101
    city Ленинград
    postalCode 101101
  phoneNumbers
    "812 123-1234"
    "916 123-4567"
```
###JSON
*Символов с пробелами: 243*
```
{
   "firstName": "Иван",
   "lastName": "Иванов",
   "address": {
       "streetAddress": "Московское ш., 101, кв.101",
       "city": "Ленинград",
       "postalCode": 101101
   },
   "phoneNumbers": [
       "812 123-1234",
       "916 123-4567"
   ]
}
```
###XML
*Символов с пробелами: 339*
```
<person>
  <firstName>Иван</firstName>
  <lastName>Иванов</lastName>
  <address>
    <streetAddress>Московское ш., 101, кв.101</streetAddress>
    <city>Ленинград</city>
    <postalCode>101101</postalCode>
  </address>
  <phoneNumbers>
    <phoneNumber>812 123-1234</phoneNumber>
    <phoneNumber>916 123-4567</phoneNumber>
  </phoneNumbers>
</person>
```
##Второй пример
Вот исходная конфигурация представленная в виде таблицы (from wiki):

| событие IRC       | команда                | регулярное выражение |
| ------------- |:------------------:| -----:|
| PRIVMSG    | newUri    |  	"^http://.*" |
| PRIVMSG     | deleteUri |   "^delete.*" |
| PRIVMSG  | randomUri         |    "^random.*" |

###KHON
*Символов с пробелами: 137*
```
bindings
  ircEvent
  method
  regexp
  
  PRIVMSG
  newUri
  '^http://.*'
  
  PRIVMSG
  deleteUri
  '^delete.*'
  
  PRIVMSG
  randomUri
  '^random.*'
```
###YAML
*Символов с пробелами: 202*
```
bindings:
  - ircEvent: PRIVMSG
    method: newUri
    regexp: '^http://.*'
  - ircEvent: PRIVMSG
    method: deleteUri
    regexp: '^delete.*'
  - ircEvent: PRIVMSG
    method: randomUri
    regexp: '^random.*'
```
###XML
*Символов с пробелами: 406*
```
<bindings>
    <binding>
        <ircEvent>PRIVMSG</ircEvent>
        <method>newUri</method>
        <regex>^http://.*</regex>
    </binding>
    <binding>
        <ircEvent>PRIVMSG</ircEvent>
        <method>deleteUri</method>
        <regex>^delete.*</regex>
    </binding>
    <binding>
        <ircEvent>PRIVMSG</ircEvent>
        <method>randomUri</method>
        <regex>^random.*</regex>
    </binding>
</bindings>
```
или  
*Символов с пробелами: 232*
```
<bindings>
    <binding ircEvent="PRIVMSG" method="newUri" regex="^http://.*" />
    <binding ircEvent="PRIVMSG" method="deleteUri" regex="^delete.*" />
    <binding ircEvent="PRIVMSG" method="randomUri" regex="^random.*" />
</bindings>
```
##Третий пример с корзиной магазина
###KHON
*Символов с пробелами: 215*
```
backet
  orderID 12345
  shopperName John Smith
  shopperEmail johnsmith@example.com
  contents
    productID 
    productName 
    quantity
    
    34
    SuperWidget
    1
    
    56
    WonderWidget
    3
  orderCompleted true
```
###JSON
*Символов с пробелами: 307 (на 43% больше, чем KHON!)*
```
{
  "orderID": 12345,
  "shopperName": "John Smith",
  "shopperEmail": "johnsmith@example.com",
  "contents": [
    {
      "productID": 34,
      "productName": "SuperWidget",
      "quantity": 1
    },
    {
      "productID": 56,
      "productName": "WonderWidget",
      "quantity": 3
    }
  ],
  "orderCompleted": true
}
```
##Четвертый пример
###KHON
*Символов с пробелами: 612*
```
Person
  Name Ivan Ivanov
  Email ivan@ru.ru
  Address
    Country Russian Federation
    City Moscow
    Street Ivanovskaya, 11-22
  Phone
    Mob 915-555-5555
    Office 777-55-55
  HeLikes
    Cars
    Apple
    Travel
  WishList
    Name
    Manufacturer
    Quantity
    Notes
    
    Dodge
    General Motors
    1
    
    MacBook Pro
    Apple
    2
    15 inch
    
    Lamp
    No matters
  WorksOn
    Google
    Khasang
  CV
    Company name
    Date to
    Date from
    Position
    
    Khasang
    now
    2008-01-01
    Architect
    
    Google
    2004-11-11
    2008-01-01
    Manager
    
    Yandex
    2000-03-03
    2004-11-11
    Developer
```
###JSON
*Символов с пробелами: 1006 (на 64% больше, чем KHON!)*
```
{
  "Name": "Ivan Ivanov",
  "Email": "ivan@ru.ru",
  "Address":
  {
    "Country": "Russian Federation",
    "City": "Moscow",
    "Street": "Ivanovskaya, 11-22"
  },
    "Phone":{
    "Mob": "915-555-5555",
    "Office": "777-55-55"
  },
  "HeLikes": [
    "Cars",
    "Apple",
    "Travel"
  ],
  "WishList": [
    {
      "Name": "Dodge",
      "Manufacturer": "General Motors",
      "Quantity": 1
    },
    {
      "Name": "MacBook Pro""
      "Manufacturer": "Apple"
      "Quantity": 2
      "Notes": "15 inch"
    },
    {
      "Name": "Lamp"
      "Manufacturer": "No matters"
    }
  ],
  "WorksOn": [
    "Google",
    "Khasang"
  ],
  "CV": [
    {
      "Company name": "Khasang",
      "Date to": "now",
      "Date from": "2008-01-01",
      "Position": "Architect"
    },
    {
      "Company name": "Google"
      "Date to": "2004-11-11"
      "Date from": "2008-01-01"
      "Position": "Manager"
    },
    {
      "Company name": "Yandex"
      "Date to": "2000-03-03"
      "Date from": "2004-11-11"
      "Position": "Developer"
    }
  ]
}
```
#Синтаксические элементы KHON
##Последовательности
###Название последовательности из одного слова, все элементы списка из одного слова
```
Films
  Casablanca
  Spellbound
  Notorious
ShoppingList
  milk
  bread
  cocoa
  juice
```
###Название последовательности из нескольких слов, все элементы списка из одного слова
```
"Список фильмов"
  Casablanca
  Spellbound
  Notorious
"Список покупок"
  milk
  bread
  cocoa
  juice
```
###Название последовательности из одного слова, некоторые элементы списка из нескольких слов
```
Films
  "Black Casablanca"
  Spellbound
  Notorious
ShoppingList
  "milk 3.2%"
  "white bread"
  cocoa
  juice
```
##Сопоставления имени и значения (Отображение, карта)
###Ключ из одного слова, значение из одного слова
```
person
  name John
  age 33
```
###Ключ из одного слова, значение многословное
```
person
  name John Smith
  age 33
```
###Ключ из нескольких слов, значение многословное
```
person
  "first name" John Smith
  age 33
```
##Блочные литералы (строка с переносами)
```
note
  """
  Quick brown fox
  jumb over the lazy dog
  """
```
##Список из отображений
###Все поля используются
| name       | age                |
| ------------- |:------------------:|
| John Smith    | 33    |
| Mary Smith     | 27 |
| Jerry Smith  | 11         |
| Kitty Smith  | 4         |
```
persons
  name
  age
  
  John Smith
  33
  
  Mary Smith
  27
  
  Jerry Smith
  11
  
  Kitty Smith
  4
```
###Поля опциональны справа налево
Как при передаче аргументов в функцию

| name       | age                |notes                |
| ------------- |:------------------:|------------------:|
| John Smith    | 33    |like snowboard |
| Mary Smith     | 27 |teacher |
| Jerry Smith  | 11         |   |
| Kitty Smith  | 4         |too small |

```
persons
  name
  age
  notes
  
  John Smith
  33
  like snowboard
  
  Mary Smith
  27
  teacher
  
  Jerry Smith
  11
  
  Kitty Smith
  4
  too small
```
##Коллекция из объектов
```
persons
  firstName
  lastName
  address
    streetAddress
    city
    postalCode 
  phoneNumbers

  Иван
  Иванов
    Московское ш., 101, кв.101
    Ленинград
    101101
    
    
    "812 123-1234"
    "916 123-4567"
    
  Петр
  Петров
    Горьковское ш., 97, кв.22
    Москва
    442123
    
    
    "812 344-5333"

  Катя
  Катечкина
    Химкинское ш., 5, кв.333


    "812 123-1234"
    "916 123-4567"  
    "916 123-4567"      
```
##Коллекция из объектов, содержащих коллекцию других объектов
Коллекция персон, где у каждой персоны может быть несколько книг. И каждая книга имеет свои характеристики.  
Вложенная коллекция (если она состоит из нескольких элементов) отделяется пустой строчкой вначале и еще одной пустой строчкой в конце. Каждый сложный элемент коллекции отделяется от другого пустой строчкой.
```
persons
  firstName
  lastName
  address
    streetAddress
    city
    postalCode 
  favoriteBooks
    ISBN
    name
    pages
  phoneNumbers

  Иван
  Иванов
    Московское ш., 101, кв.101
    Ленинград
    101101
    
    
    2-266-11156-6
    Super Java in 1 minute
    10
      
    2-266-11156-7
    Android in 50 years
    40000
      
    2-266-11156-8
    Github at a glance
    102
    
    
    "812 123-1234"
    "916 123-4567"
    
  Петр
  Петров
    Горьковское ш., 97, кв.22
    Москва
    442123
    
    
    2-266-11156-6
    Super Java in 1 minute
    10
      
    2-266-11156-7
    Android in 50 years
    40000
      
    2-266-11156-8
    Github at a glance
    102
    
    
    "812 344-5333"

  Катя
  Катечкина
    Химкинское ш., 5, кв.333
    
    
    2-266-11156-6
    Super Java in 1 minute
    10
      
      
    "812 123-1234"
    "916 123-4567"  
    "916 123-4567"      
```
##Коллекция из объектов, содержащих коллекцию других объектов
Персоны характеризуются именем, фамилией, коллекцией любимых цветов (одна характеристика: цвет), коллекцией адресов (четыре характеристики: улица, город, код, тип), коллекцией книг (три характеристики: isbn, имя, количество страниц), коллекцией телефонных номеров (одна характеристика: номер).  
В этом случае сложные коллекции имеют отступ друг от друга в **две** пустых строки
```
persons
  firstName
  lastName
  favoriteColors
  addresses
    streetAddress
    city
    postalCode 
    kind
  favoriteBooks
    ISBN
    name
    pages
  phoneNumbers

  Иван
  Иванов
    Red
    Green
    Blue
    
    Московское ш., 101, кв.101
    Ленинград
    101101
    home
    
    Московское ш., 1, кв.1
    Ленинград
    101123
    work
    
    
    2-266-11156-6
    Super Java in 1 minute
    10
      
    2-266-11156-7
    Android in 50 years
    40000
      
    2-266-11156-8
    Github at a glance
    102
    
    "812 123-1234"
    "916 123-4567"
    
  Петр
  Петров
    Black
    Purple
    
    Горьковское ш., 97, кв.22
    Москва
    442123
    work
    
    Шелепихинское ш. 1
    Москва
    134124
    home
    
    
    2-266-11156-6
    Super Java in 1 minute
    10
      
    2-266-11156-7
    Android in 50 years
    40000
      
    2-266-11156-8
    Github at a glance
    102
    
    "812 344-5333"

  Катя
  Катечкина
    Pink

    Химкинское ш., 5, кв.333
    Москва
    
    
    2-266-11156-6
    Super Java in 1 minute
    10
      
    "812 123-1234"
    "916 123-4567"  
    "916 123-4567"      
```
