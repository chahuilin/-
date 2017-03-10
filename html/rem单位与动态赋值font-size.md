    <!DOCTYPE html>
    <html>

        <head>
            <meta charset="UTF-8">
            <title></title>
            <script src="http://apps.bdimg.com/libs/jquery/1.8.0/jquery.min.js"></script>
            <script type="text/javascript">
                var a = function() {
                    var w = $(document.body).width();
                    console.log($(document.body).width())
                    var size = 20 * w / 1600;
                    $("html").css("font-size", size);
                };
                $(document).ready(a)

                $(window).resize(a);
            </script>
        </head>

        <body style="margin: 0;">
            <div style="width: 60rem;padding: 10rem;background-color: #FF0000;">
                <span style="font-size: 2rem;">查帅嘻嘻嘻嘻嘻嘻嘻嘻</span>
                11
            </div>
        </body>

    </html>