# Test the Configuration

## Test the Rule Created

1. First <mark style="color:red;">**tail**</mark> the <mark style="color:red;">`fast.log`</mark> file with <mark style="color:red;">`sudo tail -f /var/log/suricata/fast.log`</mark>.
2. Then, using curl you can test the <mark style="color:red;">**rule**</mark> with the command <mark style="color:red;">`curl http://testmynids.org/uid/index.html`</mark>.
3. Finally check the <mark style="color:red;">`fast.log`</mark> file.

```
[1:2100498:7] GPL ATTACK_RESPONSE id check returned root [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 217.160.0.187:80 -> 10.0.0.23:41618
```
