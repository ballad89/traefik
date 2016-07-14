
# Examples

You will find here some configuration examples of Træfɪk.

## HTTP only

```
defaultEntryPoints = ["http"]
[entryPoints]
  [entryPoints.http]
  address = ":80"
```

## HTTP + HTTPS (with SNI)

```
defaultEntryPoints = ["http", "https"]
[entryPoints]
  [entryPoints.http]
  address = ":80"
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]
      [[entryPoints.https.tls.certificates]]
      CertFile = "integration/fixtures/https/snitest.com.cert"
      KeyFile = "integration/fixtures/https/snitest.com.key"
      [[entryPoints.https.tls.certificates]]
      CertFile = "integration/fixtures/https/snitest.org.cert"
      KeyFile = "integration/fixtures/https/snitest.org.key"
```

## HTTPS with certificate pair as string

```
defaultEntryPoints = ["http", "https"]
[entryPoints]
  [entryPoints.http]
  address = ":80"
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]
      [[entryPoints.https.tls.certificates]]
      CertFile = `-----BEGIN CERTIFICATE-----
MIIC/zCCAeegAwIBAgIJAL858pci5XyjMA0GCSqGSIb3DQEBBQUAMBYxFDASBgNV
BAMMC3NuaXRlc3QuY29tMB4XDTE1MTEyMzIyMDU1NloXDTI1MTEyMDIyMDU1Nlow
FjEUMBIGA1UEAwwLc25pdGVzdC5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAw
ggEKAoIBAQDVF25wEroSIUO/dNgHxlyt8pZFVpJ8fNaJw7cnlZ1JP2hLuEbmjAFT
dHqS8wKDNYHktsBEOUfN/qbk0AiGb+SvhQw6kfM/QSj9fXVQ7KhYP9XYOekTOH7d
M0Z2L3RGgqs8z+83exOOnAFVvIJCMZJXEeijV6iJlmpCcJa0Kg/JHlxhoWTEeZuU
G+hITafk1yWOKorTCPlMhB30wuQoWfbHP+3G0bsERLXFiMANE8EtQu8+ZhfseBUh
5Tu5gIC4Fnria7mRixAZeEiAblFP9h0vrNRcP3nmuVz0tHPIeQsJQiEhxaZ09oUW
h9WqTsYCP1821+SVazM9oFRTpy6chZyTAgMBAAGjUDBOMB0GA1UdDgQWBBSz9mbX
ia1TM5FG4Zgagaet24S8HDAfBgNVHSMEGDAWgBSz9mbXia1TM5FG4Zgagaet24S8
HDAMBgNVHRMEBTADAQH/MA0GCSqGSIb3DQEBBQUAA4IBAQB79W8XTxlozh9w/W7T
5vDev67G4T/wetABSb68CRrqojt78PMJuS89JarA8I3ts00O+0JYnsHxp+9qC7pf
jWHcDSiLwRUMu7MXW/KIen1EB8BQNA0xWbAiQaWYPHzsBlX48+9wBe0HTDx7Lcxb
OsmnXHBF5fd2EY+R8qJu+PyTDDL1WLItFJpzHiFiGiYF8Tyic3kkPjje6eIOxRmT
hq+qbwApzbzz6h/VD5xR3zBDFBo2Xs5tdP264KIw/YXDpaXVBiJ5DDjQ3dtJw1G5
yzgrHQZWJN8Gs8ZZgGdgRf7PHox8xEZtqPiMkChDz6T7Ha3U0xYN6TZGNZOR6DHs
K9/8
-----END CERTIFICATE-----
`
      KeyFile = `-----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEA1RducBK6EiFDv3TYB8ZcrfKWRVaSfHzWicO3J5WdST9oS7hG
