# ITCSS: ~~Phát triển~~ _Mở rộng_(SCALABLE) và bảo trì kiến trúc CSS

Làm thế nào để phát triển và bảo trì CSS của mình? Nó thực sự quan trọng với từng người làm Front-end. ITCSS là câu trả lời.

Năm trước, khi chúng tôi bắt đầu lên kế hoạch thiết kế [HEROized][1] và Xfive.co một website mới, Tôi đã tìm kiếm một kiến trúc CSS mà nó cho phép dễ dàng phát triển trang web và hơn nữa là bảo trì.

[CSS Modules](http://www.sitepoint.com/understanding-css-modules-methodology/) còn khá trẻ và mới lạ tại thời điểm đó và tôi luôn luôn xem xét [Atomic Design][3] tương tự vs người làm ra nó. Rồi tôi bắt gặp [Harry Roberts's][4] ITCSS vào tháng 6 năm 2015 trên [net magazine][5] và ngay lập tức đã yêu thích cách tiếp cận đơn giản như thế này.

## ITCSS là gì?

ITCSS viết tắt của _Inverted Triangle CSS_ và nó giúp bạn quản lý project các CSS files của bạn theo cách giải quyết tốt hơn **deal with** (không phải luôn luôn dễ dàng) cụ thể như **global namespace, cascade and selectors specificity**.

ITCSS có thể được sử dụng với các tiền xử lý hoặc không có nó và tương thích với CSS methodologies như BEM, SMACSS or OOCSS.

Một trong những nguyên tắc chính của ITCSS là nó tách css CSS codebase thành các phần riêng (gọi là _layers_), có dạng hình tam giác ngược:

![ITCSS Layers][https://www.xfivecdn.com/xfive/wp-content/uploads/2016/02/01083650/itcss-layers2.svg]

Các layers này như sau:

* **Settings** – được sử dụng với các tiền xử lý và có chứa fonts, định nghĩa màu sắc...
* **Tools** – các mixin và các chức năng hỗ trợ. Điều quan trọng là không đưa CSS nào vào trong 2 lớp đầu tiên.
* **Generic** – lưu 1 số file như reset.css, normalize.css. Đây là layer đầu tiên khi tạo CSS
* **Elements** – các thành phần cơ bản của HTML (như h1,a,...). Các thành phần này sử dụng style mặc định của browser,vì vậy chúng ta có thể sửa chúng tại đây
* **Objects** – các đối tượng được tái sử dụng và cần xây dựng theo OOCSS.
* **Components**– Ui cho giao diện, với mỗi mục đích cụ thể, không có giới hạn nào cho việc xây dựng các component.
* **Utilities**– Utilities và các helper class với khả năng ghi đè bất cứ thứ gì ở mũi của tam giác, ví dụ các helper class ẩn

Hình tam giác cũng cho thấy các kiểu được biểu diễn bởi các selectors được đặt hàng trong kết quả CSS: từ cái chung đến cái riêng, từ các selectors nhỏ đến cụ thể hơn (nhưng vẫn _không quá_ cụ thể, IDs không cho phép) và từ xa đến gần.

![](https://www.xfivecdn.com/xfive/wp-content/uploads/2016/02/10154630/itcss-key-metrics.svg)

![ITCSS Key Metrics][7]

Tổ chức CSS như vậy sẽ giúp bạn tránh được Specificity Wars và được viết bởi [a healthy specificity graph][8].

## Tài liệu

_Cập nhật 10/27/2016: Net magazine vừa tái xuất bản bài báo gốc từ phiên bản in (xem bên dưới)._

Thông thường, vào thời điểm này, tôi sẽ giới thiệu bạn đến [ITCSS webpage][http://itcss.io/] để nghiên cứu thêm. Tuy nhiên, không có gì giống như tài liệu open source đã tồn tại.

ITCSS vẫn dành riêng một phần và nếu bạn muốn tận dụng nó, bạn nên nghiên cứu bản giới thiệu ban đầu trong net magazine. Tôi không ở đây để đánh giá ý tưởng của tác giả (Tôi rất biết ơn anh ấy vì anh ấy đã chia sẻ kiến ​​thức ),Tôi nghĩ rằng điều này cản ITCSS mở rộng hơn (có thể là ý tưởng, sau tất cả).

> Tính độc quyền một phần của ITCSS ngăn cản việc áp dụng rộng rãi hơn.

Điều này không ngăn cản bạn bắt đầu sử dụng nó trong dự án của bạn, tuy nhiên, nếu bạn thực sự quan tâm đến nó. [Get that particular issue][https://www.myfavouritemagazines.co.uk/design/net-magazine-back-issues/] của net magazine để học ITCSS nguyên tắc cơ bản, và sau đó nghiên cứu tài nguyên trực tuyến hiện có và ví dụ để giúp bạn với việc áp dụng nó trong các dự án thực tế.

## Tài nguyên

Tôi đã sử dụng ITCSS trong 4 project và cả những cái sau này nữa (bao gồm cả Xfive.co). Dưới đây là các nguồn tài liệu giúp tôi hiểu rõ hơn về ITCSS:

- [Manage large CSS projects with ITCSS](http://www.creativebloq.com/web-design/manage-large-css-projects-itcss-101517528) – ITCSS giới thiệu bởi Harry Roberts (bài viết ban đầu đã được xuất bản trên báo giấy, thiếu các cột shorters trong đồ thị đặc tính và tiền chỉ thị)
- [Manage large-scale web projects with new CSS architecture ITCSS](http://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731) –  giới thiệu về ITCSS và phỏng vấn Harry Roberts
- [Harry Roberts – Managing CSS Projects with ITCSS](https://www.youtube.com/watch?v=1OKZOV-iLj4) – cuộc nói chuyện của Harray tạ DaFED và slide đi kèm. 
- [Manage large CSS projects with ITCSS](https://www.youtube.com/watch?v=hz76JIU_xB0) – hình chụp trên bài viết trên mạng.
- [ITCSS Screencast code](https://github.com/itcss/itcss-netmag) – code của những screencast bên trên trên GitHub.
- [Another ITCSS project example](https://github.com/csswizardry/frcss)
- Các bài viết trên csswizardry.com liệt kê dưới đây:
    - [BEMIT: Taking the BEM Naming Convention a Step Further](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
    - [More Transparent UI Code with Namespaces](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
    - [Immutable CSS](https://csswizardry.com/2015/03/immutable-css/)
    - [The Specificity Graph](https://csswizardry.com/2014/10/the-specificity-graph/)
- [inuitcss](https://github.com/inuitcss/inuitcss) – Framework 00CSS xây dụng dựa vào ITCSS và nó đưa ra nhiều khái niệm và các tính năng nâng cao hơn.
- [The BEMIT naming convention](http://www.jamesturneronline.net/blog/bemit-naming-convention.html)

Bạn có thể theo dõi[Chisel](https://github.com/xfiveco/generator-chisel/), nhà sáng lập ra Yeoman cho các dự án front-end của WordPress, nó có hỗ trợ ITCSS.

## Kinh nghiệm

Dưới đây là một vài ý kiến dựa trên kinh nghiệm của tôi qua các dự án ITCSS:

### ~~Gợi ý cách~~ _Nghĩ ít đi về_ đặt tên và vị trí của các styles

Tính chất bắt buộc của ITCSS đặc biệt khi kết hợp với [BEMIT naming convention](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/) cho phép bạn tập trung nhiều hơn vào giải quyết các front-end challenges thay vì suy nghĩ về tên và vị trí của style. Đây là những gì Xfive.co main.scss cung cấp cho bạn:
    
    
    @import "settings.colors";
    @import "settings.global";
    
    @import "tools.mixins";
    
    @import "normalize-scss/normalize.scss";
    @import "generic.reset";
    @import "generic.box-sizing";
    @import "generic.shared";
    
    @import "elements.headings";
    @import "elements.hr";
    @import "elements.forms";
    @import "elements.links";
    @import "elements.lists";
    @import "elements.page";
    @import "elements.quotes";
    @import "elements.tables";
    
    @import "objects.animations";
    @import "objects.drawer";
    @import "objects.list-bare";
    @import "objects.media";
    @import "objects.layout";
    @import "objects.overlays";
    
    @import "components.404";
    @import "components.about";
    @import "components.archive";
    @import "components.avatars";
    @import "components.blog-post";
    @import "components.buttons";
    @import "components.callout";
    @import "components.clients";
    @import "components.comments";
    @import "components.contact";
    @import "components.cta";
    @import "components.faq";
    @import "components.features";
    @import "components.footer";
    @import "components.forms";
    @import "components.header";
    @import "components.headings";
    @import "components.hero";
    @import "components.jobs";
    @import "components.legal-nav";
    @import "components.main-cta";
    @import "components.main-nav";
    @import "components.newsletter";
    @import "components.page-title";
    @import "components.pagination";
    @import "components.post-teaser";
    @import "components.process";
    @import "components.quote-banner";
    @import "components.offices";
    @import "components.sec-nav";
    @import "components.services";
    @import "components.share-buttons";
    @import "components.social-media";
    @import "components.team";
    @import "components.testimonials";
    @import "components.topbar";
    @import "components.reasons";
    @import "components.wordpress";
    @import "components.work-list";
    @import "components.work-detail";
    
    @import "vendor.prism";
    
    @import "trumps.clearfix";
    @import "trumps.utilities";
    
    @import "healthcheck";

_Lưu ý: Chúng ta sử dụng [separate folders for each layer][https://github.com/xfiveco/generator-chisel/tree/master/generators/app/templates/styles/itcss] và tải các bảng định kiểu mới được thêm tự động vào [Chisel][https://github.com/xfiveco/generator-chisel/]._

### ~~Các Object có thể phát triển và sử dụng lại~~ _Các object được sử dụng lại cho quá trình phát triển nhanh_

Các object của ITCSS là đối tượng hoàn hảo để xây dựng thư viện chứa các component có thể tái sử dụng cho phép xây dụng front-end nhanh chóng.
Các thành phần UI khi đó sẽ bao gồm các object dùng chung và các componet cụ thể trong project. Ví dụ, (innuitcss) như là một frameworm dựa trên ITCSS, nó bao gồm [a bunch of objects](https://github.com/inuitcss/inuitcss/tree/develop/objects) nhưng chỉ là [one sample component](https://github.com/inuitcss/inuitcss/tree/develop/components)

### Hoạt ảnh

Tôi khuyên bạn nên định nghĩa chung, global animations như các đối tượng quá ,ví dụ _@keyframes_ _o-fade-in_ trong file __objects.animations.scss_

Các Component animations nên được định nghĩa cụ thể, ví dụ _@keyframes c-hero-scale_ trong __components.hero.scss._

### Linh động

ITCSS khá là linh hoạt trong các công cụ và workflow của bạn. Một developers của chúng tôi đã từng thắc mắc có bao nhiêu bản mẫu đi kèm với ITCSS. Nhưng thực tế điều này hoàn toàn tùy thuộc vào bạn, ITCSS không bắt buộc bạn phải có tất cả các thể hiện của layer(chỉ là cần đúng thứ tự).

Vì thể trong một thiết lập tối thiểu, bạn có thể chỉ có các component được gán style mặc định bởi browser. Tất nhiên, như thể không có tính thực tế - một vài thiết lập, reset và/hoặc CSS thông thường được hầu hết mọi người sử dụng vì những lý do tốt.

### Phê bình CSS

ITCSS làm tốt với CSS là nhờ tam giác ngược. Component dựa trên model cho phép bạn tách UI trên giao diện người dùng thành các thành phần logic nên bạn thậm chí có thể lấy các phần của CSS quan trọng bằng tay (chi tiết trong bài viết sắp tới).

### Việc lặp lại style và kích thước của file

Nếu có bất kỳ mối quan tâm với một kiến ​​trúc như ITCSS hoặc về bất kỳ thành phần cơ bản nào như kiến ​​trúc CSS, nó có thể là kích thước tập tin

ITCSS không thể cạnh tranh với [CSS chức năng](https://blog.colepeters.com/building-and-shipping-functional-css/) theo nghĩa này. Hay nói cách khác, nếu bạn thấy mình lặp lại rất nhiều style trong các component, bạn có thể cân nhắc chuyển các style này sang các đối tượng riêng biệt.

### Kết luận

Bạn không thể làm sai với ITCSS. Đó là sự đúc kết của kinh nghiệm và nhiều năm làm việc của Harry Roberts, một trong những tác giả CSS nổi tiếng nhất. Nếu bạn không ngại tìm hiểu sâu vào các resource, bạn sẽ có một kiến ​​trúc đơn giản nhưng mạnh mẽ sẽ cho phép bạn tạo CSS có thể mở rộng và duy trì được cho các dự án nhỏ hoặc lớn của bạn.

Nhưng đùng quên theo dõi các yếu tố khác như [CSS modules](https://github.com/css-modules/css-modules)
But don’t forget to keep an eye on other players like[CSS modules](https://github.com/css-modules/css-modules), in the meantime.

