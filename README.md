# SwiftZipStream
Super simple interface for the deflate compression format in Swift. Two very easy to use classes, `DeflateStream` and `InflateStream` with only method `write`

This project is coded with Swift 4.2 and tested in XCode 10 for MacOS and iOS

##Example

```swift

var data : [UInt8] = [ /* some data here */ ]
let dataPointer = UnsafeMutablePointer<UInt8>(&data)

// compress
var deflater = DeflateStream()
var (deflated, err) = deflater.write(bytes: dataPointer, count: data.count, flush: true)
if err != nil{
  fatalError("\(err!)")
}

// decompress
var inflater = InflateStream()
var (inflated, err) = inflater.write(bytes: dataPointer, count: data.count, flush: true)
if err != nil{
  fatalError("\(err!)")
}
println("success: \(inflated == data)")
```
