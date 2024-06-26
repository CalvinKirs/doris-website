---
{
"title": "IPV4_NUM_TO_STRING",
"language": "en"
}
---

<!-- 
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at
  http://www.apache.org/licenses/LICENSE-2.0
Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
-->

## IPV4_NUM_TO_STRING

IPV4_NUM_TO_STRING

### Description

#### Syntax

`VARCHAR IPV4_NUM_TO_STRING(BIGINT ipv4_num)`

`VARCHAR INET_NTOA(BIGINT ipv4_num)`

Takes a Int16、Int32、Int64 number. Interprets it as an IPv4 address in big endian. Returns a string containing the corresponding IPv4 address in the format A.B.C.d (dot-separated numbers in decimal form).

#### Notice

Will return `NULL` if the input parameter is negative or larger than `4294967295`(num value of `'255.255.255.255'`). This function has an alias `INET_NOTA`.

### Example

```sql
mysql> select ipv4_num_to_string(3232235521);
+--------------------------------+
| ipv4_num_to_string(3232235521) |
+--------------------------------+
| 192.168.0.1                    |
+--------------------------------+
1 row in set (0.01 sec)

mysql> select num,ipv4_num_to_string(num) from ipv4_bi;
+------------+---------------------------+
| num        | ipv4_num_to_string(`num`) |
+------------+---------------------------+
|         -1 | NULL                      |
|          0 | 0.0.0.0                   |
| 2130706433 | 127.0.0.1                 |
| 4294967295 | 255.255.255.255           |
| 4294967296 | NULL                      |
+------------+---------------------------+
7 rows in set (0.01 sec)
```

### Keywords

IPV4_NUM_TO_STRING, INET_NTOA, IP
