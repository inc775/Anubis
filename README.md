# Anubis

            d8888                   888      d8b
           d88888                   888      Y8P
          d88P888                   888
         d88P 888 88888b.  888  888 88888b.  888 .d8888b
        d88P  888 888 "88b 888  888 888 "88b 888 88K
       d88P   888 888  888 888  888 888  888 888 "Y8888b.
      d8888888888 888  888 Y88b 888 888 d88P 888      X88
     d88P     888 888  888  "Y88888 88888P"  888  88888P'

Welcome to Anubis, a subdomain enumerator and information gathering tool.

## Requirements

``pip install -r requirements``

* Python 3.6
* Nmap

## Usage

    Usage:
      anubis -t TARGET [-o FILENAME] [--with-nmap] [-iv]
      anubis -h
      anubis --version
      
    Options:
      -h --help               show this help message and exit
      -t --target             set target
      --with-nmap             perform an nmap service/script scan
      -o --output             save to filename
      -i --additional-info    show additional information about the host from Shodan (requires API key)
      --version               show version and exit
      -v --verbose            print debug info/full info dumps
    
    Help:
      For help using this tool, please open an issue on the Github repository:
      https://github.com/jonluca/anubis
      
## Sample Output
### Basic
```anubis -t reddit.com``` 

```
Searching for subdomains for 151.101.129.140
Found 126 domains
----------------
aa.reddit.com
ss.reddit.com
qu.reddit.com
roosterteeth.reddit.com
http://dg.reddit.com
pp.reddit.com
i.reddit.com
http://www.reddit.com
di.reddit.com
bj.reddit.com
augustames.reddit.com
so.reddit.com
www.reddit.com
http://reddit.com
http://nj.reddit.com
space.reddit.com
api.reddit.com
```

### Advanced
```anubis -t reddit.com --with-nmap -o temp.txt -is --overwrite-nmap-scan "-F -T5"``` 

```
Searching for subdomains for 151.101.129.140
Running SSL Scan
Available TLSv1.0 Ciphers:
    TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
    TLS_RSA_WITH_AES_256_CBC_SHA
    TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
    TLS_RSA_WITH_AES_128_CBC_SHA
    TLS_RSA_WITH_3DES_EDE_CBC_SHA
Available TLSv1.2 Ciphers:
    TLS_RSA_WITH_AES_256_CBC_SHA
    TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
    TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
    TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
    TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
    TLS_RSA_WITH_AES_128_CBC_SHA
    TLS_RSA_WITH_AES_128_GCM_SHA256
    TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256
    TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
    TLS_RSA_WITH_3DES_EDE_CBC_SHA
 * Certificate Information:
     Content
       SHA1 Fingerprint:                  f8d1965323111e86e6874aa93cc7c52969fb22bf
       Common Name:                       *.reddit.com
       Issuer:                            DigiCert SHA2 Secure Server CA
       Serial Number:                     11711178161886346105980166697563149367
       Not Before:                        2015-08-17 00:00:00
       Not After:                         2018-08-21 12:00:00
       Signature Algorithm:               sha256
       Public Key Algorithm:              RSA
       Key Size:                          2048
       Exponent:                          65537 (0x10001)
       DNS Subject Alternative Names:     ['*.reddit.com', 'reddit.com', '*.redditmedia.com', 'engine.a.redditmedia.com', 'redditmedia.com', '*.redd.it', 'redd.it', 'www.redditstatic.com', 'imgless.reddituploads.com', 'i.reddituploads.com', '*.thumbs.redditmedia.com']

     Trust
       Hostname Validation:               OK - Certificate matches reddit.com
       AOSP CA Store (7.0.0 r1):          OK - Certificate is trusted
       Apple CA Store (OS X 10.11.6):     OK - Certificate is trusted
       Java 7 CA Store (Update 79):       OK - Certificate is trusted
       Microsoft CA Store (09/2016):      OK - Certificate is trusted
       Mozilla CA Store (09/2016):        OK - Certificate is trusted
       Received Chain:                    *.reddit.com --> DigiCert SHA2 Secure Server CA
       Verified Chain:                    *.reddit.com --> DigiCert SHA2 Secure Server CA --> DigiCert Global Root CA
       Received Chain Contains Anchor:    OK - Anchor certificate not sent
       Received Chain Order:              OK - Order is valid
       Verified Chain contains SHA1:      OK - No SHA1-signed certificate in the verified certificate chain

     OCSP Stapling
       OCSP Response Status:              successful
       Validation w/ Mozilla Store:       OK - Response is trusted
       Responder Id:                      0F80611C823161D52F28E78D4638B42CE1C6D9E2
       Cert Status:                       good
       Cert Serial Number:                08CF7DA9B222C9D983C50D993F2F5437
       This Update:                       Dec 10 16:18:57 2017 GMT
       Next Update:                       Dec 17 15:33:57 2017 GMT
Server Location: San Francisco US - 94107
ISP: Fastly
Starting Nmap Scan
Host : 151.101.129.140 ()
----------
Protocol: tcp
port: 53	state: open
port: 80	state: open
port: 443	state: open
Found 126 domains
----------------
nd.reddit.com
askreddit.reddit.com
roosterteeth.reddit.com
qu.reddit.com
cp.reddit.com
mx02.reddit.com
nh.reddit.com
...
```

Additionally, it would write out to a file called "out.txt" in the directory in which it was called.


## Credits

CLI Boilerplate by [Skele-CLI](https://github.com/rdegges/skele-cli)