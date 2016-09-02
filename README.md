
var gulp = require("gulp");
gulp.task("abc",function(){
	console.log("贾楠")
});

var concat = require("gulp-concat");
gulp.task("concat",function(){
	//加载那些文件
	 gulp.src("app/*.js")
	 //整合到那个文件夹离去
	 .pipe(concat('all.js'))
	 //整合的文件夹放哪里
	 .pipe(gulp.dest("bulid/js/"));
})

var ugly = require('gulp-uglify');
gulp.task('uglyjs',function(){
	//压缩混淆文件
	gulp.src('bulid/js/all.js').pipe(ugly()).pipe(gulp.dest("bulid/js/"));
})

gulp.task("default",function(){
	//要监控的文件夹
	gulp.watch('app/a.js',["concat",'uglyjs']);
})

var ap = require("gulp-autoprefixer");
gulp.task('prefixer',function(){
	//给css加兼容性前缀
	gulp.src("app/d.css")
	.pipe(ap()).pipe(gulp.dest("bulid/css/"))
})

var server = require("gulp-webserver")

gulp.task("serve",function(){
//服务器
	gulp.src("./")
	.pipe(server({
		livereload:true,
		directoryListing:false,
		open:true
	}))
})

var less = require("gulp-less");
gulp.task("less",function(){
//css编辑工具
	gulp.src("app/less/*.less")
	.pipe(less())
	.pipe(gulp.dest('bulid/less/'));
})

npm install http-server -g
//设置http-server变量全局服务
http-server创建服务器


# -
碎记
