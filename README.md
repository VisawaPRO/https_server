# Example นี้มีชื่อว่า https_server
โดยการทำงานของ Example นี้คือการทำให้ esp32 เป็น server โดย ตอบสนองต่อคำขอ GET ด้วย Hello Secure World!
#
ขั้นตอนแรกเลือก Example
# ![image](https://github.com/user-attachments/assets/e3a39320-1635-4901-a060-25124b00d1be)
แล้วกดmenuconfig
# ![image](https://github.com/user-attachments/assets/7ce64369-0a02-4c20-ac59-df53eb34692a)
เลือก Example Connection Configuration เพื่อแก้ไขชื่อและรหัส wifi และ save
# ![image](https://github.com/user-attachments/assets/ba97b110-4dd5-41b2-aa0d-8705970b357e)
รันและbuildโปรแกรม
# ![image](https://github.com/user-attachments/assets/8e1fcf35-395f-4ae2-9ac7-347829f1ce74)
ให้สังเกตุ ip แล้วนำไปเข้าในเบราว์เซอร์ เช่น https://192.168.1.34
# ![image](https://github.com/user-attachments/assets/a7432fca-72ca-426d-9b21-9bbc9ce2f723)
# ![image](https://github.com/user-attachments/assets/0f014a62-f22a-4c97-b48c-b339a59ba18f)

# แก้ไขเพิ่มเติม
จะสังเกตุได้ว่าในหน้าเบราว์เซอร์ใน code กำหนดให้ Hello Secure World! แต่หน้าเบราว์เซอร์แสดง Header fields are too long
แก้โดยกด menuconfig และค้นหา http
# ![image](https://github.com/user-attachments/assets/2fbfea38-3d2a-4401-bba5-fa871fcc4cd4)
ปรับที่ Max HTTP Request Header Length และ Max HTTP URI Length ให้เป็น 1024 แล้วกด save
# ![image](https://github.com/user-attachments/assets/4611d402-b19b-4c1b-9de8-59eec380bee1)
รันและbuildโปรแกรม
# ![image](https://github.com/user-attachments/assets/4a752ce3-9de3-4759-9b64-cdbcb1fb2d64)
เข้าในเบราว์เซอร์ https://192.168.1.34
# ![image](https://github.com/user-attachments/assets/51a86a8b-63f7-4b01-accc-662f4a1f3cc8)
# ![image](https://github.com/user-attachments/assets/3bb3d068-a2de-4578-bb49-f6a2e324a43b)
สามารถแก้ไขข้อความที่หน้าเว็บได้ที่main.c
```
static esp_err_t root_get_handler(httpd_req_t *req)
{
    httpd_resp_set_type(req, "text/html");
    httpd_resp_send(req, "<h1>Hello Visawa!</h1>", HTTPD_RESP_USE_STRLEN);

    return ESP_OK;
}
```
# ![image](https://github.com/user-attachments/assets/aeeb1e60-36a6-4e4a-95a3-95dda93a6f34)

