# 主题

## 一、标题显示

### 列表显示

- 物理像素 device pixel: 物理像素指显示设备上的物理像素点
- CSS像素 css pixel: 指我们写页面时理解的那个像素单位px
- 独立像素dp: （dips device independent pixels）: DP用在Android上，PT用在Apple上
- 衡量设备的物理像素密度 DPI 和 PPI
	- DPI 指 Dots Per Inch（dpi ldpi mdpi hdpi for android）

## 二、代码显示
<pre>
<code class="language-javascript">
 module.exports = function(grunt) {
        var Path = require('path');
        // 项目配置(任务配置)
        grunt.initConfig({
            // 通过connect任务，创建一个静态服务器
            less: {
                development: {
                    files: {}
                }
            },
            watch: {
                files: ['/**/*.less']
            }
        });

        //用于监控less变化进行编译
            grunt.event.on('watch', function(action, filepath) {
                var fileExts = Path.extname(filepath);
                if (fileExts == '.less') {
                    var prefix = filepath.split('.less')[0];
                    var lessObj = {};
                    lessObj[prefix + '.css'] = prefix + '.less'
                    console.log(lessObj)
                    grunt.config('less.development.files', lessObj);
                    grunt.task.run(['less']);
                }

            });

        grunt.loadNpmTasks('grunt-contrib-watch');
        grunt.loadNpmTasks('grunt-contrib-less');
        grunt.registerTask('autoless', ['watch']);
    };

	</code>
</pre>



