#MOSQUITTO WITH POSTGRESQL AUTH

In the database we need 2 table 1 for the user/password and other for the acl 
(Accesss control).


create table test_user(
id bigserial primary key,
username character varying (100) not null,
password_hash character varying (200) not null,
is_admin boolean not null);

create table test_acl(
id bigserial primary key,
test_user_id bigint not null references test_user on delete cascade,
topic character varying (200) not null,
rw int not null);