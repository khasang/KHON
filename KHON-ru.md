#Этимология
Хон -- обработка абразивным бруском.  
Khasang Object Notation (от JSON -- JavaScript Object Notation)
#Цель
Обточим JSON, уберем все лишнее, категорически уменьшим объем передаваемого текста, но оставим максимальную читабельность
#Сравнение KHON, JSON, XML
##KHON
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
##JSON
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
##XML
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
#Более подробный пример
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
