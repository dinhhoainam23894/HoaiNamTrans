[Source](https://www.codeproject.com/Tips/808058/Reasons-for-using-design-patterns "Permalink to Reasons for using design patterns")

# Lý do nên sử dụng design patterns

## Giới thiệu

Tiếp theo bài viết trước có tựa đề là [Tại sao thiết kế là tối quan trọng đối với Phát triển Phần mềm][1], Tôi muốn tóm tắt lại về khía cạnh nâng cao hơn 1 chút gọi là `Design Patterns`.  Như bài báo trước của tôi, ý tưởng xuất hiện trong một cuộc thảo luận liên quan đến sự thành công của thiết kế phần mềm với một đồng nghiệp làm việc cùng. Nội dung chính của cuộc thảo luận là về những ý kiến cho rằng `Design Patterns` quá tốn thời gian để sử dụng trong lĩnh vực phát triển phần mềm. Mục đích của tôi ở đây để chứng mình rằng tại sao tôi tin điều đó là sai lầm.

Tôi sẽ không đi sâu vào nguyên lý chi tiết hay thực hiện bất cứ `Design Patterns` cụ thể nào. Có rất nhiều nguồn tuyệt vời ở những nơi có ích hơn.

## Design Pattern là cái gì?

Vậy thì sau tất cả,`Design Pattern` thực chất là cái gì? Dưới đây là 1 vài thuật ngữ và định nghĩa:

Trích từ [Wikipedia][2]:

> "Một design pattern trong kiến trúc và khoa học máy tính là một cách chính thức để ghi lại một giải pháp cho một vấn đề thiết kế trong một lĩnh vực chuyên môn cụ thể."

Trích từ [Data & Object Factory][3]:

> "Design patterns là các giải pháp định kỳ cho các vấn đề thiết kế phần mềm mà bạn tìm thấy trong phát triển ứng dụng trong thế giới thực.Patterns là về thiết kế và tương tác của các đối tượng, cũng như cung cấp một nền tảng truyền thông liên quan đến các giải pháp tiện lợi, có thể tái sử dụng đối với những thách thức lập trình thường gặp.. "

Do đó 1 `Design Pattern` là một mục đích mang tính trừu tưởng của 1 vấn đề nói chung, Có thể được áp dụng cho một giải pháp cụ thể.Khi các nhà phát triển phần mềm có xu hướng giải quyết nhiều loại vấn đề tương tự, điều đó có nghĩa là bất kỳ giải pháp phần mềm nào sẽ kết hợp các yếu tố tương tự từ các giải pháp khác. Tại sao phải phát minh bánh xe? =>> Câu này giống e quá =))

## Dẫn chứng tốt và dễ hiểu

Vì `Design Patterns` các mẫu thiết kế được các nhà kiến ​​trúc sư, nhà thiết kế và phát triển phần mềm dẫn chứng tốt và dễ hiểu, thì ứng dụng của họ trong một giải pháp cụ thể cũng sẽ được hiểu rõ.

`Design Patterns` cung cấp cho nhà phát triển phần mềm một loạt các giải pháp được thử và thử nghiệm cho các vấn đề chung, do đó giảm nguy cơ kỹ thuật cho dự án bằng cách không phải sử dụng một thiết kế mới và chưa được kiểm tra..

`Design Patterns` có thể những hướng dẫn ban đầu sẽ không làm giảm thời gian phát triển, vì đây sẽ là khó khăn nếu đội của bạn không quen với chúng. Tuy nhiên, Hãy nhìn con đường phát triển theo chiều sâu, một khi đã làm quen hơn thì thời gian phát triển cũng sẽ đc giảm dần.

## Tương đối đồng bộ với kỹ thuật dân dụng.

Để đưa ra sự giống nhau của `Design Pattern` trong lĩnh vực kỹ thuật dân dụng (Như tôi đã nêu ở bài [Tại sao thiết kế là tối quan trọng đối với Phát triển Phần mềm][1]) sẽ là một giải pháp để vượt sông. Đây là một vấn đề thường xuyên đối với các kỹ sư dân dụng, trong đó có một số giải pháp được ghi nhận và hiểu rõ. Các kỹ sư dân dụng có thể xây dựng một cây cầu hoặc một đường hầm.

Tại sao một kỹ sư dân dụng cố gắng giải quyết vấn đề này từ đầu khi có những giải pháp thế giới thực có thể được đề cập đến? Có sự tương đồng gần gũi giữa kỹ sư xây dựng giải quyết vấn đề về sông và kỹ sư phần mềm giải quyết vấn đề phần mềm:

