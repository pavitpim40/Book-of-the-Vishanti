# COMMAND 1

`docker pull [image-name]` : ดาวน์โหลด image จาก docker hub

### รัน container จาก image (หากไม่มีในเครื่องจะ pull ให้ก่อน : pull + start)
`docker run [image-name]` : นำ image ในเครื่องมาสร้่าง instance container (ต้องเปิด terminal ทิ้งไว้) 
`docker run -d [image-name]`: รันบน background + แสดงผลแค่ container id

** docker run ต้องตามด้วย [image-name] เสมอ

### เช็คสถานะ container

`docker ps` : แสดงรายการ container ทั้งหมดที่รันอยู่บน foreground  
`docker ps -a` แสดงรายการ container ทั้งหมด (foreground,background และที่ถูก kill ไปแล้ว)  

หมายเหตุ : a = absent (container ที่ซ่อนไว้ = background + kill)

### stop container

`cmd + c` หรือ `ctrl + c` : สำหรับ foreground  
`docker stop [container-id]` : สำหรับ background

### star container
`docker start [container-id]` : จะ start ให้ใหม่ (foreground)

# COMMAND 2

## docker run แบบ ใส่ port

`docker run -p:[host-port]:[container-port]  [image-name]`