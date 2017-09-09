# react-native-install-apk(android only)
## install
`npm install react-native-install-apk --save`  
`react-native link react-native-install-apk`

## usage  
    import { NativeModules } from 'react-native';  
    NativeModules.InstallApk.install(path);  

## example code  
you can use [react-native-fs](https://github.com/johanneslumpe/react-native-fs) to download the apk file:  

    var filePath = RNFS.DocumentDirectoryPath + '/com.domain.example.apk';
    var download = RNFS.downloadFile({
        fromUrl: 'apk file download url',
        toFile: filePath,
        progress: res => {
            console.log((res.bytesWritten / res.contentLength).toFixed(2));
        },
        progressDivider: 1
    });
    download.promise.then(result => {
        if(result.statusCode == 200){
            NativeModules.InstallApk.install(filePath);
        }
    });
