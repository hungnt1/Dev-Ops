## CI - _Continuous Integration_

_CI là Continuous Integration. Nó là phương pháp phát triển phần mềm yêu cầu các thành viên của team tích hợp công việc của họ thường xuyên, mỗi ngày ít nhất một lần. Mỗi tích hợp được "build" tự động (bao gồm cả test) nhằm phát hiện lỗi nhanh nhất có thể. Cả team nhận thấy rằng cách tiếp cận này giảm thiểu vấn đề tích hợp và cho phép phát triển phần mềm nhanh hơn._
Túm lại, thì lợi ích của việc sử dụng CI sẽ là:

-   Giảm thiểu rủi ro nhờ việc phát hiện lỗi và fix sớm, tăng chất lượng phần mềm nhờ việc tự động test và inspect (đây cũng là một trong những lợi ích của CI, code được inspect tự động dựa theo config đã cài đặt, đảm bảo coding style, chẳng hạn một function chỉ được dài không quá 10 dòng code ...)
-   Giảm thiểu những quy trình thủ công lặp đi lặp lại (build css, js, migrate, test...), thay vì đó là build tự động, chạy test tự động
-   Sinh ra phần mềm có thể deploy ở bất kì thời gian, địa điểm
 ## CD -  Continuous Delivery
- Trong khi Continuous Integration là quy trình để build và test tự động, thì Continuous Delivery (tạm dịch là chuyển giao liên tục) lại nâng cao hơn một chút, bằng cách triển khai tất cả thay đổi về code (đã được build và test) đến môi trường testing hoặc staging. Continuous Delivery cho phép developer tự động hóa phần testing bên cạnh việc sử dụng unit test, kiểm tra phần mềm qua nhiều thước đo trước khi triển khai cho khách hàng (production). Những bài test này bao gồm UI testing, load testing, integration testing, API testing... Nó tự động hoàn toàn quy trình release phần mềm.
## CD - Continuos Deployment
- Có một khái niệm nữa là Continuos Deployment, và hai khái niệm này thường hay bị nhầm lẫn với nhau. Nếu Continuous Delivery là triển khai code lên môi trường staging, và deploy thủ công lên môi trường production, thì Continuous Deployment (cũng viết tắt là CD ![😄](https://twemoji.maxcdn.com/2/72x72/1f604.png)) lại là kỹ thuật để triển khai code lên môi trường production một cách tự động, và cũng nên là mục tiêu của hầu hết công ty.

![](https://viblo.asia/uploads/59ee0d73-9611-4a33-a2e6-0116fe8e71c4.png)



![](https://images.viblo.asia/1c718ad6-e26b-4785-b375-0bcbf901a084.png)


## https://viblo.asia/p/ci-cd-va-devops-07LKXYXDZV4