* Các giai pháp (cầu hoặc đường hầm) đều được làm rõ và ghi lại.
* Các giai pháp (cầu hoặc đường hầm) giải quyết các vấn đề dân dụng đinh kỳ
* Các giai pháp (cầu hoặc đường hầm) không phải là xác định hoặc quy định, nhưng là trừu tượng và có thể được điều chỉnh cho các vấn đề cụ thể để khởi công (cầu hoặc các vật liệu xây dựng đường hầm ví dụ có thể được lựa chọn cho sự liên kết của họ với các vấn đề cụ thể)

Có Lập luận chống lại `Design Patterns` rằng chúng không thích hợp cho mục đích thương mại do quá trình thực hiện lâu dài của chúng không giữ được. `Design Patterns` tiết kiệm thời gian (khi được xem qua suốt thời gian sử dụng) bằng cách cho nhà phát triển lựa chọn các giải pháp đã được thử và thử nghiệm sẵn có mà họ có thể tùy chỉnh theo nhu cầu cụ thể của riêng họ.

Vấn đề duy nhất mà tôi gặp `Design Patterns` là khi giành thời gian để học về nó. Một số người trong số họ có thể khó hiểu và hiểu. Đây là một lý do chính đáng, vì nó đòi hỏi một nhà phát triển có tay nghề cao hơn sử dụng chúng. Điều này sau đó có thể làm tăng chi phí dự án ban đầu. Tuy nhiên, khi xem xét trong suốt thời gian sử dụng một ứng dụng, tôi sẽ hoàn toàn mong đợi những chi phí phát triển ban đầu này sẽ được bù đắp lại do chi phí bảo trì thấp hơn do sự hiểu biết cao hơn và khả năng mở rộng dễ dàng hơn (làm cho ứng dụng dễ dàng mở rộng trong tương lai để đáp ứng những cơ hội đang nổi lên)..

`Design Patterns` giảm sự phức tạp, và do đó giải pháp trở nên dễ hiểu hơn.

`Design Patterns` là các giải pháp được thử nghiệm và thử nghiệm, nhà phát triển không cần phải bắt đầu từ đầu, và có thể bắt đầu ngay với một giải pháp đã được chứng minh là có hiệu quả (miễn là Mẫu Thiết kế được sử dụng giải quyết một vấn đề tương tự). Sẽ là sai khi mong đợi một cây cầu để giải quyết vấn đề băng qua đại dương, nơi một cây cầu chỉ đơn giản là không phù hợp.

## Lợi ích của việc sử dụng Design Paterns

`Design Patterns` cung cấp các lợi ích sau đây.

* Chúng cung cấp cho nhà phát triển một loạt các giải pháp thử và thử nghiệm để làm việc với
* Chúng là ngôn ngữ trung gian và do đó có thể được áp dụng cho bất kỳ ngôn ngữ nào hỗ trợ hướng đối tượng
* Chúng hỗ trợ truyền thông bởi thực tế là họ có tài liệu tốt và có thể được nghiên cứu nếu đó không phải là trường hợp.
* Chúng đã có một hồ sơ theo dõi đã được chứng minh vì chúng đã được sử dụng rộng rãi và do đó làm giảm nguy cơ kỹ thuật cho dự án
* Chúng rất linh hoạt và có thể được sử dụng trong bất kỳ loại ứng dụng hoặc tên miền nào

## Kết luận

`Design Patterns`, mặc dù ban đầu chúng phải đi theo đường vòng, là một sự đầu tư rất đáng giá. Họ sẽ cho phép bạn thực hiện các giải pháp được thử và thử nghiệm cho các vấn đề, do đó tiết kiệm thời gian và nỗ lực trong giai đoạn triển khai của vòng đời phát triển phần mềm. Bằng cách sử dụng các giải pháp được hiểu rõ và có tài liệu, sản phẩm cuối cùng sẽ có một mức độ hiểu biết cao hơn nhiều. Nếu giải pháp được dễ dàng hơn để hiểu, sau đó bằng cách mở rộng, nó cũng sẽ được dễ dàng hơn để duy trì.

[1]: http://www.codeproject.com/Tips/806867/Why-Design-is-Critical-to-Software-Development
[2]: http://en.wikipedia.org/wiki/Design_pattern
[3]: http://www.dofactory.com/Patterns/Patterns.aspx

## Practice
- https://coderoncode.com/design-patterns/programming/php/coding/development/2014/01/19/design-patterns-php-factories.html
- https://www.binpress.com/tutorial/the-factory-design-pattern-explained-by-example/142
- https://www.codeproject.com/Articles/852232/PHP-Singleton-Pattern-A-Step-by-Step-And-Problem-s
- http://www.fluffycat.com/PHP-Design-Patterns/

**Keyword:** `how to separate code to package php`, `step by step php design pattern singleton`(thay đổi singleton sang other để có thêm kết quả)
