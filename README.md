1. importProject (nhập dự án vào không gian làm việc)

tresos_cmd.bat importProject -c C:\temp\myproject
2. deleteProject (xóa các dự án liên quan đến không gian làm việc)

tresos_cmd.bat xóaProject -d myproject
3. renameProject (đổi tên dự án không gian làm việc)

tresos_cmd.bat renameProject myproject mynewproject
4. nhập (thực thi nhập khẩu)

tresos_cmd.bat nhập myproject myimporter
5. listimporter (liệt kê tất cả các nhà nhập khẩu của một dự án)

tresos_cmd.bat listimporter myproject
6. xác minh (xác minh cấu hình của dự án và có xuất thông tin cảnh báo/thông tin ra đầu ra hay không)

tresos_cmd.bat -Dinfo= false -Dwarning= false xác minh dự án của tôi
7. tạo (tạo mã của một dự án nhất định và có xuất thông tin cảnh báo/thông tin ra đầu ra hay không)

tresos_cmd.bat -Dinfo= false -Dwarning= false tạo myproject
8. listmodes (liệt kê tất cả các chế độ được trình tạo hỗ trợ)

tresos_cmd.bat listmodes myproject
9. thực hiện (sử dụng trình tạo tùy chỉnh trong dự án)

tresos_cmd.bat tạo ra_SWC -T myproject
10. autoconfigure (thực thi thủ thuật tự động đã được cấu hình và kiểm tra cho một dự án)

tresos_cmd.bat autoconfigure myproject
11. listautoconfigure (liệt kê tất cả các wizard tự động của một project)

tresos_cmd.bat listautoconfigure myproject
12. upgradeModuleConfigs (nâng cấp tất cả các mô-đun đã bật của dự án lên phiên bản mới nhất)

tresos_cmd.bat upgradeModuleConfigs myproject -onlyEnabled -type Can;EcuC
13. danh sách kế thừa (liệt kê tất cả các mô-đun đã cài đặt hỗ trợ tạo mã kế thừa)

danh sách kế thừa tresos_cmd.bat
14. Tạo kế thừa (xác minh cấu hình mô-đun và tạo mã, chú ý đến sự khác biệt so với lệnh thứ bảy)

Lệnh sau hiển thị việc tải cấu hình mô-đun có tên Com từ tệp All.epc và tệp epc được coi là phiên bản Autosar4.0.3.

tresos_cmd.bat -DValidate= true Legacy generate -n Com -g Com_TS_T16D4M2I0R0 -g Custom -u All.epc@asc: 4.0 . 3
15. xác minh kế thừa (xác minh thông tin mô-đun và thông tin đầu ra, cảnh báo, lỗi)

tresos_cmd.bat danh sách kế thừa
16. listmodes kế thừa (ở chế độ kế thừa, liệt kê tất cả các chế độ tạo của trình tạo mô-đun)

tresos_cmd.bat danh sách kế thừa
17. chế độ kế thừa (ở chế độ kế thừa, thực thi trình tạo)

Ví dụ sau tải nội dung của myEpc.epc và myOther.epc cùng nhau. Lưu ý rằng chúng được hợp nhất, không bị ghi đè. generate_SWC-T là trình tạo tùy chỉnh.

tresos_cmd.bat -DmergeConfigs= true Legacy make generate_SWC -T myEpc.epc myOther.epc
18. cây kế thừa (mô-đun đầu ra và mô hình dữ liệu trong cấu hình mô-đun)

Tải cấu hình có tên Com từ tệp All.epc vào mô hình dữ liệu và in mô hình dữ liệu ở dạng cây. Tất cả các tệp .epc được coi là định dạng Autosar4.3.0.

cây kế thừa tresos_cmd.bat -n Com All.epc@asc: 4.0 .3
19. vsmd (tạo vsmd)

Ví dụ sau cho thấy: Dựa trên tệp Com.epd ở định dạng StMD, tệp MyCom.xdm ở định dạng VSMD được tạo (điều này rất quan trọng!!!!!!!!!!!!!!!!!!) . Trong số đó, VSMD cũng chứa GÓI AR TS_T16D4M2I0R0

tresos_cmd.bat -DMapOptionalAsLists= sai kế thừa vsmd Com.epd Mycom.xdm TS_T16D4M2I0R0
20. kiểm tra kế thừa vsmdcheck (kiểm tra xem VSMD có tuân theo StMD không)

Ví dụ sau đây cho thấy: xác minh tệp loại VSMD VSMD.epd đối với tệp StMD. Nhưng quy tắc EcucSws_1035 không kiểm tra.

tresos_cmd.bat -DValidate= true Legacy vsmdcheck AUTOSAR_MOD_ECUConfigurationParameters.arxml@asc: 4.0 3 VSMD.epd@asc : 4.0 3 asc: 4.0 3 -ignore EcucSws_1035
21. Legacy listrules (liệt kê tất cả các luật của lệnh Legacy vsmdcheck)

danh sách kế thừa tresos_cmd.bat
22. cryptoto (mô-đun mã hóa và ký)

Không có ví dụ nào cho lệnh này.

23. convert (hợp nhất và chuyển đổi tập tin)

Không có ví dụ nào cho lệnh này.

24. Legacy convert (chuyển đổi tập tin)

Ví dụ sau đây cho thấy: chuyển đổi tệp epd thành tệp xdm (rất quan trọng!!!!!!!!!!!!!!!!!!!!!)

tresos_cmd.bat -DValidate= false -DMapOptionalAsLists= false chuyển đổi kế thừa trong .epd ra .xdm
Ví dụ sau đây cho thấy: tải các tệp in1.epd, in2.epd, in3.xdm và cuối cùng tạo tệp out.epc.

tresos_cmd.bat -DValidate= false -DMapOptionalAsLists= false -Duuids= true Legacy convert in1.epd in2.epd in3.xdm out .epc @asc: 4.0 .3
Ví dụ sau đây cho thấy: tải tệp in1.xml (được nhập bằng trình nhập Fibex) và in2.arxml (được nhập dưới dạng mô tả hệ thống Autosar) và hợp nhất hai tệp. Hệ thống được đề cập trong /SYSTEM/system và ECU được đề cập trong /AUTOSAR/ECUInstance/ecuInstance_1  cần được đưa vào tệp in2.arxml. Cuối cùng, tệp out.tdb ở định dạng tệp tresosDB được xuất ra .

tresos_cmd.bat -Dsystem= " /SYSTEM/system " -DecuInstance= " /AUTOSAR/ECUInstance/ecuInstance_1 " chuyển đổi kế thừa in1.xml@fibex in2.arxml@sysd ra .tdb
25. xdmconvert kế thừa (cải thiện khả năng tương thích Autosar của các tệp XDM)

Không có ví dụ nào cho lệnh này.

26. hàng loạt (thực thi nhiều lệnh EB, đặt các lệnh trong tệp bó và thực hiện nhiều lệnh theo thứ tự)
