/**
 * @description:
 * @author: l_man(2017/10/30 9:35)
 * @update: l_man (2017/10/30 9:35)
 */
var driverLu = {
    commonUrl:'',
    init: function () {
        var that = this;
        FastClick.attach(document.body);
        that.setWindow();
        that.resize();
        that.resSelect();
        that.forgrtUserStyles();
        that.share();
        that.modeSwitch();
        that.award_check();
        that.billSwiper();
        that.achieveQuery();

        that.garyTime(16)
        try{
            that.datePicker('#now_time');
            that.datePicker('#future_time');
        }catch(e){}
    },
    //设置窗口宽高
    setWindow: function () {
        var winH = $(window).height(),
            winW = $(window).width();
        $("body").height(winH).width(winW);
    },
    //重置窗口高度
    resize: function () {
        var that = this;
        $(window).on("resize", function () {
            that.setWindow();
        });
    },
    //启动屏倒计时
    countDown: function (n) {
        var that = this;
        time5(n);
        var i = null;
        function time5(n) {
            if (n == 0) {
               if(localStorage.getItem('driverId')==null){
               		window.location.href='index.html'
               }else{
               		window.location.href='web/index.html'
               }
                clearInterval(i);
            } else {
                n--;
                i = setTimeout(function () {
                    time5(n);
                }, 1000);
            }
        };
    },
    //注册弹窗 //退出登录 //车型选择
    resSelect:function(){
    	var cover = $('.sel_cover'),
    		layer = $('.sel_layer'),
            outLayer= $('.login_layer');
        //注册
    	$(document).on('click','.js_sel,.js_login_out',function(){
    		cover.show();
            layer.show();
    	}).on('click','.res_layer .fr,.login_layer .fl',function(){
    		cover.hide();
            layer.hide();
    	}).on('click','.list_con li.file_info.cx a',function(){
           $('.sex_cover,.sex_layer').show();
        }).on('click',':radio',function(){
            var sex = $(this).parent().find('label').html();
            $('.sex_cover,.sex_layer').hide();
            $('.list_con li.file_info.cx a span').html(sex);
        });


        $(":radio").click(function(){


        });

    },
    //忘记密码样式
    forgrtUserStyles:function(){
        $('#js_password,#js_username,#js_card').bind('propertychange input', function () {
            var count = $('#js_password').val().length,
                count1 =  $('#js_username').val().length,
                count2 =  $('#js_card').val().length,
                code = $('#js_code'),
                reset = $('#js_reset');
            (count > 0)?code.removeClass('disabled'):code.addClass('disabled');
            (count > 0 && count1 > 0 && count2 > 0)?reset.removeClass('disabled'):reset.addClass('disabled');
        });
    },
    //设置模式
    modeSwitch:function(){
        var line = $('.mode_line');
        $(document).on('click','.mode_switch a',function(){
            $(this).addClass('active').siblings().removeClass('active');
            if($(this).html()== '全部'){
                $('.con1 p').addClass('active');
            }else if($(this).html()== '预约'){
                $('.con_time').addClass('active').siblings().removeClass('active');
            }else if($(this).html()== '实时'){
                $('.con_place').addClass('active').siblings().removeClass('active');
            }
        });
        //模式切换
        $(document).on('click','.index_btn .now',function(){
            $(this).parent().parent().addClass('mode_check_c');
            $(this).html('<span>听单中</span>');
            $('.sc').css('display','block');


        }).on('click','.index_btn .btn a.sc',function(){
            $(this).parent().parent().removeClass('mode_check_c');
            $('.now').html('点击出车');
            $(this).css('display','none');
        })
    },
    //奖励活动切换
    award_check:function(){
        var no_his = $('.no_his');
        $(document).on('click','.award_tabT a',function(){
           $(this).addClass('active').siblings().removeClass('active');
            var index = $(this).index();
            $(".tabC:eq("+index+")").addClass("active").siblings().removeClass("active");
            index ==1 ? no_his.css('display','block') : no_his.css('display','none');
        });
    },
    //分享页面
    share:function(){
        //分享弹窗
        var cover = $('.share_cover'),
            layer = $('.share_layer');
        $(document).on('click','.js_share',function(){
            cover.show();
            layer.stop().show();
        }).on('click','.share_cover',function(){
            layer.stop().hide();
            cover.hide();
        });
    },
    //钱包查询
    billSwiper:function(){
        
        $(document).on('click','.bill_query .tit a',function(){
            $(this).addClass('active').siblings().removeClass('active');
        });
    },
    //成绩查询
    achieveQuery:function(){
        new Swiper ('.achieve_query', {
            nextButton: '.swiper-button-next',
            prevButton: '.swiper-button-prev'
        });
    },
    //日期选择控件
    datePicker:function(id){
        var that = this,
            themeName = null,
            startDate = that.getDateStr(0).split('-'),
            endDate = that.getDateStr(6).split('-');
        if(that.isSystem() == 'android'){
            themeName = 'android-ics light';
        }else if(that.isSystem() == 'ios'){
            themeName = 'ios';
        }
        var opt={};
        opt.date = {preset : 'date'};
        opt.datetime = {preset : 'datetime'};
        opt.time = {preset : 'time'};
        opt.default = {
            theme: 'android-ics light', //皮肤样式
            display: 'modal', //显示方式
            mode: 'scroller', //日期选择模式
            dateFormat: 'yyyy-mm-dd',
            lang: 'zh',
            startYear:startDate[0], //开始年份
            endYear: endDate[0] ,//结束年份,
            startHour:startDate[2], //开始时间
            minDate: new Date()
        };
        var optDateTime = $.extend(opt['datetime'], opt['default']);
        $(id).mobiscroll(optDateTime).datetime(optDateTime);
    },
    //获取当前时间
    getDateStr:function(AddDayCount){
        var dd = new Date();
        dd.setDate(dd.getDate()+AddDayCount);//获取AddDayCount天后的日期
        var y = dd.getFullYear();
        var m = dd.getMonth()+1;//获取当前月份的日期
        var d = dd.getDate();
        return y+"-"+m+"-"+d;
    },
   //抢单页面
    garyTime:function(n){
        var i = null,that = this;
        if (n == 1) {
            clearTimeout(i);
            $('.js_grab_order').addClass('disabled').html('抢单失败');

            //抢单失败退回首页
            if($('.js_grab_order.disabled') && $('.js_grab_order.disabled').length){
                setTimeout(function(){
                    window.location.href="index.html"
                },500)
            }
            return false;
        } else {
            n--;
            i = setTimeout(function () {
                that.garyTime(n);
            }, 1000);
            $('.js_grab_order span').html(n);
            return false;
        }


    },
    //判断手机系统
    isSystem:function(){
        var  us = navigator.userAgent.toLowerCase();
        if ((us.indexOf('android') > -1 || us.indexOf('linux') > -1) || navigator.platform.toLowerCase().indexOf('linux') != -1) {
            return 'android'
        } else if (us.indexOf('iphone') > -1 || us.indexOf('ipad') > -1) {
            return 'ios'
        }
    },
    //热力图
    hotPointMap:function(){
        var h = $(window).height(),
            th=$('.header').height(),
            fh=$('.hot_footer').height();
        $('#l-map').height(h-th-fh);
        //获取两个数之间的随机数
        var arr1 = [],
            arr2 = [],
            arr3 =[],
             num = null;
        /*
        * 随机获取两个数字之间的数据
        * arr 代表数组
        * m 代表 第一个数字
        * n 代表第二个数字
        * t 代表是获取整数还是小数  1代表小数  0代表整数
        * */
        function getx(arr,m,n,t){
            for(var i=0;i>-1;i++){
                var flag = true;
                var c = m-n;
                if(t == 1){
                    num = Math.random() * c + n;
                    num = Number(num.toString().match(/^\d+(?:\.\d{0,8})?/))
                }else{
                    num = Math.floor(Math.random()*100+1);
                }
                for(var i in arr){
                    if(arr[i] == num){
                        flag= false;
                        break;
                    }
                }
                if(flag == true){
                    arr.push(num);
                    return;
                }
            }
        }
        //创建地图
        var map = new BMap.Map("l-map");
        //根据当前经纬度设置地图
        var geolocation = new BMap.Geolocation();
        geolocation.getCurrentPosition(function(r){
            var adr1 =null,adr2=null;
            if(this.getStatus() == BMAP_STATUS_SUCCESS){
                //根据浏览器经纬度设定地点
                var point = new BMap.Point(r.point.lng, r.point.lat);
                map.centerAndZoom(point,14);
                //创建标注
                var mk = new BMap.Marker(point);
                map.addOverlay(mk);
                mk.setAnimation(BMAP_ANIMATION_BOUNCE);
                //热力图
                hot(r,point);
                //获取地址
                dirctInfo(point);
                //拖拽
                dragging(mk,point);
            }
            else {
                alert('failed'+this.getStatus());
            }
        },{enableHighAccuracy: true});

        //获取标注地信息
        function dirctInfo(point) {
            var gc = new BMap.Geocoder();            //创建地理编码
            gc.getLocation(point, function (rs) {
                info(rs)
            });
        };

        //获取地址
        function info(rs){
            try{
                item =rs.surroundingPois[0].title;
                if(item == 'undefined' || item == ''){
                    $('.hot_footer .l').css({'line-height':'1.3333rem'})
                }else{
                    $('.hot_footer .l').css({'line-height':'22px','padding':'5px 0 2px'})
                }
                var addComp = rs.addressComponents;
                var html = addComp.district+ addComp.street+ addComp.streetNumber+'</br>'+item;
                $('.hot_footer .l').html(html);
            }catch(e){}
        }

        //拖拽
        function dragging(m,point) {
            m.enableDragging();//可拖拽
            m.addEventListener('dragend', function (e) {//拖动标注结束
                var point1 = e.point;
                map.centerAndZoom(point1, 14);
                dirctInfo(point1);
                //计算当前位置和拖拽后点的距离
                var distance = map.getDistance(point,point1);
                $('.hot_footer .r').html(Math.ceil(distance) + 'm');
            });

        };
        //热点
        function hot(r,point){
            // 设置热点区域的经纬度  随机的在位置周围选取20个点作为热点
            var le = r.point.lng -.025,
                ge = r.point.lng +.025,
                ke = r.point.lat-.015,
                fe = r.point.lat+.015;

            //把经纬度添加到一个数组
            for(var i=0;i<20;i++){
                getx(arr1,le,ge,1);
                getx(arr2,ke,fe,1);
                getx(arr3,1,100,0);
            }
            //设置热力区域的范围大小
            var points=[];
            for(var i=0;i<arr1.length;i++){
                points.push({"lng":arr1[i],"lat":arr2[i],"count":arr3[i]})
            }

            //判断浏览器是否支持热力图,不支持就给用户提示
            if(!isSupportCanvas()){
                alert('热力图目前只支持有canvas支持的浏览器,您所使用的浏览器不能使用热力图功能~')
            }

            //热力图的展示
            if(points.length>0){
                heatmapOverlay = new BMapLib.HeatmapOverlay({"radius":50});
                map.addOverlay(heatmapOverlay);
                heatmapOverlay.setDataSet({data:points,max:100});
                //是否显示热力图
                heatmapOverlay.show();
                setGradient();
            }

            //热力图的颜色显示
            function setGradient(){
                var gradient = {
                    0:'rgb(247, 212, 120)',
                    .4:'rgb(236, 188, 60)',
                    .6:'rgb(246, 161, 47)',
                    .8:'rgb(246, 143, 65)',
                    1:'rgb(239,69,42)'
                };
                var colors = document.querySelectorAll("input[type='color']");
                colors = [].slice.call(colors,0);
                colors.forEach(function(ele){
                    gradient[ele.getAttribute("data-key")] = ele.value;
                });
                heatmapOverlay.setOptions({"gradient":gradient});
            }
            //判断浏览区是否支持canvas
            function isSupportCanvas(){
                var elem = document.createElement('canvas');
                return !!(elem.getContext && elem.getContext('2d'));
            }
        }

    }
};

$(function () {
    driverLu.init();
});