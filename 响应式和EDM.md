# 收集整理我所实践过的EDM（邮件营销）
## http://templates.mailchimp.com/  可以在此站下载一些常用的模板，都是以table布局
##格式编码：
1. 页面宽度请设定在600 到800px（像素）以内，长度1024px以内。
2. Html 编码请使用utf-8。
3. HTML 代码在15kb 以内。（各个邮箱的收件标准不一样，如果超出15kb 您的邮件很有可能会进入垃圾邮件箱）。
4. 请使用table 表格来布局。同一个<td>里只放一张图片，如<td><imgsrc=" photo.JPG" ></td>。所有的图片都要定义高和宽。同一段文字放在同一<td>里。
5. 如果需要邮件居中显示，请在table 里设定align="center"。
6. 不可将word 类文件直接转换为html 格式，否则会造成编码不规范。
7. 不要使用外链的css 样式定义文字和图片（外链的css 样式在邮件里将不能被读取，所以发送出去的邮件因为没有链接
到样式，将会使你的邮件内容样式丢失），正确的写法：<td style="font-family:Arial, Helvetica, sans-serif;font-size:12px;
color:#000000;" >文字</td>"<fontstyle="font-family:Arial, Helvetica, sans-serif; font-size:12px;color:#000000;" >文字
</font>。
8. 不能使用Flash、Java、Javascript、frames、i-frames、ActiveX以及 DHTML，如果页面中的图片一定要是动态的，请
将FLASH 文件转换成GIF 动画使用，但在Outlook 2007 里，GIF 将不能正常显示，因为Outlook 2007 限制GIF 动画。
9. 不要使用<table></table>以外的body、meta 和html 之类的标签，部分邮箱系统会把这些过滤掉。
10. 背景图片代码写法如下：<table background="background.gif" cellspacing="0"cellpadding="0">，但请注意，outlook 对
背景图片不识别。
11.不能使用"onMouseOut" "onMouseOver"事件，即使在<td>里设置了，发送到邮箱后也将被过滤，将不能显示设定鼠标经过所
显示的内容。
12. 不能使用alt，里面的注释文字会被过滤。
13. font-family属性不能为空，否则会被QQ 屏蔽为垃圾邮件。
##文字：
1. 邮件主题控制在18 个字以内，避免使用――！……等符号，容易产生乱码。
2. 邮件主题不要加入带有网站地址的信息，比如“focussend.com祝您新年好”。 如果客户的品牌知名度比较高，主题上可
加入一下公司的名称，比如：“NIKE 运动时尚。
3. 文字内容、版面尽量简洁，突出主题，以达到更高的点击率。
4. 不使用类似如下敏感及带促销类的文字：免费、优惠、特惠、特价、低价、便宜、廉价、视频、赚钱、群发、发财、致
富、代开、薪水、交友、支付、商机、法宝、宝典、秘密、情报、机密、保密、绝密、神秘、秘诀等。如果一定需要，
请把敏感字制做成图片。
5. 如果发送超过20 万封，主题内容要更换，发送超过200 万封，要考虑重新设计。

##图片：
1. 尽量使用图片，以避免文字在各个主流邮箱中的显示有所不同。例如qq 邮箱，如果未在代码中设置，邮件中的文字不能
自动换行，gmail 邮箱邮件内容的字体会自动放大，与原来设定的字符大小不一致。
2. 整页图片控制在8 张以内，每张图片最大不能超过15kb。
3. 图片地址请不要写成本地路径，例如：<imgsrc="image/menu-5.gif" alt="" />，（这样发送出去的邮件，收件人将没办法
看到您的图片）。正确的写法应该是：<img src="http://放置图片的网络空间绝对地址/menu-5.gif"alt="" />。
4. 图片名称不能含有ad 字符，否则图片上传后会显示成“被过滤广告”。
5. 如果整个邮件模板只有一张图，一定要裁成2-3 张小图。
##链接：
1. 链接数量不能超过10 个，如果所有图片的链接地址一样，请将所有的小图合并成一张大图。
2. 链接请写成绝对地址，例如：<a href="http://www.baidu.com">文字或图片</a>。（以确保收信人在点击链接时能
够正常浏览您的内容）。
3. 链接地址的长度不能超过255 个字符，会导致无法追踪或链接错误。
4. 不要使用地图功能（map）链接图片，此功能会使邮件被多数邮箱划分为垃圾邮件！
5. 为避免用户收到的邮件图片无法浏览，请制作一份和邮件内容一样的web 页面，然后在邮件顶部写一句话：“如果您无法
查看邮件内容，请点击这里”， 链接到放有同样内容的web 页面。

