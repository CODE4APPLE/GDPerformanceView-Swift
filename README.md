#GDPerformanceView-Swift
Shows FPS, CPU usage, app and iOS versions above the status bar and report FPS and CPU usage via delegate.

![Alt text](https://github.com/dani-gavrilov/GDPerformanceView/blob/master/performance_view.PNG?raw=true "Example PNG")
![Alt text](https://github.com/dani-gavrilov/GDPerformanceView/blob/master/performance_view_2.PNG?raw=true "Example PNG")
![Alt text](https://github.com/dani-gavrilov/GDPerformanceView/blob/master/performance_view_3.PNG?raw=true "Example PNG")
![Alt text](https://github.com/dani-gavrilov/GDPerformanceView/blob/master/performance_view_4.PNG?raw=true "Example PNG")

## Installation
Simply add GDPerformanceMonitoring folder with files to your project, or use CocoaPods.

### Podfile
```
platform :ios, '8.0'
use_frameworks!

target 'project_name' do
	pod 'GDPerformanceView-Swift', '~> 1.0.2'
end
```

## Usage

Simply start monitoring. Performance view will be added above the status bar automatically.
Also, you can configure appearance as you like or just hide the monitoring view and use its delegate.

### Start monitoring

Call to start or resume monitoring and show monitoring view.

```
GDPerformanceMonitor.sharedInstance.startMonitoring()
```

```
self.performanceView = GDPerformanceMonitor.init()
self.performanceView?.startMonitoring()
```

### Stop monitoring

Call when you're done with performance monitoring.

```
self.performanceView?.stopMonitoring()
```

Call to hide and pause monitoring.

```
self.performanceView?.pauseMonitoring()
```

### Configuration

Call to change appearance.

```
self.performanceView?.configure(configuration: { (textLabel) in
	textLabel?.backgroundColor = UIColor.black
	textLabel?.textColor = UIColor.white
	textLabel?.layer.borderColor = UIColor.black.cgColor
})
```

Call to change output information.

```
self.performanceView?.appVersionHidden = true
```
```
self.performanceView?.deviceVersionHidden = true
```

Call to hide monitoring view.

```
self.performanceView?.hideMonitoring()
```

### Start monitoring and configure

```
self.performanceView?.startMonitoring(configuration: { (textLabel) in
	textLabel?.backgroundColor = UIColor.black
	textLabel?.textColor = UIColor.white
	textLabel?.layer.borderColor = UIColor.black.cgColor
})
```

### Delegate

Set the delegate and implement its method.

```
self.performanceView?.delegate = self
```

```
func performanceMonitorDidReport(fpsValue: Float, cpuValue: Float) {
	print(fpsValue, cpuValue)
}
```

## Requirements
- iOS 8.0+

## License
GDPerformanceView is available under the MIT license. See the LICENSE file for more info.
