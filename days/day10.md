# Abusing Hop-by-Hop Headers

Hop-by-hop headers, which are meaningful only for a single transport-level connection, and are not stored by caches or forwarded by proxies. 

Index | Section
--- | ---
**1** | What is Hop-by-Hop Headers
**2** | Attack Description
**3** | Working of the Attack
**4** | Attacks by Abusing Hop-by-Hop Header
**5** | Practice & Tools
___
#### What is Hop-by-Hop Headers
```
Hop-by-hop headers are meaningful only for a single transport-level connection, and are not stored by caches or forwarded by proxies.
Only H-b-H headers may be set using the Connection header.

The following HTTP/1.1 headers are H-b-H headers:
      - Connection
      - Keep-Alive
      - Proxy-Authenticate
      - Proxy-Authorization
      - TE
      - Trailers
      - Transfer-Encoding
      - Upgrade

All other headers defined by HTTP/1.1 are end-to-end headers.
A request may also define a custom set of headers to be treated as hop-by-hop by adding them to the Connection header

like so:
"Connection: close, X-Foo, X-Bar"
```
#### Attack Description
```
1. Removing header from HTTP Req isn't an issue itself but being able to remove headers that weren't in the original req but were added by either the frontend or another proxy in the chain could create unexpected results.

2. The Connection header itself is the default hop-by-hop header. This implies that a compatible proxy server should not forward a list of custom hop-by-hop headers to the next server in the chain in its Connection header when it forwards the request.

3. In practice this does not always occur, some systems either forward the entire Connection header/copy the H-b-H list & add it to their own Connection header. Ex most likely HAProxy passes the Connection header untouched, the same behavior with Nginx in reverse proxy mode
```
#### Working of the Attack
```
1. Suppose an application requires Cookie Headers in order to process a request and allow the user to access the target host.

2. Now, to test the H-b-H Header abuse, assume the Attacker includes a modified connection header in the HTTP Req.

3. The goal here to add the "Cookie" header name in the connection header is to ask the proxy to forward the request with Cookie Headers and then somewhere in intermediate proxy to drop this cookie header and forward the request without cookie header.

4. When the request reaches the final source, it will not contain the cookie headers and if the app is vulnerable to H-b-H Header abuse attack, the attacker will be able to access the endpoint w/o the need to have a valid user's cookie or may give some unexpected results.
```
#### Attacks by Abusing Hop-by-Hop Header
```
1. Fingerprinting Services
2. Accessing Authenticated Endpoint or Protected Information 
3. Masking the Source IP 
4. Cache Poisoned Denial of Service (CPDoS)
5. SSRF
6. WAF Bypass
```
#### resource
```
https://nathandavison.com/blog/abusing-http-hop-by-hop-request-headers
```
#### Practice & Tools
```
https://github.com/mrtc0/abusing-hop-by-hop-header

https://gist.github.com/ndavison/298d11b3a77b97c908d63a345d3c624d

- One liner to test: 
for HEADER in $(cat headers.txt); do python http://poison-test.py -u "https://target" -x "$HEADER"; sleep 1; done
 
- List of Headers:
https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/BurpSuite-ParamMiner/lowercase-headers

https://0xn3va.gitbook.io/cheat-sheets/web-application/abusing-http-hop-by-hop-request-headers

https://nathandavison.com/blog/abusing-http-hop-by-hop-request-headers
```
