# node moudle 复习
## module对象
## 主模块
## 查找包规则(require)
## 包的缓存
## 循坏依赖
## moudle 的实现
(function(exports,require,module,__filename,__dirname) {

})
## exports 和 module.exports的区别
## require.cache
### 缓存构建
Modules are cached in this object when they are required. By deleting a key value from this object, the next require will reload the module. Note that this does not apply to native addons, for which reloading will result in an error
## Tips
### 在内部中使用module
## 热更新