##响应式：
1.使用media query根据设备宽度调整图片在不同设备的显示大小
    <style type="text/css">
        .standardImage{
            width:100%;
        }

        @media only screen and (max-width:480px){
            .standardImage{
                max-width:480px; !important;  //由于大多使用内联，所以用important后缀
            }
        }
    </style>

2.使用media query根据设备宽度调整左右布局的文字块在小设备中变为上下布局。
    <table border="0" cellpadding="0" cellspacing="0" width="600" id="templateContainer">
        <tr>
            <td align="left" valign="top">
                <table align="right" border="0" cellpadding="10" cellspacing="0" width="400" class="templateBody">
                    <tr>
                        <td class="bodyContent">
                            <img src="http://placekitten.com/g/480/300" style="max-width:380px;" class="bodyImage" />
                        </td>
                    </tr>
                    <tr>
                        <td valign="top" class="bodyContent">
                            <h1>Body</h1>
                            Lorem ipsum dolor sit amet.
                        </td>
                    </tr>
                </table>
                <table align="left" border="0" cellpadding="10" cellspacing="0" width="200" class="templateSidebar">
                    <tr>
                        <td valign="top" class="sidebarContent">
                            <h2>Sidebar</h2>
                            Lorem ipsum dolor sit amet.
                        </td>
                    </tr>
                </table>
            </td>
        </tr>
    </table>

    <style type="text/css">
        @media only screen and (max-width: 480px){
            #templateSidebar,
            #templateBody{
                display:block !important;
                width:100% !important;
            }

            .sidebarContent{
                font-size:16px !important;
                line-height:125% !important;
            }

            .bodyImage{
                height:auto !important;
                max-width:480px !important;
                width:100% !important;
            }

            .bodyContent{
                font-size:18px !important;
                line-height:125% !important;
            }
        }
    </style>

2.使用media query根据设备宽度调整链接在小设备中变为大块按钮。
    <table border="0" cellpadding="0" cellspacing="0" width="100%" id="emailFooter">
        <tr>
            <td align="center" valign="top" class="footerContent" style="padding-bottom:15px;">
                &copy; 2013 EmailCo, All Rights Reserved.
                <br />
                123 Atlantic Ave. &bull; Atlanta, GA 30318 USA
            </td>
        </tr>
        <tr>
            <td align="center" valign="top">
                <table border="0" cellpadding="5" cellspacing="0" id="utilityLink">
                    <tr>
                        <td valign="top" class="utilityLinkContent">
                            <a href="..." target="_blank">View in Browser</a>
                        </td>
                        <td valign="top" class="utilityLinkContent">
                            <a href="..." target="_blank">Terms of Use</a>
                        </td>
                        <td valign="top" class="utilityLinkContent">
                            <a href="..." target="_blank">Privacy Policy</a>
                        </td>
                        <td valign="top" class="utilityLinkContent">
                            <a href="..." target="_blank">Unsubscribe</a>
                        </td>
                    </tr>
                </table>
            </td>
        </tr>
    </table>


    <style type="text/css">
        .footerContent, .utilityLinkContent{
            color:#606060;
            font-family:Helvetica, Arial, sans-serif;
            font-size:13px;
            line-height:125%;
        }

        .footerContent a, .utilityLinkContent a{
            color:#6DC6DD;
        }

        @media only screen and (max-width: 480px){
            #utilityLink{
                max-width:600px !important;
                width:100% !important;
            }

        .utilityLinkContent{
                background-color:#E1E1E1 !important;
                border-bottom:10px solid #FFFFFF;
                display:block !important;
                font-size:15px !important;
                padding:15px 0 !important;
                text-align:center !important;
                width:100% !important;
            }

            .utilityLinkContent a{
                color:#606060 !important;
                display:block !important;
                text-decoration:none !important;
            }
        }
    </style>