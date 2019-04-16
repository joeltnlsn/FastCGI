# Breaking Changes

### WriteResponseUtf8(string) and WriteResponseASCII(string)
Were replaced with `WriteResponseString(string, Encoding)` which is more flexible.

### GetParameterUTF8(string) and GetParameterASCII(string)
Were replaced with `GetFCGIParam(string, encoding)` which is more flexible and less confusing.