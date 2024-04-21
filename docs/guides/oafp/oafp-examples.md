---
layout: default
title: oafp reference list of examples
parent: oafp
grand_parent: Guides
---

# oafp reference list of examples

Examples of use of _oafp_ avaiable also in [https://ojob.io/oafp-examples.yaml](https://ojob.io/oafp-examples.yaml).

## 📚 Contents

| Category | Sub-category | #   | Description |
|:---------|:-------------|:----|:------------|
| AI | Conversation | [1](#1) | Send multiple requests to an OpenAI model keeping the conversation between interactions and setting the temperature parameter |
| AI | Ollama | [2](#2) | Setting up access to Ollama and ask for data to an AI LLM model |
| AI | OpenAI | [3](#3) | Setting up the OpenAI LLM model and gather the data into a data.json file |
| AI | Prompt | [4](#4) | Example of generating data from an AI LLM prompt |
| AI | Summarize | [5](#5) | Use an AI LLM model to summarize the weather information provided in a JSON format |
| APIs | Network | [6](#6) | Converting the Cloudflare DNS trace info |
| APIs | Network | [7](#7) | Converting the Google DNS DoH query result |
| APIs | Network | [8](#8) | Generating a simple map of the current public IP address |
| APIs | Public Holidays | [9](#9) | Return the public holidays for a given country on a given year |
| APIs | iTunes | [10](#10) | Search the Apple&#x27;s iTunes database for a specific term |
| AWS | EC2 | [11](#11) | Given all AWS EC2 instances in an account produces a table with name, type, vpc and private ip sorted by vpc |
| AWS | EKS | [12](#12) | Builds an excel spreadsheet with all persistent volumes associated with an AWS EKS &#x27;XYZ&#x27; with the corresponding Kubernetes namespace, pvc and pv names |
| AWS | Lambda | [13](#13) | Prepares a table of AWS Lambda functions with their corresponding main details |
| AWS | Lambda | [14](#14) | Prepares a table, for a specific AWS Lambda function during a specific time periods, with number of invocations and minimum, average and maximum duration per periods from AWS CloudWatch |
| Chart | Unix | [15](#15) | Output a chart with the current Unix load using uptime |
| DB | H2 | [16](#16) | Perform a SQL query over a H2 database. |
| DB | H2 | [17](#17) | Store the json result of a command into a H2 database table. |
| DB | SQLite | [18](#18) | Perform a query over a database using JDBC. |
| DB | SQLite | [19](#19) | Store the json result on a SQLite database table. |
| Docker | Containers | [20](#20) | Output a table with the list of running containers. |
| Docker | Listing | [21](#21) | List all containers with the docker-compose project, service name, file, id, name, image, creation time, status, networks and ports. |
| Docker | Listing | [22](#22) | List all containers with their corresponding labels parsed and sorted. |
| Docker | Network | [23](#23) | Output a table with the docker networks info. |
| Docker | Stats | [24](#24) | Output a table with the docker stats broken down for each value. |
| Docker | Storage | [25](#25) | Output a table with the docker volumes info. |
| ElasticSearch | Cluster | [26](#26) | Get an ElasticSearch/OpenSearch cluster nodes overview |
| ElasticSearch | Cluster | [27](#27) | Get an ElasticSearch/OpenSearch cluster per host data allocation |
| ElasticSearch | Cluster | [28](#28) | Get an ElasticSearch/OpenSearch cluster settings flat |
| ElasticSearch | Cluster | [29](#29) | Get an ElasticSearch/OpenSearch cluster settings non-flatted |
| ElasticSearch | Cluster | [30](#30) | Get an ElasticSearch/OpenSearch cluster stats per node |
| ElasticSearch | Cluster | [31](#31) | Get an overview of an ElasticSearch/OpenSearch cluster health |
| ElasticSearch | Indices | [32](#32) | Get an ElasticSearch/OpenSearch count per index |
| ElasticSearch | Indices | [33](#33) | Get an ElasticSearch/OpenSearch indices overview |
| ElasticSearch | Indices | [34](#34) | Get an ElasticSearch/OpenSearch settings for a specific index |
| Generic | Arrays | [35](#35) | Converting an array of strings into an array of maps |
| Generic | Excel | [36](#36) | Building an Excel file with the AWS IPv4 and IPv6 ranges (1). |
| Generic | Excel | [37](#37) | Building an Excel file with the AWS IPv4 and IPv6 ranges (2). |
| Generic | Excel | [38](#38) | Building an Excel file with the AWS IPv4 and IPv6 ranges (3). |
| Generic | Excel | [39](#39) | Processes each json file in /some/data creating and updating the data.xlsx file with a sheet for each file. |
| Generic | Excel | [40](#40) | Store and retrieve data from an Excel spreadsheet |
| Generic | Hex | [41](#41) | Outputs an hexadecimal representation of the characters of the file provided allowing to adjust how many per line/row. |
| Generic | RSS | [42](#42) | Builds an HTML file with the current linked news titles, publication date and source from Google News. |
| Generic | RSS | [43](#43) | Example of generating a HTML list of titles, links and publication dates from a RSS feed |
| Generic | Text | [44](#44) | Get a json with lyrics of a song. |
| GitHub | Releases | [45](#45) | Builds a table of GitHub project releases |
| GitHub | Releases | [46](#46) | Parses the latest GitHub project release markdown notes |
| Grid | Java | [47](#47) | Parse a Java stacktrace into a looping grid. |
| Grid | Kubernetes | [48](#48) | Displays a continuous updating grid with a line chart with the number of CPU throtlles and bursts recorded in the Linux cgroup cpu stats of a container running in Kubernetes and the source cpu.stats data |
| Grid | Mac | [49](#49) | Shows a grid with the Mac network metrics and 4 charts for in, out packets and in, out bytes |
| Grid | Mac | [50](#50) | Shows a grid with the Mac storage metrics and 4 charts for read, write IOPS and read, write bytes per second |
| Grid | Unix | [51](#51) | On an Unix/Linux system supporting &#x27;ps&#x27; output formats %cpu and %mem, will output a chart with the percentage of cpu and memory usage of a provided pid (e.g. 12345) |
| JSON Schemas | Lists | [52](#52) | Get a list of JSON schemas from Schema Store catalog |
| Kubernetes | Containers | [53](#53) | Parse the Linux cgroup cpu stats on a container running in Kubernetes |
| Kubernetes | Kubectl | [54](#54) | Build an output table with Kubernetes pods with namespace, pod name, container name and corresponding resources using kubectl |
| Kubernetes | Kubectl | [55](#55) | Build an output table with Kubernetes pods with node, namespace, pod name, container name and corresponding resources using kubectl |
| Kubernetes | Kubectl | [56](#56) | List of Kubernetes CPU, memory and storage stats per node using kubectl |
| Kubernetes | Kubectl | [57](#57) | List of Kubernetes pods per namespace and kind using kubectl |
| Mac | Activity | [58](#58) | Uses the Mac terminal command &#x27;last&#x27; output to build an activity table with user, tty, from, login-time and logout-time |
| Mac | Brew | [59](#59) | List all the packages and corresponding versions installed in a Mac by brew. |
| Mac | Info | [60](#60) | Parses the current Mac OS overview information |
| Mac | Safari | [61](#61) | Get a list of all Mac OS Safari bookmarks into a CSV file. |
| OpenAF | Channels | [62](#62) | Copy the json result of a command into an etcd database using OpenAF&#x27;s channels |
| OpenAF | Channels | [63](#63) | Getting all data stored in an etcd database using OpenAF&#x27;s channels |
| OpenAF | Channels | [64](#64) | Perform a query to a metric &amp; label, with a start and end time, to a Prometheus server using OpenAF&#x27;s channels |
| OpenAF | Channels | [65](#65) | Retrieve all keys stores in a H2 MVStore file using OpenAF&#x27;s channels |
| OpenAF | Channels | [66](#66) | Store and retrieve data from a Redis database |
| OpenAF | Channels | [67](#67) | Store and retrieve data from a RocksDB database |
| OpenAF | Channels | [68](#68) | Store the json results of a command into a H2 MVStore file using OpenAF&#x27;s channels |
| OpenAF | Network | [69](#69) | List all MX (mail servers) network addresses from the current DNS server for a hostname using OpenAF |
| OpenAF | Network | [70](#70) | List all network addresses returned from the current DNS server for a hostname using OpenAF |
| OpenAF | OS | [71](#71) | Current OS information visible to OpenAF |
| OpenAF | OS | [72](#72) | Using OpenAF parse the current environment variables |
| OpenAF | TLS | [73](#73) | List the TLS certificates of a target host with a sorted alternative names using OpenAF |
| OpenAF | oPacks | [74](#74) | Listing all currently accessible OpenAF&#x27;s oPacks |
| OpenAF | oafp | [75](#75) | Filter the OpenAF&#x27;s oafp examples list by a specific word in the description |
| OpenAF | oafp | [76](#76) | List the OpenAF&#x27;s oafp examples by category, sub-category and description |
| Unix | Activity | [77](#77) | Uses the Linux command &#x27;last&#x27; output to build a table with user, tty, from and period of activity |
| Unix | Alpine | [78](#78) | List all installed packages in an Alpine system |
| Unix | Compute | [79](#79) | Parses the Linux /proc/cpuinfo into an array |
| Unix | Debian/Ubuntu | [80](#80) | List all installed packages in a Debian/Ubuntu system |
| Unix | Files | [81](#81) | Converting the Linux&#x27;s /etc/os-release to SQL insert statements. |
| Unix | Files | [82](#82) | Converting the Unix&#x27;s syslog into a json output. |
| Unix | Files | [83](#83) | Parses the Linux /etc/passwd to a table order by uid and gid. |
| Unix | Generic | [84](#84) | Creates, in unix, a data.ndjson file where each record is formatted from json files in /some/data |
| Unix | Network | [85](#85) | Loop over the current Linux active network connections |
| Unix | Network | [86](#86) | Parse the Linux &#x27;arp&#x27; command output |
| Unix | Network | [87](#87) | Parse the Linux &#x27;ip tcp_metrics&#x27; command |
| Unix | Network | [88](#88) | Parse the result of the Linux route command |
| Unix | OpenSuse | [89](#89) | List all installed packages in an OpenSuse system or zypper based system |
| Unix | RedHat | [90](#90) | List all installed packages in a RedHat system or rpm based system (use rpm --querytags to list all fields available) |
| Unix | Storage | [91](#91) | Converting the Unix&#x27;s df output |
| Unix | Storage | [92](#92) | Parses the result of the Unix ls command |
| Unix | SystemCtl | [93](#93) | Converting the Unix&#x27;s systemctl list-timers |
| Unix | SystemCtl | [94](#94) | Converting the Unix&#x27;s systemctl list-units |
| Unix | SystemCtl | [95](#95) | Converting the Unix&#x27;s systemctl list-units into an overview table |
| Unix | UBI | [96](#96) | List all installed packages in an UBI system |
| Unix | named | [97](#97) | Converts a Linux&#x27;s named log, for client queries, into a CSV |
| Windows | Network | [98](#98) | Output a table with the current route table using Windows&#x27; PowerShell |
| Windows | Network | [99](#99) | Output a table with the list of network interfaces using Windows&#x27; PowerShell |
| Windows | PnP | [100](#100) | Output a table with USB/PnP devices using Windows&#x27; PowerShell |
| Windows | Storage | [101](#101) | Output a table with the attached disk information using Windows&#x27; PowerShell |

## 📗 Examples

---

##### 1
### 📖 AI | Conversation
Send multiple requests to an OpenAI model keeping the conversation between interactions and setting the temperature parameter
```bash
export OAFP_MODEL="(type: openai, model: 'gpt-3.5-turbo-0125', key: ..., timeout: 900000, temperature: 0)"
echo "List all countries in the european union" | oafp in=llm out=ctree llmconversation=cvst.json
echo "Add the corresponding country capital" | oafp in=llm out=ctree llmconversation=cvst.json
rm cvst.json
```
---

##### 2
### 📖 AI | Ollama
Setting up access to Ollama and ask for data to an AI LLM model
```bash
export OAFP_MODEL="(type: ollama, model: 'mistral', url: 'https://models.local', timeout: 900000)"
echo "Output a JSON array with 15 cities where each entry has the 'city' name, the estimated population and the corresponding 'country'" | oafp input=llm output=json > data.json
oafp data.json output=ctable sql="select * order by population desc"
```
---

##### 3
### 📖 AI | OpenAI
Setting up the OpenAI LLM model and gather the data into a data.json file
```bash
export OAFP_MODEL="(type: openai, model: gpt-3.5-turbo, key: ..., timeout: 900000)"
echo "list all United Nations secretaries with their corresponding 'name', their mandate 'begin date', their mandate 'end date' and their corresponding secretary 'numeral'" | oafp input=llm output=json > data.json
```
---

##### 4
### 📖 AI | Prompt
Example of generating data from an AI LLM prompt
```bash
export OAFP_MODEL="(type: openai, model: 'gpt-3.5-turbo', key: '...', timeout: 900000)"
oafp in=llm data="produce a list of 25 species of 'flowers' with their english and latin name and the continent where it can be found" out=json > data.json
```
---

##### 5
### 📖 AI | Summarize
Use an AI LLM model to summarize the weather information provided in a JSON format
```bash
export OAFP_MODEL="(type: openai, model: 'gpt-3.5-turbo', key: '...', timeout: 900000)"
oafp url="https://wttr.in?format=j2" llmcontext="current and forecast weather" llmprompt="produce a summary of the current and forecasted weather" out=md
```
---

##### 6
### 📖 APIs | Network
Converting the Cloudflare DNS trace info
```bash
curl -s https://1.1.1.1/cdn-cgi/trace | oafp in=ini out=ctree
```
---

##### 7
### 📖 APIs | Network
Converting the Google DNS DoH query result
```bash
DOMAIN=yahoo.com && oafp path=Answer from="sort(data)" out=ctable url="https://8.8.8.8/resolve?name=$DOMAIN&type=a"
```
---

##### 8
### 📖 APIs | Network
Generating a simple map of the current public IP address
```bash
curl -s https://ifconfig.co/json | oafp flatmap=true out=map
```
---

##### 9
### 📖 APIs | Public Holidays
Return the public holidays for a given country on a given year
```bash
COUNTRY=US && YEAR=2024 && oafp url="https://date.nager.at/api/v2/publicholidays/$YEAR/$COUNTRY" path="[].{date:date,localName:localName,name:name}" out=ctable
```
---

##### 10
### 📖 APIs | iTunes
Search the Apple&#x27;s iTunes database for a specific term
```bash
TRM="Mozart" && oafp url="https://itunes.apple.com/search?term=$TRM" out=ctree
```
---

##### 11
### 📖 AWS | EC2
Given all AWS EC2 instances in an account produces a table with name, type, vpc and private ip sorted by vpc
```bash
aws ec2 describe-instances | ./oafp path="Reservations[].Instances[].{name:join('',Tags[?Key=='Name'].Value),type:InstanceType,vpc:VpcId,ip:PrivateIpAddress} | sort_by(@, &vpc)" output=ctable
```
---

##### 12
### 📖 AWS | EKS
Builds an excel spreadsheet with all persistent volumes associated with an AWS EKS &#x27;XYZ&#x27; with the corresponding Kubernetes namespace, pvc and pv names
```bash
# sudo yum install -y fontconfig
aws ec2 describe-volumes | oafp path="Volumes[?Tags[?Key=='kubernetes.io/cluster/XYZ']|[0].Value=='owned'].{VolumeId:VolumeId,Name:Tags[?Key=='Name']|[0].Value,KubeNS:Tags[?Key=='kubernetes.io/created-for/pvc/namespace']|[0].Value,KubePVC:Tags[?Key=='kubernetes.io/created-for/pvc/name']|[0].Value,KubePV:Tags[?Key=='kubernetes.io/created-for/pv/name']|[0].Value,AZ:AvailabilityZone,Size:Size,Type:VolumeType,CreateTime:CreateTime,State:State,AttachTime:join(',',nvl(Attachments[].AttachTime,from_slon('[]'))[]),InstanceId:join(',',nvl(Attachments[].InstanceId,from_slon('[]'))[])}" from="sort(KubeNS,KubePVC)" out=xls xlsfile=xyz_pvs.xlsx
```
---

##### 13
### 📖 AWS | Lambda
Prepares a table of AWS Lambda functions with their corresponding main details
```bash
aws lambda list-functions | oafp path="Functions[].{Name:FunctionName,Runtime:Runtime,Arch:join(',',Architectures),Role:Role,MemorySize:MemorySize,EphStore:EphemeralStorage.Size,CodeSize:CodeSize,LastModified:LastModified}" from="sort(Name)" out=ctable
```
---

##### 14
### 📖 AWS | Lambda
Prepares a table, for a specific AWS Lambda function during a specific time periods, with number of invocations and minimum, average and maximum duration per periods from AWS CloudWatch
```bash
export _SH="aws cloudwatch get-metric-statistics --namespace AWS/Lambda --start-time 2024-03-01T00:00:00Z --end-time 2024-04-01T00:00:00Z --period 3600 --dimensions Name=FunctionName,Value=my-function"
$_SH --statistics Sum --metric-name Invocations  | oafp path="Datapoints[].{ts:Timestamp,cnt:Sum}" out=ndjson > data.ndjson
$_SH --statistics Average --metric-name Duration | oafp path="Datapoints[].{ts:Timestamp,avg:Average}" out=ndjson >> data.ndjson
$_SH --statistics Minimum --metric-name Duration | oafp path="Datapoints[].{ts:Timestamp,min:Minimum}" out=ndjson >> data.ndjson
$_SH --statistics Maximum --metric-name Duration | oafp path="Datapoints[].{ts:Timestamp,max:Maximum}" out=ndjson >> data.ndjson
oafp data.ndjson ndjsonjoin=true opath="[].{ts:ts,cnt:nvl(cnt,\`0\`),min:nvl(min,\`0\`),avg:nvl(avg,\`0\`),max:nvl(max,\`0\`)}" out=json | oafp isql="select \"ts\",max(\"cnt\") \"cnt\",max(\"min\") \"min\",max(\"avg\") \"avg\",max(\"max\") \"max\" group by \"ts\" order by \"ts\"" opath="[].{ts:ts,cnt:cnt,min:from_ms(min,'(abrev:true,pad:true)'),avg:from_ms(avg,'(abrev:true,pad:true)'),max:from_ms(max,'(abrev:true,pad:true)')}" out=ctable
```
---

##### 15
### 📖 Chart | Unix
Output a chart with the current Unix load using uptime
```bash
oafp cmd="uptime" in=raw path="replace(trim(@), '.+ ([\d\.]+),? ([\d\.]+),? ([\d\.]+)\$', '', '\$1|\$2|\$3').split(@,'|')" out=chart chart="dec2 [0]:green:load -min:0" loop=1 loopcls=true
```
---

##### 16
### 📖 DB | H2
Perform a SQL query over a H2 database.
```bash
echo "select * from \"data\"" | oafp in=db indbjdbc="jdbc:h2:./data" indbuser=sa indbpass=sa out=ctable
```
---

##### 17
### 📖 DB | H2
Store the json result of a command into a H2 database table.
```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=db dbjdbc="jdbc:h2:./data" dbuser=sa dbpass=sa dbtable=data
```
---

##### 18
### 📖 DB | SQLite
Perform a query over a database using JDBC.
```bash
ojob ojob.io/db/getDriver op=install db=sqlite
echo "select * from data" | oafp in=db indbjdbc="jdbc:sqlite:data.db" indbtable=data indblib=sqlite out=ctable
```
---

##### 19
### 📖 DB | SQLite
Store the json result on a SQLite database table.
```bash
ojob ojob.io/db/getDriver op=install db=sqlite
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=db dbjdbc="jdbc:sqlite:data.db" dbtable=data dblib=sqlite
```
---

##### 20
### 📖 Docker | Containers
Output a table with the list of running containers.
```bash
oafp cmd="docker ps --format json" input=ndjson ndjsonjoin=true path="[].{id:ID,name:Names,state:State,image:Image,networks:Networks,ports:Ports,Status:Status}" sql="select * order by networks,state,name" output=ctable
```
---

##### 21
### 📖 Docker | Listing
List all containers with the docker-compose project, service name, file, id, name, image, creation time, status, networks and ports.
```bash
docker ps -a --format=json | oafp in=ndjson ndjsonjoin=true out=ctree path="[].insert(@,'Labels',sort_by(split(Labels,',')[].split(@,'=').{key:[0],value:[1]},&key))" out=json | oafp path="[].{dcProject:nvl(Labels[?key=='com.docker.compose.project']|[0].value,''),dcService:nvl(Labels[?key=='com.docker.compose.service']|[0].value,''),ID:ID,Names:Names,Image:Image,Created:RunningFor,Status:Status,Ports:Ports,Networks:Networks,dcFile:nvl(Labels[?key=='com.docker.compose.project.config_files']|[0].value,'')}" sql="select * order by dcProject,dcService,Networks,Names" out=ctable
```
---

##### 22
### 📖 Docker | Listing
List all containers with their corresponding labels parsed and sorted.
```bash
docker ps -a --format=json | oafp in=ndjson ndjsonjoin=true out=ctree path="[].insert(@,'Labels',sort_by(split(Labels,',')[].split(@,'=').{key:[0],value:[1]},&key))" out=ctree
```
---

##### 23
### 📖 Docker | Network
Output a table with the docker networks info.
```bash
docker network ls --format json | oafp in=ndjson ndjsonjoin=true out=ctable
```
---

##### 24
### 📖 Docker | Stats
Output a table with the docker stats broken down for each value.
```bash
oafp cmd="docker stats --no-stream" in=lines linesvisual=true linesjoin=true out=ctree path="[].{containerId:\"CONTAINER ID\",pids:PIDS,name:\"NAME\",cpuPerc:\"CPU %\",memory:\"MEM USAGE / LIMIT\",memPerc:\"MEM %\",netIO:\"NET I/O\",blockIO:\"BLOCK I/O\"}|[].{containerId:containerId,pids:pids,name:name,cpuPerc:replace(cpuPerc,'%','',''),memUsage:from_bytesAbbr(split(memory,' / ')[0]),memLimit:from_bytesAbbr(split(memory,' / ')[1]),memPerc:replace(memPerc,'%','',''),netIn:from_bytesAbbr(split(netIO,' / ')[0]),netOut:from_bytesAbbr(split(netIO,' / ')[1]),blockIn:from_bytesAbbr(split(blockIO,' / ')[0]),blockOut:from_bytesAbbr(split(blockIO,' / ')[1])}" out=ctable
```
---

##### 25
### 📖 Docker | Storage
Output a table with the docker volumes info.
```bash
docker volume ls --format json | oafp in=ndjson ndjsonjoin=true out=ctable
```
---

##### 26
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster nodes overview
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/nodes?format=json" $ES_EXTRA | oafp sql="select * order by ip" out=ctable
```
---

##### 27
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster per host data allocation
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/allocation?format=json&bytes=b" $ES_EXTRA | oafp sql="select * order by host" out=ctable
```
---

##### 28
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster settings flat
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cluster/settings?include_defaults=true&flat_settings=true" $ES_EXTRA | oafp out=ctree
```
---

##### 29
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster settings non-flatted
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cluster/settings?include_defaults=true" $ES_EXTRA | oafp out=ctree
```
---

##### 30
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster stats per node
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_nodes/stats/indices/search" $ES_EXTRA | oafp out=ctree
```
---

##### 31
### 📖 ElasticSearch | Cluster
Get an overview of an ElasticSearch/OpenSearch cluster health
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/health?format=json" $ES_EXTRA | oafp out=ctable
```
---

##### 32
### 📖 ElasticSearch | Indices
Get an ElasticSearch/OpenSearch count per index
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/kibana_sample_data_flights/_count" $ES_EXTRA | oafp
```
---

##### 33
### 📖 ElasticSearch | Indices
Get an ElasticSearch/OpenSearch indices overview
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/indices?format=json&bytes=b" $ES_EXTRA | oafp sql="select * order by index" out=ctable
```
---

##### 34
### 📖 ElasticSearch | Indices
Get an ElasticSearch/OpenSearch settings for a specific index
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/kibana_sample_data_flights/_settings" $ES_EXTRA | oafp out=ctree
```
---

##### 35
### 📖 Generic | Arrays
Converting an array of strings into an array of maps
```bash
oafp -v path="java.params[].insert(from_json('{}'), 'param', @).insert(@, 'len', length(param))"
```
---

##### 36
### 📖 Generic | Excel
Building an Excel file with the AWS IPv4 and IPv6 ranges (1).
```bash
curl https://ip-ranges.amazonaws.com/ip-ranges.json > ip-ranges.json
```
---

##### 37
### 📖 Generic | Excel
Building an Excel file with the AWS IPv4 and IPv6 ranges (2).
```bash
oafp ip-ranges.json path=prefixes out=xls xlsfile=aws-ip-ranges.xlsx xlssheet=ipv4
```
---

##### 38
### 📖 Generic | Excel
Building an Excel file with the AWS IPv4 and IPv6 ranges (3).
```bash
oafp ip-ranges.json path=ipv6_prefixes out=xls xlsfile=aws-ip-ranges.xlsx xlssheet=ipv6
```
---

##### 39
### 📖 Generic | Excel
Processes each json file in /some/data creating and updating the data.xlsx file with a sheet for each file.
```bash
find /some/data -name "*.json" | xargs -I '{}' /bin/sh -c 'oafp file={} output=xls xlsfile=data.xlsx xlsopen=false xlssheet=$(echo {} | sed "s/.*\/\(.*\)\.json/\1/g" )'
```
---

##### 40
### 📖 Generic | Excel
Store and retrieve data from an Excel spreadsheet
```bash
# Storing data
oafp cmd="oaf -c \"sprint(listFilesRecursive('/usr/bin'))\"" out=xls xlsfile=data.xlsx
# Retrieve data
oafp in=xls file=data.xlsx xlscol=A xlsrow=1 out=pjson
```
---

##### 41
### 📖 Generic | Hex
Outputs an hexadecimal representation of the characters of the file provided allowing to adjust how many per line/row.
```bash
oafp some.file in=rawhex inrawhexline=15 out=ctable
```
---

##### 42
### 📖 Generic | RSS
Builds an HTML file with the current linked news titles, publication date and source from Google News.
```bash
oafp url="https://news.google.com/rss" path="rss.channel.item[].{title:replace(t(@,'[{{title}}]({{link}})'),'\|','g','\\|'),date:pubDate,source:source._}" from="sort(-date)" out=mdtable | oafp in=md out=html
```
---

##### 43
### 📖 Generic | RSS
Example of generating a HTML list of titles, links and publication dates from a RSS feed
```bash
oafp url="https://blog.google/rss" path="rss.channel.item" sql="select title, link, pubDate" output=html
```
---

##### 44
### 📖 Generic | Text
Get a json with lyrics of a song.
```bash
curl -s https://api.lyrics.ovh/v1/Coldplay/Viva%20La%20Vida | oafp path="substring(lyrics,index_of(lyrics, '\n'),length(lyrics))"
```
---

##### 45
### 📖 GitHub | Releases
Builds a table of GitHub project releases
```bash
curl -s https://api.github.com/repos/openaf/openaf/releases | oafp sql="select name, tag_name, published_at order by published_at" output=ctable
```
---

##### 46
### 📖 GitHub | Releases
Parses the latest GitHub project release markdown notes
```bash
curl -s https://api.github.com/repos/openaf/openaf/releases | oafp path="[0].body" output=md
```
---

##### 47
### 📖 Grid | Java
Parse a Java stacktrace into a looping grid.
```bash
HSPERF=/tmp/hsperfdata_user/12345 && oafp $HSPERF in=hsperf path=java out=grid grid="[[(title:Threads,type:chart,obj:'int threads.live:green:live threads.livePeak:red:peak threads.daemon:blue:daemon -min:0')|(title:Class Loaders,type:chart,obj:'int cls.loadedClasses:blue:loaded cls.unloadedClasses:red:unloaded')]|[(title:Heap,type:chart,obj:'bytes __mem.total:red:total __mem.used:blue:used -min:0')|(title:Metaspace,type:chart,obj:'bytes __mem.metaTotal:blue:total __mem.metaUsed:green:used -min:0')]]" loop=1
```
---

##### 48
### 📖 Grid | Kubernetes
Displays a continuous updating grid with a line chart with the number of CPU throtlles and bursts recorded in the Linux cgroup cpu stats of a container running in Kubernetes and the source cpu.stats data
```bash
oafp cmd="cat /sys/fs/cgroup/cpu.stat | sed 's/ /: /g'" in=yaml out=grid grid="[[(title:cpu.stat,type:tree)|(title:chart,type:chart,obj:'int nr_throttled:red:throttled nr_bursts:blue:bursts -min:0 -vsize:10')]]" loop=1
```
---

##### 49
### 📖 Grid | Mac
Shows a grid with the Mac network metrics and 4 charts for in, out packets and in, out bytes
```bash
# opack install mac
sudo powermetrics --help > /dev/null
oafp libs=Mac cmd="sudo powermetrics --format=plist --show-initial-usage -n 0 --samplers network" in=plist path=network out=grid grid="[[(title:data,path:@,xsnap:2)]|[(title:in packets,type:chart,obj:'int ipackets:blue:in')|(title:out packets,type:chart,obj:'int opackets:red:out')]|[(title:in bytes,type:chart,obj:'int ibytes:blue:in')|(title:out bytes,type:chart,obj:'int obytes:red:out')]]" loop=1
```
---

##### 50
### 📖 Grid | Mac
Shows a grid with the Mac storage metrics and 4 charts for read, write IOPS and read, write bytes per second
```bash
# opack install mac
sudo powermetrics --help > /dev/null
oafp libs=Mac cmd="sudo powermetrics --format=plist --show-initial-usage -n 0 --samplers disk" in=plist path=disk out=grid grid="[[(title:data,path:@,xsnap:2)]|[(title:read iops,type:chart,obj:'dec3 rops_per_s:blue:read_iops')|(title:write iops,type:chart,obj:'dec3 wops_per_s:red:write_iops')]|[(title:read bytes per sec,type:chart,obj:'bytes rbytes_per_s:blue:read_bytes_per_sec')|(title:write bytes per sec,type:chart,obj:'bytes wbytes_per_s:red:write_bytes_per_sec')]]" loop=1
```
---

##### 51
### 📖 Grid | Unix
On an Unix/Linux system supporting &#x27;ps&#x27; output formats %cpu and %mem, will output a chart with the percentage of cpu and memory usage of a provided pid (e.g. 12345)
```bash
oafp cmd="ps -p 12345 -o %cpu,%mem" in=lines linesvisual=true linesvisualsepre="\\s+" out=chart chart="int '\"%CPU\"':red:cpu '\"%MEM\"':blue:mem -min:0 -max:100" loop=1 loopcls=true
```
---

##### 52
### 📖 JSON Schemas | Lists
Get a list of JSON schemas from Schema Store catalog
```bash
oafp cmd="curl https://raw.githubusercontent.com/SchemaStore/schemastore/master/src/api/json/catalog.json" path="schemas[].{name:name,description:description,files:to_string(fileMatch)}" out=ctable
```
---

##### 53
### 📖 Kubernetes | Containers
Parse the Linux cgroup cpu stats on a container running in Kubernetes
```bash
cat /sys/fs/cgroup/cpu.stat | sed 's/ /: /g' | oafp in=yaml out=ctree
```
---

##### 54
### 📖 Kubernetes | Kubectl
Build an output table with Kubernetes pods with namespace, pod name, container name and corresponding resources using kubectl
```bash
kubectl get pods -A -o json | oafp path="items[].amerge({ ns: metadata.namespace, pod: metadata.name, phase: status.phase }, spec.containers[].{ container: name, resources: to_slon(resources) })[]" sql="select ns, pod, container, phase, resources order by ns, pod, container" out=ctable
```
---

##### 55
### 📖 Kubernetes | Kubectl
Build an output table with Kubernetes pods with node, namespace, pod name, container name and corresponding resources using kubectl
```bash
kubectl get pods -A -o json | oafp path="items[].amerge({ node: spec.nodeName, ns: metadata.namespace, pod: metadata.name, phase: status.phase }, spec.containers[].{ container: name, resources: to_slon(resources) })[]" sql="select node, ns, pod, container, phase, resources order by node, ns, pod, container" out=ctable
```
---

##### 56
### 📖 Kubernetes | Kubectl
List of Kubernetes CPU, memory and storage stats per node using kubectl
```bash
oafp cmd="kubectl get nodes -o json" path="items[].{node:metadata.name,totalCPU:status.capacity.cpu,allocCPU:status.allocatable.cpu,totalMem:to_bytesAbbr(from_bytesAbbr(status.capacity.memory)),allocMem:to_bytesAbbr(from_bytesAbbr(status.allocatable.memory)),totalStorage:to_bytesAbbr(from_bytesAbbr(status.capacity.\"ephemeral-storage\")),allocStorage:to_bytesAbbr(to_number(status.allocatable.\"ephemeral-storage\")),conditions:join(\`, \`,status.conditions[].reason)}" output=ctable
```
---

##### 57
### 📖 Kubernetes | Kubectl
List of Kubernetes pods per namespace and kind using kubectl
```bash
oafp cmd="kubectl get pods -A -o json" path="items[].{ns:metadata.namespace,kind:metadata.ownerReferences[].kind,name:metadata.name,status:status.phase,restarts:sum(status.containerStatuses[].restartCount),node:spec.nodeName,age:timeago(status.startTime)}" sql="select * order by status,name" output=ctable
```
---

##### 58
### 📖 Mac | Activity
Uses the Mac terminal command &#x27;last&#x27; output to build an activity table with user, tty, from, login-time and logout-time
```bash
oafp cmd="last --libxo json" path="\"last-information\".last" out=ctable
```
---

##### 59
### 📖 Mac | Brew
List all the packages and corresponding versions installed in a Mac by brew.
```bash
brew list --versions | oafp in=lines linesjoin=true path="[].split(@,' ').{package:[0],version:[1]}|sort_by(@,&package)" out=ctable
```
---

##### 60
### 📖 Mac | Info
Parses the current Mac OS overview information
```bash
system_profiler SPSoftwareDataType -json | oafp path="SPSoftwareDataType[0]" out=ctree
```
---

##### 61
### 📖 Mac | Safari
Get a list of all Mac OS Safari bookmarks into a CSV file.
```bash
# opack install mac
oafp ~/Library/Safari/Bookmarks.plist libs=Mac path="Children[].map(&{category:get('cat'),title:URIDictionary.title,url:URLString},setp(@,'Title','cat').nvl(Children,from_json('[]')))[][]" out=csv > bookmarks.csv
```
---

##### 62
### 📖 OpenAF | Channels
Copy the json result of a command into an etcd database using OpenAF&#x27;s channels
```bash
oaf -c "\$o(io.listFiles('.').files,{__format:'json'})" | oafp out=ch ch="(type: etcd3, options: (host: localhost, port: 2379), lib: 'etcd3.js')" chkey=canonicalPath
```
---

##### 63
### 📖 OpenAF | Channels
Getting all data stored in an etcd database using OpenAF&#x27;s channels
```bash
echo "" | oafp in=ch inch="(type: etcd3, options: (host: localhost, port: 2379), lib: 'etcd3.js')" out=ctable
```
---

##### 64
### 📖 OpenAF | Channels
Perform a query to a metric &amp; label, with a start and end time, to a Prometheus server using OpenAF&#x27;s channels
```bash
oafp in=ch inch="(type:prometheus,options:(urlQuery:'http://prometheus.local'))" inchall=true data="(start:'2024-03-22T19:00:00.000Z',end:'2024-03-22T19:05:00.000Z',step:60,query:go_memstats_alloc_bytes_total{job=\"prometheus\"})" path="[].values[].{date:to_date(mul([0],to_number('1000'))),value:[1]}" out=ctable
```
---

##### 65
### 📖 OpenAF | Channels
Retrieve all keys stores in a H2 MVStore file using OpenAF&#x27;s channels
```bash
echo "" | oafp in=ch inch="(type: mvs, options: (file: data.db))" out=ctable
```
---

##### 66
### 📖 OpenAF | Channels
Store and retrieve data from a Redis database
```bash
# Install rocksdb opack: 'opack install redis'
#
# Storing data
oafp cmd="oaf -c \"sprint(listFilesRecursive('/usr/bin'))\"" out=ch ch="(type: redis, lib: redis.js, options: (host: '127.0.0.1', port: 6379))" chkey=canonicalPath
# Retrieve data
echo "" | oafp in=ch inch="(type: redis, lib: redis.js, options: (host: '127.0.0.1', port: 6379))" out=pjson
```
---

##### 67
### 📖 OpenAF | Channels
Store and retrieve data from a RocksDB database
```bash
# Install rocksdb opack: 'opack install rocksdb'
#
# Storing data
oafp cmd="oaf -c \"sprint(listFilesRecursive('/usr/bin'))\"" out=ch ch="(type: rocksdb, lib: rocksdb.js, options: (path: db))" chkey=canonicalPath
# Retrieve data
echo "" | oafp in=ch inch="(type: rocksdb, lib: rocksdb.js, options: (path: db))" out=pjson
```
---

##### 68
### 📖 OpenAF | Channels
Store the json results of a command into a H2 MVStore file using OpenAF&#x27;s channels
```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=ch ch="(type: mvs, options: (file: data.db))" chkey=canonicalPath
```
---

##### 69
### 📖 OpenAF | Network
List all MX (mail servers) network addresses from the current DNS server for a hostname using OpenAF
```bash
DOMAIN=gmail.com && TYPE=MX && oaf -c "sprint(ow.loadNet().getDNS('$DOMAIN','$TYPE'))" | oafp from="sort(Address)" out=ctable
```
---

##### 70
### 📖 OpenAF | Network
List all network addresses returned from the current DNS server for a hostname using OpenAF
```bash
DOMAIN=yahoo.com && oaf -c "sprint(ow.loadNet().getDNS('$DOMAIN'))" | oafp from="sort(Address)" out=ctable
```
---

##### 71
### 📖 OpenAF | OS
Current OS information visible to OpenAF
```bash
oafp -v path=os
```
---

##### 72
### 📖 OpenAF | OS
Using OpenAF parse the current environment variables
```bash
oaf -c "sprint(getEnvs())" | oafp sortmapkeys=true out=ctree
```
---

##### 73
### 📖 OpenAF | TLS
List the TLS certificates of a target host with a sorted alternative names using OpenAF
```bash
DOMAIN=yahoo.com && oaf -c "sprint(ow.loadNet().getTLSCertificates('$DOMAIN',443))" | oafp path="[].{issuer:issuerDN,subject:subjectDN,notBefore:notBefore,notAfter:notAfter,alternatives:join(' | ',sort(map(&[1],nvl(alternatives,\`[]\`))))}" out=ctree
```
---

##### 74
### 📖 OpenAF | oPacks
Listing all currently accessible OpenAF&#x27;s oPacks
```bash
oaf -c "sprint(getOPackRemoteDB())" | oafp maptoarray=true opath="[].{name:name,description:description,version:version}" from="sort(name)" out=ctable
```
---

##### 75
### 📖 OpenAF | oafp
Filter the OpenAF&#x27;s oafp examples list by a specific word in the description
```bash
oafp url="https://ojob.io/oafp-examples.yaml" in=yaml out=template path=data templatepath=tmpl sql="select * where d like '%something%'"
```
---

##### 76
### 📖 OpenAF | oafp
List the OpenAF&#x27;s oafp examples by category, sub-category and description
```bash
oafp url="https://ojob.io/oafp-examples.yaml" in=yaml path="data[].{category:c,subCategory:s,description:d}" from="sort(category,subCategory,description)" out=ctable
```
---

##### 77
### 📖 Unix | Activity
Uses the Linux command &#x27;last&#x27; output to build a table with user, tty, from and period of activity
```bash
oafp cmd="last" in=lines linesjoin=true path="[:-3]|[?contains(@,'no logout')==\`false\`&&contains(@,'system boot')==\`false\`].split_re(@,' \\s+').{user:[0],tty:[1],from:[2],period:join(' ',[3:])}" out=ctable
```
---

##### 78
### 📖 Unix | Alpine
List all installed packages in an Alpine system
```bash
apk list -I | oafp in=lines linesjoin=true path="[].replace(@,'(.+) (.+) {(.+)} \((.+)\) \[(.+)\]','','\$1|\$2|\$3|\$4').split(@,'|').{package:[0],arch:[1],source:[2],license:[3]}" out=ctable
```
---

##### 79
### 📖 Unix | Compute
Parses the Linux /proc/cpuinfo into an array
```bash
cat /proc/cpuinfo | sed "s/^$/---/mg" | ./oafp in=yaml path="[?not_null(@)]" out=ctree
```
---

##### 80
### 📖 Unix | Debian/Ubuntu
List all installed packages in a Debian/Ubuntu system
```bash
apt list --installed | sed "1d" | oafp in=lines linesjoin=true path="[].split(@,' ').{pack:split([0],'/')[0],version:[1],arch:[2]}" out=ctable
```
---

##### 81
### 📖 Unix | Files
Converting the Linux&#x27;s /etc/os-release to SQL insert statements.
```bash
oafp cmd="cat /etc/os-release" in=ini outkey=release path="[@]" sql="select '$HOSTNAME' \"HOST\", *" out=sql sqlnocreate=true
```
---

##### 82
### 📖 Unix | Files
Converting the Unix&#x27;s syslog into a json output.
```bash
cat syslog | oafp in=raw path="split(trim(@),'\n').map(&split(@, ' ').{ date: concat([0],concat(' ',[1])), time: [2], host: [3], process: [4], message: join(' ',[5:]) }, [])"
```
---

##### 83
### 📖 Unix | Files
Parses the Linux /etc/passwd to a table order by uid and gid.
```bash
oafp cmd="cat /etc/passwd" in=csv inputcsv="(withHeader: false, withDelimiter: ':')" path="[].{user:f0,pass:f1,uid:to_number(f2),gid:to_number(f3),description:f4,home:f5,shell:f6}" out=json | oafp from="notStarts(user, '#').sort(uid, gid)" out=ctable
```
---

##### 84
### 📖 Unix | Generic
Creates, in unix, a data.ndjson file where each record is formatted from json files in /some/data
```bash
find /some/data -name "*.json" -exec oafp {} output=json \; > data.ndjson
```
---

##### 85
### 📖 Unix | Network
Loop over the current Linux active network connections
```bash
oafp cmd="netstat -tun | sed \"1d\"" in=lines linesvisual=true linesjoin=true linesvisualsepre="\\s+(\\?\!Address)" out=ctable loop=1
```
---

##### 86
### 📖 Unix | Network
Parse the Linux &#x27;arp&#x27; command output
```bash
arp | oafp in=lines linesvisual=true linesjoin=true out=ctable
```
---

##### 87
### 📖 Unix | Network
Parse the Linux &#x27;ip tcp_metrics&#x27; command
```bash
ip tcp_metrics | sed 's/^/target: /g' | sed 's/$/\n\n---\n/g' | sed 's/ \([a-z]*\) /\n\1: /g' | head -n -2 | oafp in=yaml path="[].{target:target,age:from_timeAbbr(replace(age,'[sec|\.]','','')),cwnd:cwnd,rtt:from_timeAbbr(rtt),rttvar:from_timeAbbr(rttvar),source:source}" sql="select * order by target" out=ctable
```
---

##### 88
### 📖 Unix | Network
Parse the result of the Linux route command
```bash
route | sed "1d" | oafp in=lines linesjoin=true linesvisual=true linesvisualsepre="\s+" out=ctable
```
---

##### 89
### 📖 Unix | OpenSuse
List all installed packages in an OpenSuse system or zypper based system
```bash
zypper se -is | egrep "^i" | oafp in=lines linesjoin=true path="[].split(@,'|').{name:[1],version:[2],arch:[3],repo:[4]}" out=ctable
```
---

##### 90
### 📖 Unix | RedHat
List all installed packages in a RedHat system or rpm based system (use rpm --querytags to list all fields available)
```bash
rpm -qa --qf "%{NAME}|%{VERSION}|%{PACKAGER}|%{VENDOR}|%{ARCH}\n" | oafp in=lines linesjoin=true path="[].split(@,'|').{package:[0],version:[1],packager:[2],vendor:[3],arch:[4]}" from="sort(package)" out=ctable
```
---

##### 91
### 📖 Unix | Storage
Converting the Unix&#x27;s df output
```bash
df --output=target,fstype,size,used,avail,pcent | tail -n +2 | oafp in=lines linesjoin=true path="[].split_re(@, ' +').{filesystem:[0],type:[1],size:[2],used:[3],available:[4],use:[5]}" out=ctable
```
---

##### 92
### 📖 Unix | Storage
Parses the result of the Unix ls command
```bash
ls -lad --time-style="+%Y-%m-%d %H:%M" * | oafp in=lines path="map(&split_re(@,'\\s+').{permissions:[0],id:[1],user:[2],group:[3],size:[4],date:[5],time:[6],file:[7]},[])" linesjoin=true out=ctable
```
---

##### 93
### 📖 Unix | SystemCtl
Converting the Unix&#x27;s systemctl list-timers
```bash
systemctl list-timers | head -n -3 | oafp in=lines linesvisual=true linesjoin=true out=ctable
```
---

##### 94
### 📖 Unix | SystemCtl
Converting the Unix&#x27;s systemctl list-units
```bash
systemctl list-units | head -n -6 | oafp in=lines linesvisual=true linesjoin=true path="[].delete(@,'')" out=ctable
```
---

##### 95
### 📖 Unix | SystemCtl
Converting the Unix&#x27;s systemctl list-units into an overview table
```bash
systemctl list-units | head -n -6 | oafp in=lines linesvisual=true linesjoin=true path="[].delete(@,'')" sql="select \"LOAD\", \"ACTIVE SUB\", count(1) as \"COUNT\" group by \"LOAD\", \"ACTIVE SUB\"" sqlfilter=advanced out=ctable
```
---

##### 96
### 📖 Unix | UBI
List all installed packages in an UBI system
```bash
microdnf repoquery --setopt=cachedir=/tmp --installed | oafp in=lines linesjoin=true path="[].replace(@,'(.+)\.(\w+)\.(\w+)\$','','\$1|\$2|\$3').split(@,'|').{package:[0],dist:[1],arch:[2]}" out=ctable
```
---

##### 97
### 📖 Unix | named
Converts a Linux&#x27;s named log, for client queries, into a CSV
```bash
cat named.log | oafp in=lines linesjoin=true path="[?contains(@,' client ')==\`true\`].split(@,' ').{datetime:to_datef(concat([0],concat(' ',[1])),'dd-MMM-yyyy HH:mm:ss.SSS'),session:[3],sourceIP:replace([4],'(.+)#(\d+)','','\$1'),sourcePort:replace([4],'(.+)#(\d+)','','\$2'),target:replace([5],'\((.+)\):','','\$1'),query:join(' ',[6:])}" out=csv
```
---

##### 98
### 📖 Windows | Network
Output a table with the current route table using Windows&#x27; PowerShell
```bash
Get-NetRoute | ConvertTo-Json | .\oafp.bat path="[].{destination:DestinationPrefix,gateway:NextHop,interface:InterfaceAlias,metric:InterfaceMetric}" sql=select\ *\ order\ by\ interface,destination out=ctable
```
---

##### 99
### 📖 Windows | Network
Output a table with the list of network interfaces using Windows&#x27; PowerShell
```bash
Get-NetIPAddress | ConvertTo-Json | .\oafp.bat path="[].{ipAddress:IPAddress,prefixLen:PrefixLength,interface:InterfaceAlias}" sql=select\ *\ order\ by\ interface out=ctable
```
---

##### 100
### 📖 Windows | PnP
Output a table with USB/PnP devices using Windows&#x27; PowerShell
```bash
Get-PnpDevice -PresentOnly | ConvertTo-Csv -NoTypeInformation | .\oafp.bat in=csv path="[].{class:PNPClass,service:Service,name:FriendlyName,id:InstanceId,description:Description,deviceId:DeviceID,status:Status,present:Present}" sql=select\ *\ order\ by\ class,service out=ctable
```
---

##### 101
### 📖 Windows | Storage
Output a table with the attached disk information using Windows&#x27; PowerShell
```bash
Get-Disk | ConvertTo-Csv -NoTypeInformation | .\oafp.bat in=csv path="[].{id:trim(UniqueId),name:FriendlyName,isBoot:IsBoot,location:Location,size:to_bytesAbbr(to_number(Size)),allocSize:to_bytesAbbr(to_number(AllocatedSize)),sectorSize:LogicalSectorSize,phySectorSize:PhysicalSectorSize,numPartitions:NumberOfPartitions,partitioning:PartitionStyle,health:HealthStatus,bus:BusType,manufacturer:Manufacturer,model:Model,firmwareVersion:FirmwareVersion,serialNumber:SerialNumber}" out=ctable
```

