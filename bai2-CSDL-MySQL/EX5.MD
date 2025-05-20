```sql
create database QuanLyBanHang;
use QuanLyBanHang;

create table Customer (
  cID varchar(20) primary key,
  cName varchar(50) not null,
  cAge int check (cAge >= 1)
);

create table Orders (
  oID varchar(20) primary key,
  cID varchar(20) not null,
  oDate datetime,
  oTotalPrice float not null,
  foreign key (cID) references Customer(cID) on delete cascade
);

create table Product (
  pID varchar(20) primary key,
  pName varchar(50) not null,
  pPrice float not null
);

create table OrderDetail (
  oID varchar(20) not null,
  pID varchar(20) not null,
  odQTY int not null,
  primary key (oID, pID),
  foreign key (oID) references Orders(oID) on delete cascade,
  foreign key (pID) references Product(pID) on delete cascade
);