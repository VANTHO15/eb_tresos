## 1. importProject (nhập dự án vào không gian làm việc)
    tresos_cmd.bat importProject -c C:\temp\myproject
    
## 2. deleteProject (xóa các dự án liên quan đến không gian làm việc)
    tresos_cmd.bat deleteProject -d myproject
    
## 3. renameProject (đổi tên dự án không gian làm việc)
    tresos_cmd.bat renameProject myproject mynewproject
    
## 4. import  (thực thi nhập khẩu)
    tresos_cmd.bat import myproject myimporter
    
## 5. listimporter (liệt kê tất cả các nhà nhập khẩu của một dự án)
    tresos_cmd.bat listimporter myproject
    
## 6. verify (xác minh cấu hình của dự án và có xuất thông tin cảnh báo/thông tin ra đầu ra hay không)
    tresos_cmd.bat -Dinfo=false -Dwarning=false verify myproject
    
## 7. generate (tạo mã của một dự án nhất định và có xuất thông tin cảnh báo/thông tin ra đầu ra hay không)
    tresos_cmd.bat -Dinfo=false -Dwarning=false generate myproject
    
## 8. listmodes (liệt kê tất cả các chế độ được trình tạo hỗ trợ)
    tresos_cmd.bat listmodes myproject
    
## 9. make  (sử dụng trình tạo tùy chỉnh trong dự án)
    tresos_cmd.bat make generate_SWC-T myproject
    
## 10. autoconfigure (thực thi thủ thuật tự động đã được cấu hình và kiểm tra cho một dự án)
    tresos_cmd.bat autoconfigure myproject
    
## 11. listautoconfigure (liệt kê tất cả các wizard tự động của một project)
    tresos_cmd.bat listautoconfigure myproject
    
## 12. upgradeModuleConfigs (nâng cấp tất cả các mô-đun đã bật của dự án lên phiên bản mới nhất)
    tresos_cmd.bat upgradeModuleConfigs myproject -onlyEnabled -type Can;EcuC
    
## 13. legacy list (liệt kê tất cả các mô-đun đã cài đặt hỗ trợ tạo mã kế thừa)
    tresos_cmd.bat legacy list
    
## 14. legacy generate (xác minh cấu hình mô-đun và tạo mã, chú ý đến sự khác biệt so với lệnh thứ bảy)
    Lệnh sau hiển thị việc tải cấu hình mô-đun có tên Com từ tệp All.epc và tệp epc được coi là phiên bản Autosar4.0.3.
    tresos_cmd.bat -DValidate=true legacy generate -n Com -g Com_TS_T16D4M2I0R0 -g Custom -u All.epc@asc:4.0.3
    
## 15. legacy verify (xác minh thông tin mô-đun và thông tin đầu ra, cảnh báo, lỗi)
    tresos_cmd.bat legacy listmodes
    
## 16. legacy listmodes (ở chế độ kế thừa, liệt kê tất cả các chế độ tạo của trình tạo mô-đun)
    tresos_cmd.bat legacy listmodes
    
## 17. legacy make (ở chế độ kế thừa, thực thi trình tạo)
    Ví dụ sau tải nội dung của myEpc.epc và myOther.epc cùng nhau. Lưu ý rằng chúng được hợp nhất, không bị ghi đè. generate_SWC-T là trình tạo tùy chỉnh.
    tresos_cmd.bat -DmergeConfigs=true legacy make generate_SWC-T myEpc.epc myOther.epc
    
## 18. legacy tree (mô-đun đầu ra và mô hình dữ liệu trong cấu hình mô-đun)
    Tải cấu hình có tên Com từ tệp All.epc vào mô hình dữ liệu và in mô hình dữ liệu ở dạng cây. Tất cả các tệp .epc được coi là định dạng Autosar4.3.0.
    tresos_cmd.bat legacy tree -n Com All.epc@asc:4.0.3
    
## 19. vsmd (tạo vsmd)
    Ví dụ sau cho thấy: Dựa trên tệp Com.epd ở định dạng StMD, tệp MyCom.xdm ở định dạng VSMD được tạo (điều này rất quan trọng!!!!!!!!!!!!!!!!!!) . Trong số đó, VSMD cũng chứa GÓI AR TS_T16D4M2I0R0
    tresos_cmd.bat -DMapOptionalAsLists=false legacy vsmd Com.epd Mycom.xdm TS_T16D4M2I0R0
    
## 20. legacy vsmdcheck (kiểm tra xem VSMD có tuân theo StMD không)
    Ví dụ sau đây cho thấy: xác minh tệp loại VSMD VSMD.epd đối với tệp StMD. Nhưng quy tắc EcucSws_1035 không kiểm tra.
    tresos_cmd.bat -DValidate=true legacy vsmdcheck AUTOSAR_MOD_ECUConfigurationParameters.arxml@asc:4.0.3 VSMD.epd@asc:4.0.3 asc:4.0.3 -ignore EcucSws_1035
    
## 21. Legacy listrules (liệt kê tất cả các luật của lệnh Legacy vsmdcheck)
    tresos_cmd.bat legacy listrules
    
## 22. cryptoto (mô-đun mã hóa và ký)
    Không có ví dụ nào cho lệnh này.

## 23. convert (hợp nhất và chuyển đổi tập tin)
    Không có ví dụ nào cho lệnh này.

## 24. Legacy convert (chuyển đổi tập tin)
    Ví dụ sau đây cho thấy: chuyển đổi tệp epd thành tệp xdm (rất quan trọng!!!!!!!!!!!!!!!!!!!!!
    tresos_cmd.bat -DValidate=false -DMapOptionalAsLists=false legacy convert in.epd out.xdm
    
    Ví dụ sau đây cho thấy: tải các tệp in1.epd, in2.epd, in3.xdm và cuối cùng tạo tệp out.epc.
    tresos_cmd.bat -DValidate=false -DMapOptionalAsLists=false -Duuids=true legacy convert in1.epd in2.epd in3.xdm out.epc@asc:4.0.3
    
    Ví dụ sau đây cho thấy: tải tệp in1.xml (được nhập bằng trình nhập Fibex) và in2.arxml (được nhập dưới dạng mô tả hệ thống Autosar) và hợp nhất hai tệp. Hệ thống được đề cập trong /SYSTEM/system và ECU được đề cập trong /AUTOSAR/ECUInstance/ecuInstance_1  cần được đưa vào tệp in2.arxml. Cuối cùng, tệp out.tdb ở định dạng tệp tresosDB được xuất ra .
    tresos_cmd.bat -Dsystem="/SYSTEM/system" -DecuInstance="/AUTOSAR/ECUInstance/ecuInstance_1" legacy convert in1.xml@fibex in2.arxml@sysd out.tdb
    
## 25. xdmconvert kế thừa (cải thiện khả năng tương thích Autosar của các tệp XDM)
    Không có ví dụ nào cho lệnh này.

## 26. batch  (thực thi nhiều lệnh EB, đặt các lệnh trong batch file và thực hiện nhiều lệnh theo thứ tự)
