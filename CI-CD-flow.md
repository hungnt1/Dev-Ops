
## Quy trình CI/CD tham khảo

Có rất nhiều quy trình, công cụ khác nhau để ứng dụng CI/CD vào dự án. Nội dung của bài viết này dựa trên kinh nghiệm cho các dự án của mình triển khai cũng như đặc thù là các hệ thống web, và viết bằng PHP (PHP hoặc Python hoặc abc…không quá quan trọng trong ngữ cảnh chia sẻ về CI/CD).

Dưới đây là các bước thông thường của quá trình release tính năng trong một dự án thuộc hệ thống ......  
– **Bước 1:** [Manual] Khởi tạo repository và có branch default là master và dev. Cài đặt trên Gitlab .  

– **Bước 2:** [Manual] Trừ owner ra, thì các coder sẽ push code tính năng lên branch dev. Coder sẽ tạo branch từ nhánh dev dựa theo module cần phát triển. 
– **Bước 3:** [Auto] Hệ thống tự động thực hiện test source code, nếu PASS thì sẽ deploy tự động (rsync) code lên server beta.  
– **Bước 4:** [Manual] Tester/QA sẽ vào hệ thống beta để làm UAT (User Acceptance Testing) và confirm là mọi thứ OK.  
– **Bước 5:** [Manual] Coder hoặc owner sẽ vào tạo Merge Request, và merge từ branch dev sang branch master.  
– **Bước 6:** [Manual] Owner sẽ accept merge request.  
– **Bước 7:** [Auto] Hệ thống sẽ tự động thực hiện test source code, nếu PASS sẽ enable tính năng cho phép deploy lên staging server.  
– **Bước 8:** [Manual] Owner review là merge request OK, test OK. Tiến hành nhấn nút để deploy các thay đổi lên môi trường staging.  
– **Bước 9:** [Manual] Tester/QA sẽ vào hệ thống staging để làm UAT và confirm mọi thứ OK. Nếu không OK, hệ thống sẽ pending ở hệ thống Staging. Chờ merge request tiếp theo.
– **Bước 10:** [Manual] Owner review là merge request OK, test OK. Tiến hành khởi tạo tag release và chuyển cho team Devops . Devops sẽ triển khai lên production và chuyển cho Tester/QA
– **Bước 11:** [Manual] Tester/QA sẽ vào hệ thống production để làm UAT và confirm mọi thứ OK. Nếu không OK, Owner có thể nhấn nút Deploy phiên bản master trước đó để rollback hệ thống về trạng thái stable trước đó.
– **Bước 11:** [Manual] Thắp nhang và hy vọng khách hàng không chửi rủa hoặc email complain.