5owBU3R6kvMCgzWB5LbARDlHzf6m5NAIhm/kr4UMOpHzP0Eo/X11UOyoWD/V2Dnp
Ezh+3TNGdi90RoKrPM/vN3sTjpwBVbyCQjGSVxHoo1eoiZZqQnCWtCoPyR5cYaFk
xHmblBvoSE2n5NcljiqK0wj5TIQd9MLkKFn2xz/txtG7BES1xYjADRPBLULvPmYX
7HgVIeU7uYCAuBZ64mu5kYsQGXhIgG5RT/YdL6zUXD955rlc9LRzyHkLCUIhIcWm
dPaFFofVqk7GAj9fNtfklWszPaBUU6cunIWckwIDAQABAoIBABAdQYDAKcoNMe5c
i6mq2n9dBPghX9qCJkcswcEAk3BilySCvvnYRJFnEY3jSqFZfoUpPMjr+/4b78sF
4F8qPwT27sHPH7H833ir8B86hlCGI0nCt1l4wD9CDWYKmKRsZT6oCtMLP6NdMMyn
AMK4tPRYqlsP2fLtqQN1ODBPrfnraoNHtOVE784iBCD5dewICA5RIQG2i/d2+CGF
+bahFqUXVCqHoxBz4AVvrRFL99VcP7P2iZyk6hDQ7fci7Xay8Wb/HutRxuqvF0aU
bG6Enk6CCtNZHLwNPp4Hqft0Udvg2tG8okYwbEmoEO40nQsCSzRCpq5Uvzi+LX1k
LykQ6+ECgYEA7x8vQoyOK60Q3LPpJFGDec2+XJPoesTfJTT6idaP7ukUL8p3FsUo
9vtxRRfhSOdPoAINmrL0TyMekO2B6zXx0pmWVpMrFwZW6zMwZAnLp/w+3USpbGCy
K12IIwvRYzTzKwoMTVAKTXm36b6oqr2La4bTdJR7REY6G374FrJb/H0CgYEA5CHk
Ym0h7cf00fw9UEHRfzUZxmCfRWY6K8InOuHdLi+u4TiyXzs8x5s0e/DN/raNmTGx
QO81UzuS3nKwc4n5QyXjVnhzR5DbbSACDwHtdnxZByL0D1KvPjtRF8F+rWXViXv2
TM7UiOmn6R375FPSAPxeyMx8Womc3EnAAfLWGk8CgYEAv8I2WBv3dzcWqqbsdF+a
G/fOjNdgO/PdLy1JLXiPfHwV4C1xSyVZMJd7wnjgBWLaC+sZldGk8kGrpXWSFlnw
T38zfMIQcCp5Uax/RfpFA7XZhAAoDe2NdBFRtyknBXPU/dLVArsJSBAwWJa5FBNk
1xoMQRVBtQLMXnh341utQNECgYEA4o1R2/ka16NaWmpPjXM/lD9skFgF84p4vFn8
UXpaB3LtDdcbNH2Ed4mHToouWAR8jCUQLTcg0r53tRdaafMcKfXnVUka2nhdoHpH
8RVt99u3IeIxU0I+q+OGPbw3jAV0UStcxpwj7q9zw4q2SuJ+y+HUUz7XQ6Yjs5Q9
7PF2c/sCgYEAhdVn5gZ5FvYKrBi46t3pxPsWK476HmQEVHVi5+od7wg+araDelAe
8QE8hc8qdZGbjdB/AHSPCeUxfO2vnpsCoSRs29o6pDvQuqvHYs+M53l5LEYeOjof
t6J/DK5Pim2CAFjYFcZk8/Gyl5HjTw3PpdWxoPD5v2Xw3bbY57IIbm4=
-----END RSA PRIVATE KEY-----
`
```


## HTTP redirect on HTTPS

```
defaultEntryPoints = ["http", "https"]
[entryPoints]
  [entryPoints.http]
  address = ":80"
    [entryPoints.http.redirect]
    entryPoint = "https"
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]
      [[entryPoints.https.tls.certificates]]
      certFile = "tests/traefik.crt"
      keyFile = "tests/traefik.key"
```

## Let's Encrypt support

```
[entryPoints]
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]
      # certs used as default certs
      [[entryPoints.https.tls.certificates]]
      certFile = "tests/traefik.crt"
      keyFile = "tests/traefik.key"
[acme]
email = "test@traefik.io"
storageFile = "acme.json"
onDemand = true
caServer = "http://172.18.0.1:4000/directory"
entryPoint = "https"

[[acme.domains]]
  main = "local1.com"
  sans = ["test1.local1.com", "test2.local1.com"]
[[acme.domains]]
  main = "local2.com"
  sans = ["test1.local2.com", "test2x.local2.com"]
[[acme.domains]]
  main = "local3.com"
[[acme.domains]]
  main = "local4.com"
```

## Override entrypoints in frontends

```
[frontends]
  [frontends.frontend1]
  backend = "backend2"
    [frontends.frontend1.routes.test_1]
    rule = "Host:test.localhost"
  [frontends.frontend2]
  backend = "backend1"
  passHostHeader = true
  entrypoints = ["https"] # overrides defaultEntryPoints
    [frontends.frontend2.routes.test_1]
    rule = "Host:{subdomain:[a-z]+}.localhost"
  [frontends.frontend3]
  entrypoints = ["http", "https"] # overrides defaultEntryPoints
  backend = "backend2"
    rule = "Path:/test"
```
