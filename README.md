ITMS-91061: Missing privacy manifest - Your app includes “Frameworks/UnityFramework.framework/UnityFramework”, which includes UnityFramework, an SDK that was identified in the documentation as a privacy-impacting third-party SDK. Starting November 12, 2024, if a new app includes a privacy-impacting SDK, or an app update adds a new privacy-impacting SDK, the SDK must include a privacy manifest file. Please contact the provider of the SDK that includes this file to get an updated SDK version with a privacy manifest. For more details about this policy, including a list of SDKs that are required to include signatures and manifests, visit: https://developer.apple.com/support/third-party-SDK-requirements.

问题详情如下：
ITMS-91061: 缺少隐私声明 - 你的应用包含“Frameworks/UnityFramework.framework/UnityFramework”，其中包括了UnityFramework，这个SDK在文档中被标识为一个影响隐私的第三方SDK。从2024年11月12日开始，如果一个新应用包含一个影响隐私的SDK，或者一个应用更新添加了一个新的影响隐私的SDK，则该SDK必须包含隐私声明文件。请联系包含该文件的SDK提供商获取一个包含隐私声明的更新版本SDK。有关此政策的更多详细信息，包括必须包含签名和声明的SDK列表，请访问：https://developer.apple.com/support/third-party-SDK-requirements。

解决办法：
1. 使用新版本Unity出一个空的xcode工程查看 PrivacyInfo.xcprivacy 文件的格式与内容 熟悉PrivacyInfo.xcprivacy文件格式
   <?xml version="1.0" encoding="utf-8"?>
<plist version="1.0">
  <dict>
    <key>NSPrivacyAccessedAPITypes</key>
    <array>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategorySystemBootTime</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>35F9.1</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategoryDiskSpace</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>E174.1</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategoryUserDefaults</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>CA92.1</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategoryFileTimestamp</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>0A2A.1</string>
          <string>C617.1</string>
        </array>
      </dict>
    </array>
    <key>NSPrivacyTracking</key>
    <false />
  </dict>
</plist>

       
2. 参考参数说明进行文件内容补充
<?xml version="1.0" encoding="utf-8"?>
<plist version="1.0">
  <dict>
  <key>NSPrivacyTrackingDomains</key>
  <array/>
  <key>NSPrivacyCollectedDataTypes</key>
  <array>
      <dict>
        <key>NSPrivacyCollectedDataType</key>
        <string>NSPrivacyCollectedDataTypeDeviceID</string>
        <key>NSPrivacyCollectedDataTypeLinked</key>
        <false/>
        <key>NSPrivacyCollectedDataTypeTracking</key>
        <false/>
        <key>NSPrivacyCollectedDataTypePurposes</key>
        <array>
          <string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyCollectedDataType</key>
        <string>NSPrivacyCollectedDataTypeName</string>
        <key>NSPrivacyCollectedDataTypeLinked</key>
        <false/>
        <key>NSPrivacyCollectedDataTypeTracking</key>
        <false/>
        <key>NSPrivacyCollectedDataTypePurposes</key>
        <array>
          <string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyCollectedDataType</key>
        <string>NSPrivacyCollectedDataTypePhoneNumber</string>
        <key>NSPrivacyCollectedDataTypeLinked</key>
        <false/>
        <key>NSPrivacyCollectedDataTypeTracking</key>
        <false/>
        <key>NSPrivacyCollectedDataTypePurposes</key>
        <array>
          <string>NSPrivacyCollectedDataTypePurposeAppFunctionality</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyCollectedDataType</key>
        <string>NSPrivacyCollectedDataTypeOtherDataTypes</string>
        <key>NSPrivacyCollectedDataTypeLinked</key>
        <false/>
        <key>NSPrivacyCollectedDataTypeTracking</key>
        <false/>
        <key>NSPrivacyCollectedDataTypePurposes</key>
        <array>
          <string>NSPrivacyCollectedDataTypePurposeAnalytics</string>
        </array>
      </dict>
    </array>
    <key>NSPrivacyAccessedAPITypes</key>
    <array>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategorySystemBootTime</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>35F9.1</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategoryDiskSpace</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>E174.1</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategoryUserDefaults</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>CA92.1</string>
        </array>
      </dict>
      <dict>
        <key>NSPrivacyAccessedAPIType</key>
        <string>NSPrivacyAccessedAPICategoryFileTimestamp</string>
        <key>NSPrivacyAccessedAPITypeReasons</key>
        <array>
          <string>0A2A.1</string>
          <string>C617.1</string>
        </array>
      </dict>
    </array>
    <key>NSPrivacyTracking</key>
    <false />
  </dict>
</plist>


3.将PrivacyInfo.xcprivacy放到对应xcode工程的UnityFramework文件夹内

![image](https://github.com/user-attachments/assets/b8f81503-00c1-4ea0-bdff-20f991b3e025)

![image](https://github.com/user-attachments/assets/048f0e83-14bc-4d42-9ba6-707b6820aed6)


4.使用python进行xcode工程进行文件关联

PS：当前使用版本Unity2020.3.x 重新上架了应用没有再给警告邮件，理论上2021版本以后Unity已经处理了 Unity2018以前版本xcode工程不是Framewor方式无需处理
Unity2019没有测试 应该和Unity2020 类似 具体差异自行修改
