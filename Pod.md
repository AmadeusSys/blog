步骤简介
先创建.podspec配置文件
配置完毕后使用
```
pod lib lint 验证本地文件是否有效
将代码上传至仓库后打Tag与配置文件版本一致
pod spec lint 验证仓库代码是否有效 注意spec会缓存 厂库代码变更后请及时清除缓存
pod repo push 推送至pod repo中
``` 
```
pod spec lint ScreenAdvertisement.podspec --use-libraries --allow-warnings
pod spec lint 配置文件名 --use-libraries --allow-warnings
pod repo push PrivatePodspec ScreenAdvertisement.podspec --use-libraries --allow-warnings
pod repo push 私有空间名 配置文件名 --use-libraries --allow-warnings
--use-libraries 使用本地一些三方库
--allow-warnings 显示详细错误信息
```