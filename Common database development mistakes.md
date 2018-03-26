## Những sai lầm về phát triển dữ liệu mà các nhà phát triển phần mềm thường mắc phải?

_source https://stackoverflow.com/questions/621884/database-development-mistakes-made-by-application-developers_

**1. Không sử dụng các chỉ số thích hợp**

Đây là một điều tưởng chừng như đơn giản nhưng nó lại gặp phải mọi lúc. Khóa ngoại nên có chỉ số trên chúng.Nếu bạn đang sử dụng 1 trường trong mệnh đề 

WHERE bạn nên (có thể) có một chỉ số cho nó. các chỉ mục này thường dựa trên nhiều trường bạn cần để thực hiện truy vấn.

**2. Không thực thi toàn vẹn tham chiếu**

Cơ sở dữ liệu của bạn có thể thay đổi ngay ở đây nhưng nếu cơ sở dữ liệu của bạn hỗ trợ toàn vẹn tham chiếu--có nghĩa là tất cả khóa ngoại đều đảm bảo trỏ tới thực thể có tồn tại--bạn nên sử dụng nó.

Nó là lỗi khá phổ biến ở cớ sở dữ liệu MySQL. Tôi không tin rằng MyISAM hỗ trợ nó. InnoDB thì có. Bạn sẽ tìm thấy những người sử dụng MyISAM hoặc đang sử dụng InnoDB nhưng sẽ không sử dụng nó (nó ở đây là toàn vẹn tham chiếu) theo bất cứ cách nào.

Đọc thêm ở đây:

