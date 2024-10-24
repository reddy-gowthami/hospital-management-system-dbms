#List of Tables
PATIENT:
![image](https://github.com/user-attachments/assets/88ef0bae-cf84-4d4f-b7f5-d986fe241b19)
create table Patient(
p_id int primary key, name varchar (20) not null, age int not null, gender varchar(20) not null, address varchar (200) not null, phone _no int not null, disease varchar (20) not null, doctor_id int not null);
insert into patient values
(1, "Ram", 20, "Male", "Trirupati-Balajicolony", "6304647948", "fever", 11), (2, "Jai",30, "Male", "Guntur-Bcolony", "9146567889", "heart disease", 12), (3, "Balaji",35, "Male", "Vijayawada-krishnalanka", "9191919119", "lung cancer", 13), (4, "Sree",25, "Female", "Podhili-policecolony", "5456778898", "pmeumonia", 14), (5, "Anjani",15, "Female", "Ongole-scolony", "5467788990", "fever", 15);

DOCTOR:
![image](https://github.com/user-attachments/assets/3199085f-04bc-4065-834a-7d1195997c29)
create table doctor(
doctor_id int primary key, doctor_name varchar (30) not null, dept varchar(30) not null) ;
insert into doctor values
(11, "RAJA"', "MEDICINE"), (12, "RAM", "SURGERY"), (13, "SITA", "GYNACOLOGY"), (14, "МАНА", "NEUROLOGY"), (15, "GOWTHAMI" , "OTOLARYNGOLOGIST");

LABREPORT:
![image](https://github.com/user-attachments/assets/59cb65a5-a990-4595-9df8-47a82c1171e3)

create table labreport (
lab_no int primary key, P_id int not null, doctor_id int not null, Reportdate DATE not null, Category varchar (200) not null, Amount int not null, foreign key (doctor_id)references doctor (doctor_id));
insert into labreport values
(101,1,11, "2023-03-13", "Diabetes", 678), (102,2,12, "2022-02-10", "HIV", 9867), (103,3,13, "2021-01-01", "ВР", 9800), （104,4,14，“2024-02-25”，”Thyroid"，300），
（105,5,15，"2024-02-20"， "Hemoglobin"，500）；

INPATIENT:
![image](https://github.com/user-attachments/assets/daa3d87f-28b4-442d-9ef4-b5226083b907)

create table Inpatient(
p_id int primary key, room no varchar(20) not null, date_of_adm date not null, date_of_dis date not null, advance int not null, lab_no int not null, foreign key (lab_no)references labreport (lab_no));
insert into Inpatient values
(1, "201A", "2023-03-14","2023-03-16,4000,101），
(2, "202", "2022-02-11", "2022-04-12", 50000, 102), (3, "203А", "2021-01-02", "2021-02-12", 20000,103), (4, "204A","2024-02-25", "2024-04-12", 20000, 104), (5, "205A", "2024-02-20", "2024-02-25", 4000, 105) ;

OUTPATIENT:
![image](https://github.com/user-attachments/assets/d3be26e8-4526-4345-a5e1-daf4fa0395b2)

create table Outpatient(
p_id int primary key, date_of_dis date not null, lab_no int not null, foreign key (lab_no)references labreport (lab_no)) ;
insert into Outpatient values
(1, "2023-03-16", 101), (2, "2022-04-12", 102), (3,"2021-02-12", 103), (4, "2024-04-12", 104), (5, "2024-02-25", 105);

ROOM:
![image](https://github.com/user-attachments/assets/5c06d554-ce63-4d93-bf12-1419ddc96840)

create table Room(
room_no int primary key, room_type varchar(20) not null, room_status varchar(20) not null);
insert into Room values
("201A", "AC", "available"), ("202A", "NON-AC", "not available"), (" 203А", "AC", "available"), ("204A", "NON-AC", "not available"), ("205A","AC", "not available")

BILL:
![image](https://github.com/user-attachments/assets/7789def1-1e1f-4ad2-9404-e82ddc0e4ad7)

create table Bill(
bill_no int primary key, p_id int not null, doctor_charge int not null, medicine_charge int not null, room_charge int not null, lab_charge int not null, oprtn_charge int not null, no_of_days int not null, advance int not null, healthcard varchar (50) not null, bill varchar(20) not null);
insert into Bill values
(1001,1,300,500,2000,678,10,2,4000, "YES", 5000), (1002,2,1000,2000, 25000,9867,40000,60, 50000, "NO", 100000), (1003,3,1000,2000,15000,9800,40000, 30, 20000, "YES", 98000), (1004,4,500, 1000,20000, 300, 20000, 60,20000, "NO",78000), (1005,5,300,500, 3000,500,10,5,4000, "YES",7000);
