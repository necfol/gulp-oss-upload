# gulp-oss-upload

[![NPM version][npm-image]][npm-url]

[npm-image]: https://img.shields.io/npm/v/gulp-oss-upload.svg?style=flat-square
[npm-url]: https://npmjs.org/package/gulp-oss-upload

A gulp plugin for uploading static file to aliyun oss(by official ali-oss sdk).

上传文件到阿里云 OSS 的 gulp 插件.

## install
`npm install gulp-oss-upload --save-dev`

## usage
```javascript
var gulp = require('gulp');
var ossUpload = require('gulp-oss-upload');

gulp.task('publish-oss', function() {
	return gulp.src("./app.js")
		       .pipe(ossUpload({
                    accessKeyId: 'your accessKeyId',
                    accessKeySecret: 'your accessKeySecret',
                    bucket: 'your bucket name',
                    rootDir: 'v1' // upload file root directory in the bucket(optional)
		        }));
});
```

This config will upload your current directory file `app.js` to `v1/app.js` in your bucket.

## optional param

### rootDir {string}
`default: ''; //root directory`

### customObjectName {function}
```javascript
/**
 * custom object name
 * 
 * @param objectName {string} default generate objectName
 * @param rootDir {string} options.rootDir
 * @param fileRelative {string} the file path relative to cwd path
 *
 * @return {string}
 */
function(objectName, rootDir, fileRelative){
	return ''
}
```

## reference
* [gulp-oss-up](https://github.com/marshalYuan/gulp-oss-up)

  功能完全正常, 满足了我的需求(感谢作者), 但使用过程中发现 OSS SDK 不是阿里云官方的 SDK. `objectDir` 配置项也有点 [bug](https://github.com/marshalYuan/gulp-oss-up/issues/1), 因此自己参考着重写了一个.