# central-examination-system
#E R Model of central examination system implemented using MySQL 
CREATE TABLE company (
    company_name VARCHAR(100) PRIMARY KEY,
    owner VARCHAR(100),
    no_of_exams INT,
    name_of_exams VARCHAR(255),
    headquarters VARCHAR(100),
    contact VARCHAR(100),
    no_of_employees INT
);

CREATE TABLE centre (
    centre_id INT PRIMARY KEY,
    cname VARCHAR(100),
    city VARCHAR(100),
    state VARCHAR(100),
    pincode VARCHAR(10),
    type VARCHAR(50),
    landmark VARCHAR(100),
    building_no VARCHAR(20),
    floor_no INT,
    rent_per_day DECIMAL(10,2)
);

CREATE TABLE computer (
    computer_id INT PRIMARY KEY,
    centre_id INT,
    manufacturer VARCHAR(100),
    internet BOOLEAN,
    FOREIGN KEY (centre_id) REFERENCES centre(centre_id)
);

CREATE TABLE staff (
    staff_id INT PRIMARY KEY,
    centre_id INT,
    sname VARCHAR(100),
    type VARCHAR(50),
    gender VARCHAR(10),
    FOREIGN KEY (centre_id) REFERENCES centre(centre_id)
);

CREATE TABLE exam (
    exam_id INT PRIMARY KEY,
    subject VARCHAR(100),
    topic VARCHAR(100),
    fee DECIMAL(10,2),
    centre_id INT,
    FOREIGN KEY (centre_id) REFERENCES centre(centre_id)
);

CREATE TABLE login (
    login_id INT PRIMARY KEY,
    password VARCHAR(100)
);

CREATE TABLE student (
    id INT PRIMARY KEY,
    centre_id INT,
    login_id INT,
    name VARCHAR(100),
    dob DATE,
    gender VARCHAR(10),
    city VARCHAR(100),
    colony VARCHAR(100),
    landmark VARCHAR(100),
    house_no VARCHAR(20),
    exam_id INT,
    subject VARCHAR(100),
    topic VARCHAR(100),
    state VARCHAR(100),
    pincode VARCHAR(10),
    age INT,
    FOREIGN KEY (centre_id) REFERENCES centre(centre_id),
    FOREIGN KEY (login_id) REFERENCES login(login_id),
    FOREIGN KEY (exam_id) REFERENCES exam(exam_id)
);

CREATE TABLE result (
    id INT PRIMARY KEY,
    staff_id INT,
    exam_id INT,
    score DECIMAL(5,2),
    FOREIGN KEY (staff_id) REFERENCES staff(staff_id),
    FOREIGN KEY (exam_id) REFERENCES exam(exam_id)
);

