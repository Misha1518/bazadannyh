create database Диспечерская аэропорта 
go 
use Аэропорт 
go 
create table Сотрудники 
( 
Код_сотрудника int not null identity(1, 1) primary key, 
ФИО varchar(255), 
Заработная_плата decimal not null , 
Должность varchar(255), 
Состояние varchar(255), 
); 
go 
create table Полоса 
( 
Код_полосы int not null identity(1, 1) primary key, 
Состояние varchar(255), 
Уровень varchar(255), 
Налёт int not null, 
); 
go 
create table Экипаж 
( 
Код_члена_экипажа int not null identity(1, 1) primary key, 
ФИО varchar(255), 
Заработная_плата decimal not null , 
Ранг varchar(255), 
Возраст int not null, 
Часов_налёта int not null, 
); 
create table Здание 
( 
Код_здания int not null identity(1, 1) primary key, 
Тип varchar(255) not null, 
); 

go 
create table Самолёт 
( 
Код_самолёта int not null identity(1, 1) primary key, 
Экипаж(Код_члена_экипажа) primary key, 
Номер(Номер_рейса) primary key, 
Тип varchar(255), 
Модель varchar(255), 
Класс_по_взлётной_массе int not null, 
Часов_налёта int not null, 
); 
go 
create table Метеослужба 
( 
ID_здания(Код_здания) primary key , 
Режим varchar(255), 
Уровень varchar(255), 
Сотрудники(Код_сотрудника) primary key, 
); 
go 
create table Окружающая_среда 
( 
Животные_на_территории varchar(255), 
Растительность_на_территории varchar(255), 
Водные объекты varchar(255), 

); 
go 
create table Погодные_условия 
( 
Количество_осадков int not null, 
Осадки_тип varchar(255), 
Скорость_ветра int not null, 
Направление_ветра varchar(255), 
Температура int not null, 

); 
go 
create table Чрезвычайна_ситуация 
( 
Дата int not null, 
Жертвы varchar(255), 
Уровень varchar(255), 
Самолёт(Код_самолёта) primary key, 
Полоса(Код_полосы) primary key, 

); 
go 
create table Комплекс 
( 
ID_здания(Код_здания) primary key , 
Режим varchar(255), 
Уровень varchar(255), 

); 
go 
create table Грузовой_комплекс 
( 
ID_здания(Код_здания) primary key , 
Состояние varchar(255), 
Заполненость_склада int not null, 

); 
go 
create table Пассажирский_комплекс 
( 
ID_здания(Код_здания) primary key , 
Состояние varchar(255), 
Класс varchar(255), 

); 
go 
create table Службы 
( 
Служба int not null identity(1, 1) primary key, 
Название varchar(255), 
Экипировка varchar(255), 
Связь varchar(255), 
Транспорт varchar(255), 
Сотрудники(Код_сотрудника) primary key, 

); 
go 
create table Служба_быстрого_реагирования 
( 
Инфо(Служба) primary key 
varchar(255), 
int not null, 

); 
go 
create table Регулярная_служба 
( 
ID_здания(Код_здания) primary key 
varchar(255), 

Сотрудники(Код_сотрудника) primary key, 
); 
go 
create table Ремонтная_служба 
( 
ID_здания(Код_здания) primary key 
Оценка varchar(255), 
Самолёт(Код_самолёта) primary key, 
Сотрудники(Код_сотрудника) primary key, 
); 
go 
create table Ангар 
( 
ID_здания(Код_здания) primary key , 
Материалы(Материалы) primary key , 
Сотрудники(Код_сотрудника) primary key, 
Срок date not null, 
Тип varchar(255), 
); 
go 
create table Материалы 
( 
Материалы int not null identity(1, 1) primary key, 
Тип varchar(255), 
Количество int not null, 
); 
go 
create table Контроль_занятости_неба 
( 
Номер(Номер_рейса) primary key, 
Сотрудники(Код_сотрудника) primary key, 
Высота int not null, 
Связь varchar(255), 
Сопровождение varchar(255), 
); 
go 
create table Рейс 
( 
Номер_рейса int not null identity(1, 1) primary key, 
Место_назначения varchar(255), 
Место_отправления varchar(255), 
Координаты int not null, 
Состояние int not null, 
); 
go 
create table Служба_контроля_полётов 
( 
Номер(Номер_рейса) primary key, 
Сотрудники(Код_сотрудника) primary key, 
Занятость_неба varchar(255), 
Количество_на_кругу int not null, 

); 
go 
create table Авиакомпания 
( 
Номер(Номер_рейса) primary key, 
Сотрудники(Код_сотрудника) primary key, 
Название varchar(255), 
Цвета varchar(255), 
Аэропорт_прописки varchar(255), 
);
