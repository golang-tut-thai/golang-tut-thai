Function
การประกาศ Function เราจะใช้ keyword "func" โดยวิธีประกาศเป็นดังนี้

	func function_name (input_argument) (return) {
	     statement..
	}
	  
ตัวอย่าง

	func square (f float64) float64 {
	     return f*f
	}
	
จากที่เห็นข้างต้น เราประกาศ function ชื่อ square โดยรับค่าเข้า function เพียง 1 ตัวเป็น type float64
และ return ค่าออกไปเพียงค่าเดียว โดยค่าที่ return ออกไปเป็น type float64 ถ้ามีการ เขียนไว้ว่าจะมีการ return ค่าอะไรออกมาสักตัวนั้น 
เราจะต้องใช้ keyword "return" ไว้ข้างในด้วย ซึ่งเราจะสังเกตเห็น ว่ามีการ return f*f ออกมานั้นเอง

แต่เราอย่าลืมว่า golang นั้นมีสามารถ assign ค่าให้ตัวแปรได้หลายค่า เพราะฉะนั้น function ก็สามารถ 
return ค่าได้หลายค่าเช่นกัน ดัง code ข้างต้น
       
	func Mysquare (f float64) (float64, bool) {
		return f*f, true
	}
	
จาก function ข้างบนนั้น จะมีการ return ค่าออกมาสองค่า เป็น type float64 และ boolean เป็นต้น และจะต้องใส่ () ครอบ type ที่ return ด้วย และ golang ยังมาสามารถ return ตัวแปรออกไปได้ด้วยเช่น

	func Mysquare (f float64) (v float64, ok bool) {
		v, ok := f*f, true
		return
	}

ซึ่งเราสามารถส่งค่าของตัวแปร v และ ok กลับไปได้ด้วย และเมื่อเจอ keyword return มันจะส่งค่าของ v และ ok กลับไป

เอาหล่ะ เมื่อเรามาดูวิธีสร้าง function กันแล้วเรามาดูวิธีการ เรียกกันบ้าง
การเรียกใช้นั้นจะได้ทำได้คล้าย ภาษา C เลยเมื่อ function ไม่มี return ออกมาจะสามารถเรียกออกมาได้เลย 
แต่เมื่อมีการประกาศ return นั้นจะต้องหาค่าที่มารับ เช่น
		
	 v, ok := Mysquare(2.5)

Function Literal
function literal นั้นเป็นการสร้าง function ในตัวแปรได้ ดังตัวอย่าง

	 g := func(i int) { fmt.Println(i) }

โดย ประกาศตัวแปร g โดยมีค่าเท่ากับ function ที่รับค่า int แต่ไม่มีการ return ค่าออกมา(เป็น void)
และเราสามารถเรียกใช้ได้โดย การเรียก

	g(2)

โดย เรียกชื่อตัวแปร และใส่ค่าเข้าไปทำให้เรียกเหมือน function
นอกจากนี้ funcition literal ยังสามารถใช้ใน return ใน function ได้อีกด้วยและยังเก็บค่าของตัวแปรได้อีก เช่น

	func adder() (func(int) int) {
	     var x int
	     return func(delta int) int {
	     	    x += delta
		    return x
		}
	}
	
	f := adder()
	fmt.Print(f(1))
	fmt.Print(f(20))
	fmt.Print(f(20))
	fmt.Print(f(300))

	คำตอบจะได้ออกมาเป็น 1 21 321