CREATE TABLE registration_form (
    registration_no INT PRIMARY KEY,
    centre_id INT,
    cname VARCHAR(100),
    state VARCHAR(50),
    city VARCHAR(100),
    pincode VARCHAR(10),
    colony VARCHAR(100),
    landmark VARCHAR(100),
    age INT,
    name VARCHAR(100),
    gender VARCHAR(10),
    dob DATE,
    topic VARCHAR(100),
    subject VARCHAR(100),
    type VARCHAR(50),
    FOREIGN KEY (centre_id) REFERENCES centre(centre_id)
);
INSERT INTO company (company_name,owner,no_of_exams,name_of_exams,headquarters,contact,no_of_employees) VALUES ('EduCorp','Jane Smith',10,'ExamsList','Main HQ','1234567890',150);
INSERT INTO centre (centre_id,cname,city,state,pincode,type,landmark,building_no,floor_no,rent_per_day) VALUES (1,'Centre1','City1','StateX','Pin1','TypeA','Landmark1','B1',1,150.0);
INSERT INTO centre (centre_id,cname,city,state,pincode,type,landmark,building_no,floor_no,rent_per_day) VALUES (2,'Centre2','City2','StateX','Pin2','TypeA','Landmark2','B2',2,300.0);
INSERT INTO centre (centre_id,cname,city,state,pincode,type,landmark,building_no,floor_no,rent_per_day) VALUES (3,'Centre3','City3','StateX','Pin3','TypeA','Landmark3','B3',3,450.0);
INSERT INTO centre (centre_id,cname,city,state,pincode,type,landmark,building_no,floor_no,rent_per_day) VALUES (4,'Centre4','City4','StateX','Pin4','TypeA','Landmark4','B4',4,600.0);
INSERT INTO centre (centre_id,cname,city,state,pincode,type,landmark,building_no,floor_no,rent_per_day) VALUES (5,'Centre5','City5','StateX','Pin5','TypeA','Landmark5','B5',5,750.0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (1,3,'CompMfg1',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (2,1,'CompMfg2',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (3,5,'CompMfg3',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (4,3,'CompMfg0',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (5,3,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (6,2,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (7,4,'CompMfg3',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (8,1,'CompMfg0',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (9,3,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (10,1,'CompMfg2',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (11,4,'CompMfg3',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (12,3,'CompMfg0',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (13,2,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (14,3,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (15,2,'CompMfg3',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (16,2,'CompMfg0',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (17,3,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (18,1,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (19,5,'CompMfg3',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (20,5,'CompMfg0',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (21,1,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (22,1,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (23,2,'CompMfg3',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (24,3,'CompMfg0',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (25,1,'CompMfg1',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (26,2,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (27,2,'CompMfg3',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (28,3,'CompMfg0',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (29,1,'CompMfg1',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (30,5,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (31,5,'CompMfg3',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (32,4,'CompMfg0',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (33,1,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (34,5,'CompMfg2',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (35,5,'CompMfg3',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (36,5,'CompMfg0',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (37,3,'CompMfg1',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (38,3,'CompMfg2',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (39,1,'CompMfg3',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (40,2,'CompMfg0',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (41,3,'CompMfg1',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (42,4,'CompMfg2',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (43,1,'CompMfg3',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (44,2,'CompMfg0',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (45,4,'CompMfg1',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (46,1,'CompMfg2',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (47,5,'CompMfg3',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (48,4,'CompMfg0',0);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (49,4,'CompMfg1',1);
INSERT INTO computer (computer_id,centre_id,manufacturer,internet) VALUES (50,5,'CompMfg2',0);
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (1,2,'Staff1','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (2,2,'Staff2','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (3,4,'Staff3','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (4,3,'Staff4','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (5,3,'Staff5','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (6,2,'Staff6','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (7,4,'Staff7','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (8,1,'Staff8','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (9,5,'Staff9','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (10,4,'Staff10','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (11,1,'Staff11','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (12,4,'Staff12','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (13,3,'Staff13','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (14,2,'Staff14','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (15,3,'Staff15','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (16,2,'Staff16','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (17,1,'Staff17','teacher','F');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (18,3,'Staff18','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (19,3,'Staff19','teacher','M');
INSERT INTO staff (staff_id,centre_id,sname,type,gender) VALUES (20,5,'Staff20','teacher','F');
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (1,'Subject1','Topic1',310,3);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (2,'Subject2','Topic2',320,2);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (3,'Subject3','Topic3',330,4);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (4,'Subject4','Topic0',340,4);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (5,'Subject0','Topic1',350,4);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (6,'Subject1','Topic2',360,2);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (7,'Subject2','Topic3',370,4);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (8,'Subject3','Topic0',380,1);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (9,'Subject4','Topic1',390,3);
INSERT INTO exam (exam_id,subject,topic,fee,centre_id) VALUES (10,'Subject0','Topic2',400,5);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (1,1,1,'Student1','2006-05-18','M','City1','Colony1','Landmark1','H1',9,'Subject1','Topic1','StateX','Pin1',18);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (2,1,2,'Student2','1999-04-16','F','City2','Colony2','Landmark2','H2',3,'Subject2','Topic2','StateX','Pin2',20);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (3,4,3,'Student3','2009-06-14','M','City3','Colony3','Landmark3','H3',5,'Subject3','Topic3','StateX','Pin3',16);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (4,5,4,'Student4','2009-12-07','F','City4','Colony0','Landmark4','H4',7,'Subject4','Topic0','StateX','Pin4',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (5,5,5,'Student5','1997-12-10','M','City0','Colony1','Landmark0','H5',3,'Subject0','Topic1','StateX','Pin0',22);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (6,2,6,'Student6','1994-08-25','F','City1','Colony2','Landmark1','H6',4,'Subject1','Topic2','StateX','Pin1',14);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (7,4,7,'Student7','2001-07-27','M','City2','Colony3','Landmark2','H7',9,'Subject2','Topic3','StateX','Pin2',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (8,3,8,'Student8','2003-01-29','M','City3','Colony0','Landmark3','H8',9,'Subject3','Topic0','StateX','Pin3',20);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (9,2,9,'Student9','1996-04-19','M','City4','Colony1','Landmark4','H9',5,'Subject4','Topic1','StateX','Pin4',21);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (10,5,10,'Student10','2001-08-28','F','City0','Colony2','Landmark0','H10',5,'Subject0','Topic2','StateX','Pin0',14);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (11,1,11,'Student11','2001-12-11','F','City1','Colony3','Landmark1','H11',1,'Subject1','Topic3','StateX','Pin1',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (12,5,12,'Student12','2002-12-11','F','City2','Colony0','Landmark2','H12',4,'Subject2','Topic0','StateX','Pin2',22);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (13,2,13,'Student13','1999-10-31','M','City3','Colony1','Landmark3','H13',4,'Subject3','Topic1','StateX','Pin3',16);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (14,3,14,'Student14','1999-05-04','F','City4','Colony2','Landmark4','H14',9,'Subject4','Topic2','StateX','Pin4',17);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (15,5,15,'Student15','2000-03-06','M','City0','Colony3','Landmark0','H15',2,'Subject0','Topic3','StateX','Pin0',22);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (16,1,16,'Student16','2007-09-01','M','City1','Colony0','Landmark1','H16',2,'Subject1','Topic0','StateX','Pin1',17);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (17,5,17,'Student17','1990-11-24','M','City2','Colony1','Landmark2','H17',9,'Subject2','Topic1','StateX','Pin2',21);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (18,5,18,'Student18','2001-09-05','M','City3','Colony2','Landmark3','H18',7,'Subject3','Topic2','StateX','Pin3',14);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (19,3,19,'Student19','2002-03-24','F','City4','Colony3','Landmark4','H19',3,'Subject4','Topic3','StateX','Pin4',15);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (20,5,20,'Student20','2006-10-02','F','City0','Colony0','Landmark0','H20',6,'Subject0','Topic0','StateX','Pin0',17);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (21,4,21,'Student21','2005-12-09','F','City1','Colony1','Landmark1','H21',10,'Subject1','Topic1','StateX','Pin1',18);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (22,5,22,'Student22','2000-07-21','F','City2','Colony2','Landmark2','H22',3,'Subject2','Topic2','StateX','Pin2',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (23,3,23,'Student23','2005-07-15','F','City3','Colony3','Landmark3','H23',6,'Subject3','Topic3','StateX','Pin3',13);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (24,1,24,'Student24','1990-05-11','M','City4','Colony0','Landmark4','H24',7,'Subject4','Topic0','StateX','Pin4',13);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (25,4,25,'Student25','1994-09-22','F','City0','Colony1','Landmark0','H25',1,'Subject0','Topic1','StateX','Pin0',20);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (26,2,26,'Student26','2001-01-04','F','City1','Colony2','Landmark1','H26',1,'Subject1','Topic2','StateX','Pin1',22);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (27,4,27,'Student27','2003-03-01','M','City2','Colony3','Landmark2','H27',2,'Subject2','Topic3','StateX','Pin2',22);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (28,3,28,'Student28','1995-10-20','F','City3','Colony0','Landmark3','H28',5,'Subject3','Topic0','StateX','Pin3',20);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (29,3,29,'Student29','1997-03-16','F','City4','Colony1','Landmark4','H29',2,'Subject4','Topic1','StateX','Pin4',16);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (30,4,30,'Student30','1990-10-26','F','City0','Colony2','Landmark0','H30',3,'Subject0','Topic2','StateX','Pin0',17);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (31,1,31,'Student31','2002-04-01','M','City1','Colony3','Landmark1','H31',6,'Subject1','Topic3','StateX','Pin1',16);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (32,3,32,'Student32','2010-05-24','M','City2','Colony0','Landmark2','H32',8,'Subject2','Topic0','StateX','Pin2',21);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (33,4,33,'Student33','2000-11-03','M','City3','Colony1','Landmark3','H33',6,'Subject3','Topic1','StateX','Pin3',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (34,5,34,'Student34','1992-07-02','F','City4','Colony2','Landmark4','H34',8,'Subject4','Topic2','StateX','Pin4',21);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (35,2,35,'Student35','1993-03-20','M','City0','Colony3','Landmark0','H35',6,'Subject0','Topic3','StateX','Pin0',13);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (36,1,36,'Student36','1997-05-21','M','City1','Colony0','Landmark1','H36',6,'Subject1','Topic0','StateX','Pin1',14);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (37,3,37,'Student37','1991-05-02','F','City2','Colony1','Landmark2','H37',5,'Subject2','Topic1','StateX','Pin2',14);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (38,4,38,'Student38','1998-10-23','F','City3','Colony2','Landmark3','H38',3,'Subject3','Topic2','StateX','Pin3',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (39,5,39,'Student39','2000-07-27','F','City4','Colony3','Landmark4','H39',7,'Subject4','Topic3','StateX','Pin4',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (40,4,40,'Student40','1999-06-08','M','City0','Colony0','Landmark0','H40',5,'Subject0','Topic0','StateX','Pin0',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (41,1,41,'Student41','2010-10-21','F','City1','Colony1','Landmark1','H41',3,'Subject1','Topic1','StateX','Pin1',19);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (42,4,42,'Student42','2008-06-05','M','City2','Colony2','Landmark2','H42',5,'Subject2','Topic2','StateX','Pin2',21);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (43,5,43,'Student43','1993-05-05','M','City3','Colony3','Landmark3','H43',7,'Subject3','Topic3','StateX','Pin3',14);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (44,5,44,'Student44','2004-12-06','M','City4','Colony0','Landmark4','H44',3,'Subject4','Topic0','StateX','Pin4',17);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (45,2,45,'Student45','1999-04-17','F','City0','Colony1','Landmark0','H45',5,'Subject0','Topic1','StateX','Pin0',15);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (46,3,46,'Student46','2006-11-06','F','City1','Colony2','Landmark1','H46',4,'Subject1','Topic2','StateX','Pin1',17);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (47,1,47,'Student47','2007-10-16','M','City2','Colony3','Landmark2','H47',7,'Subject2','Topic3','StateX','Pin2',18);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (48,5,48,'Student48','1995-07-21','F','City3','Colony0','Landmark3','H48',6,'Subject3','Topic0','StateX','Pin3',18);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (49,5,49,'Student49','1991-10-23','F','City4','Colony1','Landmark4','H49',9,'Subject4','Topic1','StateX','Pin4',15);
INSERT INTO student (id,centre_id,login_id,name,dob,gender,city,colony,landmark,house_no,exam_id,subject,topic,state,pincode,age) VALUES (50,5,50,'Student50','2000-02-26','M','City0','Colony2','Landmark0','H50',3,'Subject0','Topic2','StateX','Pin0',17);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (1,14,9,36.9103176117524);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (2,18,3,44.14831241130349);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (3,12,5,32.77688997817617);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (4,19,7,53.42393651767463);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (5,18,3,97.89728724359757);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (6,7,4,99.60231784033866);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (7,18,9,51.01378210508776);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (8,8,9,31.4931936962573);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (9,6,5,98.38917307089747);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (10,13,5,46.65770484748167);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (11,16,1,33.9429545861643);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (12,8,4,94.21737258262296);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (13,3,4,77.04836187881097);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (14,19,9,67.63323570075116);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (15,3,2,75.60461034519898);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (16,17,2,45.391370210358005);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (17,2,9,69.17027035011023);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (18,14,7,97.28651203901326);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (19,4,3,33.40229805888113);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (20,1,6,37.657172500213576);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (21,17,10,43.81446223300842);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (22,1,3,91.94439498293642);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (23,5,6,35.57543060884154);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (24,8,7,90.69891629032342);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (25,13,1,97.74887543535507);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (26,12,1,76.19442000632534);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (27,15,2,48.8153083251819);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (28,10,5,66.00319866190188);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (29,2,2,90.93086906080552);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (30,1,3,47.54236021568113);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (31,16,6,90.43080532572594);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (32,16,8,75.64357180322307);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (33,5,6,99.21485914612407);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (34,14,8,94.75151564754235);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (35,9,6,80.80981463696642);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (36,13,6,63.597059323826144);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (37,3,5,71.22618954477599);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (38,20,3,89.67177945938406);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (39,19,7,35.021426752960785);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (40,3,5,53.1293469105973);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (41,14,3,66.94809115289266);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (42,4,5,42.20020590940872);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (43,4,7,76.15598700615428);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (44,11,3,58.132112471729855);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (45,1,5,35.372383465698064);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (46,3,4,72.20951850845454);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (47,6,7,92.6616920001901);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (48,7,6,77.29242451044922);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (49,9,9,43.55440702356591);
INSERT INTO result (id,staff_id,exam_id,score) VALUES (50,4,3,47.29817215386711);
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (1,1,'CentreName1','StateX','City1','Pin1','Colony1','Landmark1',18,'Student1','M','2006-05-18','Topic1','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (2,1,'CentreName1','StateX','City2','Pin2','Colony2','Landmark2',20,'Student2','F','1999-04-16','Topic2','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (3,4,'CentreName4','StateX','City3','Pin3','Colony3','Landmark3',16,'Student3','M','2009-06-14','Topic3','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (4,5,'CentreName5','StateX','City4','Pin4','Colony0','Landmark4',19,'Student4','F','2009-12-07','Topic0','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (5,5,'CentreName5','StateX','City0','Pin0','Colony1','Landmark0',22,'Student5','M','1997-12-10','Topic1','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (6,2,'CentreName2','StateX','City1','Pin1','Colony2','Landmark1',14,'Student6','F','1994-08-25','Topic2','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (7,4,'CentreName4','StateX','City2','Pin2','Colony3','Landmark2',19,'Student7','M','2001-07-27','Topic3','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (8,3,'CentreName3','StateX','City3','Pin3','Colony0','Landmark3',20,'Student8','M','2003-01-29','Topic0','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (9,2,'CentreName2','StateX','City4','Pin4','Colony1','Landmark4',21,'Student9','M','1996-04-19','Topic1','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (10,5,'CentreName5','StateX','City0','Pin0','Colony2','Landmark0',14,'Student10','F','2001-08-28','Topic2','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (11,1,'CentreName1','StateX','City1','Pin1','Colony3','Landmark1',19,'Student11','F','2001-12-11','Topic3','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (12,5,'CentreName5','StateX','City2','Pin2','Colony0','Landmark2',22,'Student12','F','2002-12-11','Topic0','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (13,2,'CentreName2','StateX','City3','Pin3','Colony1','Landmark3',16,'Student13','M','1999-10-31','Topic1','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (14,3,'CentreName3','StateX','City4','Pin4','Colony2','Landmark4',17,'Student14','F','1999-05-04','Topic2','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (15,5,'CentreName5','StateX','City0','Pin0','Colony3','Landmark0',22,'Student15','M','2000-03-06','Topic3','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (16,1,'CentreName1','StateX','City1','Pin1','Colony0','Landmark1',17,'Student16','M','2007-09-01','Topic0','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (17,5,'CentreName5','StateX','City2','Pin2','Colony1','Landmark2',21,'Student17','M','1990-11-24','Topic1','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (18,5,'CentreName5','StateX','City3','Pin3','Colony2','Landmark3',14,'Student18','M','2001-09-05','Topic2','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (19,3,'CentreName3','StateX','City4','Pin4','Colony3','Landmark4',15,'Student19','F','2002-03-24','Topic3','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (20,5,'CentreName5','StateX','City0','Pin0','Colony0','Landmark0',17,'Student20','F','2006-10-02','Topic0','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (21,4,'CentreName4','StateX','City1','Pin1','Colony1','Landmark1',18,'Student21','F','2005-12-09','Topic1','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (22,5,'CentreName5','StateX','City2','Pin2','Colony2','Landmark2',19,'Student22','F','2000-07-21','Topic2','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (23,3,'CentreName3','StateX','City3','Pin3','Colony3','Landmark3',13,'Student23','F','2005-07-15','Topic3','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (24,1,'CentreName1','StateX','City4','Pin4','Colony0','Landmark4',13,'Student24','M','1990-05-11','Topic0','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (25,4,'CentreName4','StateX','City0','Pin0','Colony1','Landmark0',20,'Student25','F','1994-09-22','Topic1','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (26,2,'CentreName2','StateX','City1','Pin1','Colony2','Landmark1',22,'Student26','F','2001-01-04','Topic2','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (27,4,'CentreName4','StateX','City2','Pin2','Colony3','Landmark2',22,'Student27','M','2003-03-01','Topic3','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (28,3,'CentreName3','StateX','City3','Pin3','Colony0','Landmark3',20,'Student28','F','1995-10-20','Topic0','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (29,3,'CentreName3','StateX','City4','Pin4','Colony1','Landmark4',16,'Student29','F','1997-03-16','Topic1','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (30,4,'CentreName4','StateX','City0','Pin0','Colony2','Landmark0',17,'Student30','F','1990-10-26','Topic2','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (31,1,'CentreName1','StateX','City1','Pin1','Colony3','Landmark1',16,'Student31','M','2002-04-01','Topic3','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (32,3,'CentreName3','StateX','City2','Pin2','Colony0','Landmark2',21,'Student32','M','2010-05-24','Topic0','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (33,4,'CentreName4','StateX','City3','Pin3','Colony1','Landmark3',19,'Student33','M','2000-11-03','Topic1','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (34,5,'CentreName5','StateX','City4','Pin4','Colony2','Landmark4',21,'Student34','F','1992-07-02','Topic2','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (35,2,'CentreName2','StateX','City0','Pin0','Colony3','Landmark0',13,'Student35','M','1993-03-20','Topic3','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (36,1,'CentreName1','StateX','City1','Pin1','Colony0','Landmark1',14,'Student36','M','1997-05-21','Topic0','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (37,3,'CentreName3','StateX','City2','Pin2','Colony1','Landmark2',14,'Student37','F','1991-05-02','Topic1','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (38,4,'CentreName4','StateX','City3','Pin3','Colony2','Landmark3',19,'Student38','F','1998-10-23','Topic2','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (39,5,'CentreName5','StateX','City4','Pin4','Colony3','Landmark4',19,'Student39','F','2000-07-27','Topic3','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (40,4,'CentreName4','StateX','City0','Pin0','Colony0','Landmark0',19,'Student40','M','1999-06-08','Topic0','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (41,1,'CentreName1','StateX','City1','Pin1','Colony1','Landmark1',19,'Student41','F','2010-10-21','Topic1','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (42,4,'CentreName4','StateX','City2','Pin2','Colony2','Landmark2',21,'Student42','M','2008-06-05','Topic2','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (43,5,'CentreName5','StateX','City3','Pin3','Colony3','Landmark3',14,'Student43','M','1993-05-05','Topic3','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (44,5,'CentreName5','StateX','City4','Pin4','Colony0','Landmark4',17,'Student44','M','2004-12-06','Topic0','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (45,2,'CentreName2','StateX','City0','Pin0','Colony1','Landmark0',15,'Student45','F','1999-04-17','Topic1','Subject0','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (46,3,'CentreName3','StateX','City1','Pin1','Colony2','Landmark1',17,'Student46','F','2006-11-06','Topic2','Subject1','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (47,1,'CentreName1','StateX','City2','Pin2','Colony3','Landmark2',18,'Student47','M','2007-10-16','Topic3','Subject2','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (48,5,'CentreName5','StateX','City3','Pin3','Colony0','Landmark3',18,'Student48','F','1995-07-21','Topic0','Subject3','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (49,5,'CentreName5','StateX','City4','Pin4','Colony1','Landmark4',15,'Student49','F','1991-10-23','Topic1','Subject4','Student');
INSERT INTO registration_form (registration_no,centre_id,cname,state,city,pincode,colony,landmark,age,name,gender,dob,topic,subject,type) VALUES (50,5,'CentreName5','StateX','City0','Pin0','Colony2','Landmark0',17,'Student50','M','2000-02-26','Topic2','Subject0','Student');
INSERT INTO login (login_id,password) VALUES (1,'pass1');
INSERT INTO login (login_id,password) VALUES (2,'pass2');
INSERT INTO login (login_id,password) VALUES (3,'pass3');
INSERT INTO login (login_id,password) VALUES (4,'pass4');
INSERT INTO login (login_id,password) VALUES (5,'pass5');
INSERT INTO login (login_id,password) VALUES (6,'pass6');
INSERT INTO login (login_id,password) VALUES (7,'pass7');
INSERT INTO login (login_id,password) VALUES (8,'pass8');
INSERT INTO login (login_id,password) VALUES (9,'pass9');
INSERT INTO login (login_id,password) VALUES (10,'pass10');
INSERT INTO login (login_id,password) VALUES (11,'pass11');
INSERT INTO login (login_id,password) VALUES (12,'pass12');
INSERT INTO login (login_id,password) VALUES (13,'pass13');
INSERT INTO login (login_id,password) VALUES (14,'pass14');
INSERT INTO login (login_id,password) VALUES (15,'pass15');
INSERT INTO login (login_id,password) VALUES (16,'pass16');
INSERT INTO login (login_id,password) VALUES (17,'pass17');
INSERT INTO login (login_id,password) VALUES (18,'pass18');
INSERT INTO login (login_id,password) VALUES (19,'pass19');
INSERT INTO login (login_id,password) VALUES (20,'pass20');
INSERT INTO login (login_id,password) VALUES (21,'pass21');
INSERT INTO login (login_id,password) VALUES (22,'pass22');
INSERT INTO login (login_id,password) VALUES (23,'pass23');
INSERT INTO login (login_id,password) VALUES (24,'pass24');
INSERT INTO login (login_id,password) VALUES (25,'pass25');
INSERT INTO login (login_id,password) VALUES (26,'pass26');
INSERT INTO login (login_id,password) VALUES (27,'pass27');
INSERT INTO login (login_id,password) VALUES (28,'pass28');
INSERT INTO login (login_id,password) VALUES (29,'pass29');
INSERT INTO login (login_id,password) VALUES (30,'pass30');
INSERT INTO login (login_id,password) VALUES (31,'pass31');
INSERT INTO login (login_id,password) VALUES (32,'pass32');
INSERT INTO login (login_id,password) VALUES (33,'pass33');
INSERT INTO login (login_id,password) VALUES (34,'pass34');
INSERT INTO login (login_id,password) VALUES (35,'pass35');
INSERT INTO login (login_id,password) VALUES (36,'pass36');
INSERT INTO login (login_id,password) VALUES (37,'pass37');
INSERT INTO login (login_id,password) VALUES (38,'pass38');
INSERT INTO login (login_id,password) VALUES (39,'pass39');
INSERT INTO login (login_id,password) VALUES (40,'pass40');
INSERT INTO login (login_id,password) VALUES (41,'pass41');
INSERT INTO login (login_id,password) VALUES (42,'pass42');
INSERT INTO login (login_id,password) VALUES (43,'pass43');
INSERT INTO login (login_id,password) VALUES (44,'pass44');
INSERT INTO login (login_id,password) VALUES (45,'pass45');
INSERT INTO login (login_id,password) VALUES (46,'pass46');
INSERT INTO login (login_id,password) VALUES (47,'pass47');
INSERT INTO login (login_id,password) VALUES (48,'pass48');
INSERT INTO login (login_id,password) VALUES (49,'pass49');
INSERT INTO login (login_id,password) VALUES (50,'pass50');
INSERT INTO login (login_id,password) VALUES (51,'pass51');
INSERT INTO login (login_id,password) VALUES (52,'pass52');
INSERT INTO login (login_id,password) VALUES (53,'pass53');
INSERT INTO login (login_id,password) VALUES (54,'pass54');
INSERT INTO login (login_id,password) VALUES (55,'pass55');
INSERT INTO login (login_id,password) VALUES (56,'pass56');
INSERT INTO login (login_id,password) VALUES (57,'pass57');
INSERT INTO login (login_id,password) VALUES (58,'pass58');
INSERT INTO login (login_id,password) VALUES (59,'pass59');
INSERT INTO login (login_id,password) VALUES (60,'pass60');
INSERT INTO login (login_id,password) VALUES (61,'pass61');
INSERT INTO login (login_id,password) VALUES (62,'pass62');
INSERT INTO login (login_id,password) VALUES (63,'pass63');
INSERT INTO login (login_id,password) VALUES (64,'pass64');
INSERT INTO login (login_id,password) VALUES (65,'pass65');
INSERT INTO login (login_id,password) VALUES (66,'pass66');
INSERT INTO login (login_id,password) VALUES (67,'pass67');
INSERT INTO login (login_id,password) VALUES (68,'pass68');
INSERT INTO login (login_id,password) VALUES (69,'pass69');
INSERT INTO login (login_id,password) VALUES (70,'pass70');



