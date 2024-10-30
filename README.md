# Conclusion OOP
oop มีหลักอยู่ 4 อย่าง คือ 
## 1.Abstrack 
- มีส่วนประกอบย่อย อยู่ 2 อย่าง คือ 1 class และ 2 method ซึ่ง class เป็น object ที่มี method อยู่ในนั้น ตัวอย่าง

class Car { constructor(color, brand) { this.color = color; this.brand = brand; }

drive() {
    console.log(`The ${this.color} ${this.brand} is driving.`);
}

stop() {
    console.log(`The ${this.color} ${this.brand} has stopped.`);
}
}

ในตัวอย่างโค๊ดมี class Car ที่รับ 2 property ในคลาสมี 2 method โดยที่ผายนอกจะไม่รู้ว่า แต่ละmethod ทำอะไร เวลาเรียกใช้ให้แสดงก็สามารถทำงานได้ และป้องกันการถึงจากแหล่งที่อื่นที่ไม่ใช่ตัวมันเอง

## 2.Encapsulation 
- การห่อหุ้มการปกป้องข้อมูล จากโค๊ดตัวอย่างจะไม่สามารถเข้าถึงค่าของตัวแปรได้โดยตรง เช่นจะใช้ cosole.log(color) จะไม่สามามารถเข้าถึงค่าของ color ได้ การจะเข้าถึงค่าต้องเข้าผ่านเฉพาะ method ที่กำหนดไว้เท่านั้น

สมมติ const myCar = new Car("red","honda") การจะเข้าถึงให้แสดงค่าparameter เข้าผ่าน method myCar.drive()

## 3.การสืบทอด
- เป็นการเข้าถึงobject จากที่สืบทอด และสามารถเพิ่ม parameter หรือ method เข้าไปเพิ่มได้หรือสามารถ เขียน method ชื่อซ้ำทับไปได้ เช่น

class Car { #color; // ห่อหุ้มด้วย # #brand;
constructor(color, brand) {
    this.#color = color;
    this.#brand = brand;
}

getColor() {
    return this.#color;
}
}

ต่อไปการสืบทอด 'class ElectricCar extends Car { // การสืบทอดจากคลาส Car constructor(color, brand, batteryLevel) { super(color, brand); this.batteryLevel = batteryLevel; } }

## 4.ความสามารถในการใช้ method เดียวกันที่ต่าง object กัน 
- จะแสดงตามตัวอย่าง เช่นมี 2 class แต่มัน method ชื่อเดียวกันเลยซึ่ง method ชื่อเดียวกัน แต่ในmethod ที่ชื่อเดัยวกันทำงานไม่เหมือนกัน โค๊ดตัวอย่าง

class Car { drive() { console.log("The car is driving."); } }
class ElectricCar extends Car { drive() { console.log("The electric car is driving silently."); } }
function testDrive(car) { car.drive(); }
const car = new Car(); const electricCar = new ElectricCar();
testDrive(car); // Output: The car is driving. testDrive(electricCar); // Output: The electric car is driving silently.
จะเห็นว่า method drive ใน class Car ต่างจาก class ElectricCar
เมื่อมีการเรียกใช้ function testDrive ถึงแม้ method เดียวกันแต่ผลลัพธ์ที่ได้ต่างกัน
