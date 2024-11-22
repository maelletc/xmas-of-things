# TTN Documentation

## JSON formatting

The goal is to have standard to define how data should be sent to TTN.

This currently needs to be done with the SEN team and reported to the CTH team for the logic mapper.

### Example

__Basic JSON decoder example with two values__

Below is a simpler JSON decoder for data packets constructed as such:

```
+-----------------------+--------------------+
| Temperature (4 bytes) | Humidity (4 bytes) |
+-----------------------+--------------------+
```

```js
function decodeUplink(input) {
 let temperature =
 (input.bytes[3] << 24) |
 (input.bytes[2] << 16) |
 (input.bytes[1] << 8) |
 (input.bytes[0]);
 
 let humidity =
 (input.bytes[7] << 24) |
 (input.bytes[6] << 16) |
 (input.bytes[5] << 8) |
 (input.bytes[4]);
 
 return {
   data : {
     humidity: humidity,
     temperature: temperature
   }
 };
}
```