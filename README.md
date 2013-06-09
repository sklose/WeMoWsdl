WeMoWsdl
========

This project provides WSDL definitions that can be used to generate client-side code for controlling Belin WeMo devices.

Example usage with C#
---------------------

Add a Service Reference to 'https://raw.github.com/sklose/WeMoWsdl/master/BasicService.wsdl'. Afterwards you can run the following example code (adjust, IP address and namespaces accordingly)

```csharp
string ip = "192.168.1.101";
int port = 49153;

var client = new ServiceReference1.BasicServicePortTypeClient();
client.Endpoint.Address = new EndpointAddress(string.Format("http://{0}:{1}/upnp/control/basicevent1", ip, port));

var state = client.GetBinaryState(new ServiceReference1.GetBinaryState());
Console.WriteLine("Switch is current set to: {0}", state.BinaryState);

Console.WriteLine("Turning Switch On");
var msg = new ServiceReference1.SetBinaryState { BinaryState = "1" };
client.SetBinaryState(msg);
```