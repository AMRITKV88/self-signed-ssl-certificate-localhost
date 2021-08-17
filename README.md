# Generate self-signed ssl certificate for localhost

To do this, it needs to have openssl installed.

Openssl executor can be installed from different sources, but if you don't want to roam here and there, then it can be found in your system itself, if you have git installed in your system.

To find the openssl executor in windows, go to git installed folder i.e.: "C:\Program Files\Git\usr\bin" and there you can find the `openssl.exe`. To set the path, type the below command :

1. Open `cmd` with admin access into a directory/folder

2. Command 1 : `set PATH=%PATH%;C:\Program Files\Git\usr\bin;.`
3. Command 2 : `openssl req -x509 -nodes -days 365 -subj "/C=CA/ST=QC/O=Company, Inc./CN=localhost" -addext "subjectAltName=DNS:localhost,DNS:127.0.0.1" -newkey rsa:2048 -keyout nginx-selfsigned.key -out nginx-selfsigned.crt`

4. Command 3 : `call certutil -addstore -f -enterprise -user root "%~dp0nginx-selfsigned.crt"`

N.B. : `Command 2` is to generate the self signed ssl certificate and `Command 3` is used for giving trusted root permission to the certificate.