- [Các ràng buộc quan trngj như thế nào như NOT NULL và FOREIGN KEY nếu tôi luôn luôn kiểm soát đầu vào của cơ sở dữ liệu trong php?](https://stackoverflow.com/questions/382309/how-important-are-constraints-like-not-null-and-foreign-key-if-ill-always-contr)
- [khóa ngoại thực sự cần thiết trong thiết kế csdl?](https://stackoverflow.com/questions/18717/are-foreign-keys-really-necessary-in-a-database-design)
- [Are foreign keys really necessary in a database design?](http://www.diovo.com/2008/08/are-foreign-keys-really-necessary-in-a-database-design/)

**3. Sử dụng khóa chính 1 cách tự nhiên thay vì chỉ để đại diện ( về mặt kỹ thuật)**

Những khóa tự nhiên là những khóa dựa trên ý nghĩa bên ngoài của dữ liệu đó là (bề ngoài) độc nhất.Các ví dụ phổ biến là mã sản phẩm,2 chữa của mã tiểu bang (US), số bảo mật xã hội và vân vân. Các khóa chính thay thế hoặc kỹ thuật chính là những khoá hoàn toàn không có ý nghĩa bên ngoài hệ thống. Chúng được phát minh hoàn toàn để xác định thực thể và thường là các trường gia tăng tự động (SQL Server, MySQL, others) hoặc các chuỗi (đáng chú ý nhất là Oracle).

Theo tôi bạn nên **luôn luôn** sử dụng khóa đại diện. Vấn đề này đưa ra trong những câu hỏi dưới đây:

- [Bạn thích khóa chính của mình như thế nào?](https://stackoverflow.com/questions/404040/how-do-you-like-your-primary-keys)
- [cách thực hành tốt nhất các khóa chính trong bảng?](https://stackoverflow.com/questions/337503/whats-the-best-practice-for-primary-keys-in-tables)
- [Bạn sử dụng định dạng khóa chính nào trong trường hợp này.](https://stackoverflow.com/questions/506164/which-format-of-primary-key-would-you-use-in-this-situation)
- [Khóa đại diện với khóa tự nhiên / business](https://stackoverflow.com/questions/63090/surrogate-vs-natural-business-keys)
- [Bạn có nên có trường khóa chính riêng?](https://stackoverflow.com/questions/166750/should-i-have-a-dedicated-primary-key-field)

Đây là một chủ đề gây nhiều tranh cãi mà bạn sẽ không đạt được thỏa thuận chung. Trong khi bạn có thể tìm thấy một số người, những người nghĩ rằng các khóa tự nhiên là trong một số tình huống OK, bạn sẽ không tìm thấy bất kỳ lời chỉ trích của các khóa đại diện khác hơn là cho là không cần thiết. Đó là một nhược điểm nhỏ nếu bạn hỏi tôi.

Hãy nhớ rằng, [Các quốc gia có thể không tồn tại](http://en.wikipedia.org/wiki/ISO_3166-1) (ví dụ, Yugoslavia).

**4. Viết các truy vấn yêu cầu

DISTINCT làm việc**

Bạn thường thấy điều này trong truy vấn tạo-ORM. Để ý đầu ra log từ Hibernate và bạn sẽ nhìn thấy toàn bộ truy vấn bắt đầu với:

SELECT DISTINCT ...

Đây là một chút của một phím tắt để đảm bảo bạn không trả lại các hàng trùng lặp và do đó nhận được các đối tượng trùng lặp. Đôi khi bạn cũng thấy những người làm việc này. Nếu bạn nhìn thấy nó quá nhiều đó là một lá cờ đỏ thực sự (xuất hiện khi gặp lỗi). Không phải cái đó

DISTINCT là xấu hoặc là không có ứng dụng hợp lệ. Nó có (về cả 2 mặt) Nhưng nó không phải là 1 đại diện hoặc là 1 rào cản cho việc viết truy vấn hợp lệ.

Từ [Tại sao tôi ghét DISTINCT](http://weblogs.sqlteam.com/markc/archive/2008/11/11/60752.aspx):

> Trong trường hợp mọi thứ bắt đầu trở nên rắc rối theo ý kiến ​​của tôi là khi một nhà phát triển đang xây dựng truy vấn đáng kể, Nối các bảng với nhau, và đột nhiên anh ta nhận ra rằng có vẻ như anh ta đang nhận được bản sao (hoặc thậm chí nhiều hơn) hàng và phản ứng ngay lập tức "giải pháp" của anh ta đối với "vấn đề" này là ném vào từ khóa DISTINCT và **POOF** tất cả các rắc rối của ông biến mất..

**5. Khuyến khích tập hợp các kết nối**

Một sai lầm phổ biến khác của các nhà phát triển ứng dụng csdl là không nhận ra các tập hợp giá trị hơn (ví dụ như mệnh đề GROUP BY) có thể được so sánh với joins.

Để cung cấp cho ban một ý tưởng về sự phổ biến rộng rãi này là, Tôi đã viết chủ đề này rất nhiều lần ở đây và bị khá nhiều downvote , Ví dụ:

Từ [Câu lệnh SQL - “join” vs “group by và having”](https://stackoverflow.com/questions/477006/sql-statement-join-vs-group-by-and-having/477013#477013):

> Truy vấn đầu tiên:

SELECT userid
FROM userrole
WHERE roleid IN (1, 2, 3)
GROUP by userid
HAVING COUNT(1) = 3

> Query time: 0.312 s

> Truy vấn thứ 2:

SELECT t1.userid
FROM userrole t1
JOIN userrole t2 ON t1.userid = t2.userid AND t2.roleid = 2
JOIN userrole t3 ON t2.userid = t3.userid AND t3.roleid = 3
AND t1.roleid = 1

> Query time: 0.016 s

> Nó là đúng. Phiên bản join do tôi đề xuất **nhanh hơn gấp 20 lần phiên bản tổng hợp.**

**6. Không đơn giản hóa các truy vấn phức tạp thông qua các chế độ views**

Không phải tất cả các nhà cung cấp cơ sở dữ liệu hỗ trợ quan điểm nhưng đối với những người làm, họ có thể đơn giản hóa các truy vấn nếu được sử dụng một cách thận trọng. Ví dụ, trong một dự án tôi đã sử dụng một [mô hình chung của Party](http://www.tdan.com/view-articles/5014/) đối với CRM. Đây là một kỹ thuật mô hình rất mạnh và linh hoạt nhưng có thể dẫn đến nhiều người tham gia. Trong mô hình này có:

- **Party**: mọi người và tổ chức;
- **Party Role**: những điều mà các bên đã làm, ví dụ Nhân viên và Nhà tuyển dụng;
- **Party Role Relationship**: làm thế nào để những vai trò liên qua đến nhau.

Ví dụ:

- Ted là 1 con người, là 1 phần tử của bữa tiệc;
- Ted có nhiều vai trò, một trong số đó là nhân viên;
- Intel là một tổ chức, là 1 phần tử của bữa tiệc;
- Intel có nhiều vai trò, một trong số đó là nhà tuyển dụng;
- Intel thuê Ted, có nghĩa là có một mối quan hệ tương ứng giữa họ;

Vì vậy, có năm bảng tham gia để liên kết Ted với chủ của mình. Bạn giả định tất cả nhân viên là Người (không phải tổ chức) và cung cấp khung nhìn trợ giúp này:

CREATE VIEW vw_employee AS
SELECT p.title, p.given_names, p.surname, p.date_of_birth, p2.party_name employer_name
FROM person p
JOIN party py ON py.id = p.id
JOIN party_role child ON p.id = child.party_id
JOIN party_role_relationship prr ON child.id = prr.child_id AND prr.type = 'EMPLOYMENT'
JOIN party_role parent ON parent.id = prr.parent_id = parent.id
JOIN party p2 ON parent.party_id = p2.id

và đột nhiên bạn có một cái nhìn đơn giản về dữ liệu mà bạn muốn trên một mô hình có tính linh hoạt cao.

**7. Không chắt lọc đầu vào**

Đây là một lỗi lớn.  Bây giờ tôi thích PHP nhưng nếu bạn không biết bạn đang làm gì thì thật dễ dàng để tạo các trang web dễ bị tấn công. Không có gì tổng kết nó tốt hơn so với [cầu truyện về cái bàn Bobby bé nhỏ](http://xkcd.com/327/).

Dữ liệu được cung cấp bởi người dùng thông qua URLs, form dữ liệu **và cookies** nên luôn luôn được coi là thù địch và khử trùng. Đảm bảo bạn đang nhận được những gì bạn mong đợi.

**8. Không sử dụng câu lệnh đã được chuẩn bị sẵn**

Các câu lệnh đã được chuẩn bị là khi bạn biên dịch truy vấn trừ dữ liệu được sử dụng trong inserts , updates và

mệnh đề WHERE và sau đó cung cấp chúng muộn. Ví dụ như:

SELECT * FROM users WHERE username = 'bob'

vs

SELECT * FROM users WHERE username = ?

hoặc

SELECT * FROM users WHERE username = :username

tùy thuộc vào nền tảng của bạn.

Tôi đã nhìn thấy cơ sở dữ liệu bị sụp xuống bằng cách làm điều này. Về cơ bản, mỗi khi cơ sở dữ liệu hiện đại gặp một truy vấn mới, nó phải biên dịch nó. Nếu nó gặp một truy vấn nó được nhìn thấy trước, bạn đang cho cơ sở dữ liệu cơ hội để cache truy vấn biên dịch và kế hoạch thực hiện. Bằng cách thực hiện các truy vấn rất nhiều bạn đang cho cơ sở dữ liệu cơ hội để con số đó ra và tối ưu hóa cho phù hợp (ví dụ, bằng cách ghim các truy vấn biên dịch trong bộ nhớ).

Sử dụng các câu lệnh chuẩn bị cũng sẽ cung cấp cho bạn số liệu thống kê có ý nghĩa về tần suất các truy vấn nhất định được sử dụng.

Các câu lệnh được chuẩn bị cũng sẽ giúp bạn chống lại các cuộc tấn công SQL injection tốt hơn.

**9. Not normalizing enough**

[Database normalization](http://en.wikipedia.org/wiki/Database_normalization) is basically the process of optimizing database design or how you organize your data into tables.

Just this week I ran across some code where someone had imploded an array and inserted it into a single field in a database. Normalizing that would be to treat element of that array as a separate row in a child table (ie a one-to-many relationship).

This also came up in [Best method for storing a list of user IDs](https://stackoverflow.com/questions/620645/best-method-for-storing-a-list-of-user-ids):

> I've seen in other systems that the list is stored in a serialized PHP array.

But lack of normalization comes in many forms.

More:

- [Normalization: How far is far enough?](http://www.techrepublic.com/article/normalization-how-far-is-far-enough/)
- [SQL by Design: Why You Need Database Normalization ](http://www.sqlmag.com/Article/ArticleID/4887/sql_server_4887.html)

**10. Normalizing too much**

This may seem like a contradiction to the previous point but normalization, like many things, is a tool. It is a means to an end and not an end in and of itself. I think many developers forget this and start treating a "means" as an "end". Unit testing is a prime example of this.

I once worked on a system that had a huge hierarchy for clients that went something like:

Licensee -&gt;  Dealer Group -&gt; Company -&gt; Practice -&gt; ...

such that you had to join about 11 tables together before you could get any meaningful data. It was a good example of normalization taken too far.

More to the point, careful and considered denormalization can have huge performance benefits but you have to be really careful when doing this.

More:

- [Why too much Database Normalization can be a Bad Thing](http://www.selikoff.net/blog/2008/11/19/why-too-much-database-normalization-can-be-a-bad-thing/)
- [How far to take normalization in database design?](https://stackoverflow.com/questions/496508/how-far-to-take-normalization-in-database-design)
- [When Not to Normalize your SQL Database](http://www.25hoursaday.com/weblog/CommentView.aspx?guid=cc0e740c-a828-4b9d-b244-4ee96e2fad4b)
- [Maybe Normalizing Isn't Normal](http://www.codinghorror.com/blog/archives/001152.html)
- [The Mother of All Database Normalization Debates on Coding Horror](http://highscalability.com/mother-all-database-normalization-debates-coding-horror)

**11. Using exclusive arcs**

An exclusive arc is a common mistake where a table is created with two or more foreign keys where one and only one of them can be non-null.  **Big mistake.** For one thing it becomes that much harder to maintain data integrity. After all, even with referential integrity, nothing is preventing two or more of these foreign keys from being set (complex check constraints notwithstanding).

From [A Practical Guide to Relational Database Design](http://books.google.com.au/books?id=7ZAk0YiKQV0C&pg=PA110&lpg=PA110&dq=%22exclusive+arc%22+database&source=bl&ots=AyNPWsac__&sig=gBFIerXckQlVpRdd6ycI5JEgq3U&hl=en&ei=PzGzSZfrFcPVkAWWyZDZBA&sa=X&oi=book_result&resnum=1&ct=result):

> We have strongly advised against exclusive arc construction wherever possible, for the good reason that they can be awkward to write code and pose more maintenance difficulties.

**12. Not doing performance analysis on queries at all**

Pragmatism reigns supreme, particularly in the database world. If you're sticking to principles to the point that they've become a dogma then you've quite probably made mistakes. Take the example of the aggregate queries from above. The aggregate version might look "nice" but its performance is woeful. A performance comparison should've ended the debate (but it didn't) but more to the point: spouting such ill-informed views in the first place is ignorant, even dangerous.

**13. Over-reliance on UNION ALL and particularly UNION constructs**

A UNION in SQL terms merely concatenates congruent data sets, meaning they have the same type and number of columns. The difference between them is that UNION ALL is a simple concatenation and should be preferred wherever possible whereas a UNION will implicitly do a DISTINCT to remove duplicate tuples.

UNIONs, like DISTINCT, have their place. There are valid applications. But if you find yourself doing a lot of them, particularly in subqueries, then you're probably doing something wrong. That might be a case of poor query construction or a poorly designed data model forcing you to do such things.

UNIONs, particularly when used in joins or dependent subqueries, can cripple a database. Try to avoid them whenever possible.

**14. Using OR conditions in queries**

This might seem harmless. After all, ANDs are OK. OR should be OK too right? Wrong. Basically an AND condition **restricts** the data set whereas an OR condition **grows** it but not in a way that lends itself to optimisation. Particularly when the different OR conditions might intersect thus forcing the optimizer to effectively to a DISTINCT operation on the result.

Bad:

... WHERE a = 2 OR a = 5 OR a = 11

Better:

... WHERE a IN (2, 5, 11)

Now your SQL optimizer may effectively turn the first query into the second. But it might not. Just don't do it.

**15. Not designing their data model to lend itself to high-performing solutions**

This is a hard point to quantify. It is typically observed by its effect. If you find yourself writing gnarly queries for relatively simple tasks or that queries for finding out relatively straightforward information are not efficient, then you probably have a poor data model.

In some ways this point summarizes all the earlier ones but it's more of a cautionary tale that doing things like query optimisation is often done first when it should be done second. First and foremost you should ensure you have a good data model before trying to optimize the performance. As Knuth said:

> Premature optimization is the root of all evil

**16. Incorrect use of Database Transactions**

All data changes for a specific process should be atomic. I.e. If the operation succeeds, it does so fully. If it fails, the data is left unchanged. - There should be no possibility of 'half-done' changes.

Ideally, the simplest way to achieve this is that the entire system design should strive to support all data changes through single INSERT/UPDATE/DELETE statements. In this case, no special transaction handling is needed, as your database engine should do so automatically.

However, if any processes do require multiple statements be performed as a unit to keep the data in a consistent state, then appropriate Transaction Control is necessary.

- Begin a Transaction before the first statement.
- Commit the Transaction after the last statement.
- On any error, Rollback the Transaction. And very NB! Don't forget to skip/abort all statements that follow after the error.

Also recommended to pay careful attention to the subtelties of how your database connectivity layer, and database engine interact in this regard. 

**17. Not understanding the 'set-based' paradigm**

The SQL language follows a specific paradigm suited to specific kinds of problems. Various vendor-specific extensions notwithstanding, the language struggles to deal with problems that are trivial in langues like Java, C#, Delphi etc.

This lack of understanding manifests itself in a few ways.

- Inappropriately imposing too much procedural or imperative logic on the databse.
- Inappropriate or excessive use of cursors. Especially when a single query would suffice.
- Incorrectly assuming that triggers fire once per row affected in multi-row updates.

Determine clear division of responsibility, and strive to use the appropriate tool to solve each problem.