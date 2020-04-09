最近在尝试使用私有POD封装通用逻辑，遇到一个问题友盟SDK的导入方式让我的SWIFT代码无法合入。
经过尝试使用了如下思路
使用NSClassFromString动态获取友盟class如果获取不到这停止操作
使用NSSelectorFromString 验证具体方法是否有效
最后使用class.perform()函数动态调用方法
```
guard let mobClick: NSObject = NSClassFromString("MobClick") as? NSObject else {
    return
}
let event = NSSelectorFromString("event:attributes:")
if mobClick.responds(to: event) == true {
    mobClick.perform(event, with: "a", with: ["a", "b"])
}
```