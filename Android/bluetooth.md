# BlueTooth 지원하기

활용하고자 하는 객체
- BluetoothAdapter
- BluetoothGatt
- BluetoothManager
- ScanCallback
- ScanFilter
- ScanResult
- ScanSettings

## 권한
Bluetooth Derive physical location ?? 분실물 추적에 사용됨

### Specify Bluetooth feature usage
~~~
// required == true 설정된 경우 디바이스에서 블루투스 지원하지 않을 경우 Google Play Store 에서 받을 수 없게 된다.
<uses-feature android:name="android.hardware.bluetooth" android:required="true"/>
<uses-feature android:name="android.hardware.bluetooth_le" android:required="true"/>
~~~

## Set up Bluetooth
1. Get the BluetoothAdapter
2. Enable Bluetooth : 블루투스 기능의 ON/OFF 여부를 확인
    is Enable? - BluetoothAdapter.ACTION_REQUEST_ENABLE
    optional - listener for the ACTION_STATE_CHANGED

## Scan Bluetooth
ScanSettings.SCAN_MODE_LOW_LATENCY // 스캔 주기 2초로 단축 설정, 단독 세팅 옵션으로 적용해야함.

-------------------------------------------------------------------------------------------------
## 마지막 등록된 기기 기억기능이 포함된 BlueTooth Scanner 만들기 

- UiData : lastSelectedDevice, lastSelectedDeviceId
- Job 
    - Scan
        - Success : Device Update
        - Failed : Show Device Dialog
            

### Scan
~~~
job.launch {
    try {
        scanStart
    } finally {
        scanStop   // 필수적으로 실행되도록 함.
    }
}

job.cancel
~~~