# hms-safetydetect-demo-java
## Table of Contents

- [Introduction](https://github.com/HMS-Core/hms-safetydetect-demo-java/blob/master/SafetyDetect-SysIntegrity-Server-Sample/README.md#introduction)
- [Installation](https://github.com/HMS-Core/hms-safetydetect-demo-java/blob/master/SafetyDetect-SysIntegrity-Server-Sample/README.md#installation)
- [Configuration](https://github.com/HMS-Core/hms-safetydetect-demo-java/blob/master/SafetyDetect-SysIntegrity-Server-Sample/README.md#configuration)
- [Supported Environments](https://github.com/HMS-Core/hms-safetydetect-demo-java/blob/master/SafetyDetect-SysIntegrity-Server-Sample/README.md#supported-environments)
- [Sample Code](https://github.com/HMS-Core/hms-safetydetect-demo-java/blob/master/SafetyDetect-SysIntegrity-Server-Sample/README.md#sample-code)
- [License](https://github.com/HMS-Core/hms-safetydetect-demo-java/blob/master/SafetyDetect-SysIntegrity-Server-Sample/README.md#license)

## Introduction

SafetyDetect SysIntegrity Server Sample provides sample program to verify the check result on your server.

 SafetyDetect UserDetect Server Sample provides sample program to obtain the detection result. 

## Installation

Before using SafetyDetect Server Sample code, check whether java environment and Maven has been installed. Decompress the SafetyDetect Server sample code package.

## Supported Environments

Java 1.7 or a later version is recommended.

## Configuration

No additional configuration is required.

## Sample Code

### SafetyDetect SysIntegrity Server Sample Code

1. Parse the JWS-format result to obtain header, payload, and signature.
2. Obtain the certificate chain from header and use the HUAWEI CBG Root CA certificate to verify it.
3. Verify the domain name of the leaf certificate in the certificate chain. The correct domain name is sysintegrity.platform.hicloud.com.
4. Obtain the signature from signature and verify it.
5. Obtain the integrity verification result from payload. The format and example are as follows:

```
{
    "advice":"RESTORE_TO_FACTORY_ROM",
    "apkCertificateDigestSha256":[
        "yT5JtXRgeIgXssx1gQTsMA9GzM9ER4xAgCsCC69Fz3I="
    ],
    "apkDigestSha256":"6Ihk8Wcv1MLm0O5KUCEVYCI/0KWzAHn9DyN38R3WYu8=",
    "apkPackageName":"com.huawei.hms.safetydetectsample",
    "basicIntegrity":false,
    "nonce":"R2Rra24fVm5xa2Mg",
    "timestampMs":1571708929141
}
```

More API information please visit  https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/SafetyDetectSysIntegrityDevelopment 

###  SafetyDetect UserDetect Server Sample Code

Perform the following steps on the server:

1. Obtain an access token.
2. Call the cloud-side API to obtain the detection result.

The procedure is as follows: Obtain an access token. For details, please refer to Open Platform Authentication. Call the cloud-side API to obtain the detection result. The following is a request example:

```
POST https://rms-api.cloud.huawei.com/rms/v1/userRisks/verify?appId=123456 HTTP/1.1
Content-Type: application/json;charset=utf-8
{
    "accessToken":"AAWWHI94sgUR2RU5_P1ZptUiwLq7W8XWJO2LxaAPuXw4_HOJFXnBlN-q5_3bwlxVW_SHeDPx_s5bWW-9DjtWZsvcm9CwXe1FHJg0u-D2pcQPcb3sTxDTJeiwEb9WBPl_9w",
    "response":"bc9d6e73-b422-4d7c-8464-2a8b5ad5b525"
}
```

More API information please visit  https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/SafetyDetectUserDetectDevelopment 

## License

SafetyDetect SysIntegrity Server Sample is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).
