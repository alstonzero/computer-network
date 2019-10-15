### DNS recursive query vs. Iterative query

The goal of DNS is to resolve a fully qulified domain name(FQDN) to an IP address.The process is called name resolution.

#### recursive query(递归查询)

The recursive query demands a name resolution or the answer:"It can't be found."



递归查询是一种DNS 服务器的查询模式，在该模式下DNS 服务器接收到客户机请求，必须使用一个准确的查询结果回复客户机。如果DNS 服务器本地没有存储查询DNS 信息，那么该服务器会询问其他服务器，并将返回的查询结果提交给客户机。



#### iterative query

The iterative query is between a local DNS server and other DNS servers.





DNS 服务器另外一种查询方式为迭代查询，DNS 服务器会向客户机提供其他能够解析查询请求的DNS 服务器地址，当客户机发送查询请求时，DNS 服务器并不直接回复查询结果，而是告诉客户机另一台DNS 服务器地址，客户机再向这台DNS 服务器提交请求，依次循环直到返回查询的结果