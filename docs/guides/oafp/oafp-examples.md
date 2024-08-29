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
| AI | Classification | [1](#1) | Given a list of news titles with corresponding dates and sources add a category and sub-category field to each |
| AI | Conversation | [2](#2) | Send multiple requests to an OpenAI model keeping the conversation between interactions and setting the temperature parameter |
| AI | Generate data | [3](#3) | Generates synthetic data using a LLM model and then uses the recorded conversation to generate more data respecting the provided instructions |
| AI | Groq | [4](#4) | Calculation |
| AI | Mistral | [5](#5) | List all available LLM models at mistral.ai |
| AI | Ollama | [6](#6) | Setting up access to Ollama and ask for data to an AI LLM model |
| AI | OpenAI | [7](#7) | Setting up the OpenAI LLM model and gather the data into a data.json file |
| AI | Prompt | [8](#8) | Example of generating data from an AI LLM prompt |
| AI | Summarize | [9](#9) | Use an AI LLM model to summarize the weather information provided in a JSON format |
| AI | TogetherAI | [10](#10) | List all available LLM models at together.ai with their corresponding type and price components order by the more expensive, for input and output |
| APIs | NASA | [11](#11) | Markdown table of near Earth objects by name, magnitude, if is potentially hazardous asteroids and corresponding distance |
| APIs | Network | [12](#12) | Converting the Cloudflare DNS trace info |
| APIs | Network | [13](#13) | Converting the Google DNS DoH query result |
| APIs | Network | [14](#14) | Generating a simple map of the current public IP address |
| APIs | Public Holidays | [15](#15) | Return the public holidays for a given country on a given year |
| APIs | Space | [16](#16) | How many people are in space and in which craft currently in space |
| APIs | iTunes | [17](#17) | Search the Apple&#x27;s iTunes database for a specific term |
| AWS | EC2 | [18](#18) | Given all AWS EC2 instances in an account produces a table with name, type, vpc and private ip sorted by vpc |
| AWS | EKS | [19](#19) | Builds an excel spreadsheet with all persistent volumes associated with an AWS EKS &#x27;XYZ&#x27; with the corresponding Kubernetes namespace, pvc and pv names |
| AWS | Lambda | [20](#20) | Prepares a table of AWS Lambda functions with their corresponding main details |
| AWS | Lambda | [21](#21) | Prepares a table, for a specific AWS Lambda function during a specific time periods, with number of invocations and minimum, average and maximum duration per periods from AWS CloudWatch |
| Azure | Bing | [22](#22) | Given an Azure Bing Search API key and a query returns the corresponding search result from Bing. |
| Chart | Unix | [23](#23) | Output a chart with the current Unix load using uptime |
| DB | H2 | [24](#24) | Perform a SQL query over a H2 database. |
| DB | H2 | [25](#25) | Store the json result of a command into a H2 database table. |
| DB | SQLite | [26](#26) | Perform a query over a database using JDBC. |
| DB | SQLite | [27](#27) | Store the json result on a SQLite database table. |
| Diff | Envs | [28](#28) | Given two JSON files with environment variables performs a diff and returns a colored result with the corresponding differences |
| Diff | Lines | [29](#29) | Performing a diff between two long command lines to spot differences |
| Diff | Path | [30](#30) | Given two JSON files with the parsed PATH environment variable performs a diff and returns a colored result with the corresponding differences |
| Docker | Containers | [31](#31) | Output a table with the list of running containers. |
| Docker | Listing | [32](#32) | List all containers with the docker-compose project, service name, file, id, name, image, creation time, status, networks and ports. |
| Docker | Listing | [33](#33) | List all containers with their corresponding labels parsed and sorted. |
| Docker | Network | [34](#34) | Output a table with the docker networks info. |
| Docker | Registry | [35](#35) | List all a table of docker container images repository and corresponding tags of a private registry. |
| Docker | Registry | [36](#36) | List all the docker container image repositories of a private registry. |
| Docker | Registry | [37](#37) | List all the docker container image repository tags of a private registry. |
| Docker | Stats | [38](#38) | Output a table with the docker stats broken down for each value. |
| Docker | Storage | [39](#39) | Output a table with the docker volumes info. |
| ElasticSearch | Cluster | [40](#40) | Get an ElasticSearch/OpenSearch cluster nodes overview |
| ElasticSearch | Cluster | [41](#41) | Get an ElasticSearch/OpenSearch cluster per host data allocation |
| ElasticSearch | Cluster | [42](#42) | Get an ElasticSearch/OpenSearch cluster settings flat |
| ElasticSearch | Cluster | [43](#43) | Get an ElasticSearch/OpenSearch cluster settings non-flatted |
| ElasticSearch | Cluster | [44](#44) | Get an ElasticSearch/OpenSearch cluster stats per node |
| ElasticSearch | Cluster | [45](#45) | Get an overview of an ElasticSearch/OpenSearch cluster health |
| ElasticSearch | Indices | [46](#46) | Get an ElasticSearch/OpenSearch count per index |
| ElasticSearch | Indices | [47](#47) | Get an ElasticSearch/OpenSearch indices overview |
| ElasticSearch | Indices | [48](#48) | Get an ElasticSearch/OpenSearch settings for a specific index |
| Generic | Arrays | [49](#49) | Converting an array of strings into an array of maps |
| Generic | Avro | [50](#50) | Given an Avro data file outputs it&#x27;s corresponding statistics |
| Generic | Avro | [51](#51) | Given an Avro data file outputs the correspoding schema |
| Generic | Avro | [52](#52) | Reads an Avro data file as input |
| Generic | Avro | [53](#53) | Write an Avro data file as an output |
| Generic | Base64 | [54](#54) | Encode/decode data (or text-like files) to/from gzip base64 representation for easier packing and transport. |
| Generic | Excel | [55](#55) | Building an Excel file with the AWS IPv4 and IPv6 ranges (1). |
| Generic | Excel | [56](#56) | Building an Excel file with the AWS IPv4 and IPv6 ranges (2). |
| Generic | Excel | [57](#57) | Building an Excel file with the AWS IPv4 and IPv6 ranges (3). |
| Generic | Excel | [58](#58) | Processes each json file in /some/data creating and updating the data.xlsx file with a sheet for each file. |
| Generic | Excel | [59](#59) | Store and retrieve data from an Excel spreadsheet |
| Generic | HTML | [60](#60) | Generate a HTML with table of emoticons/emojis by category, group, name, unicode and html code. |
| Generic | Hex | [61](#61) | Outputs an hexadecimal representation of the characters of the file provided allowing to adjust how many per line/row. |
| Generic | RSS | [62](#62) | Builds an HTML file with the current linked news titles, publication date and source from Google News RSS. |
| Generic | RSS | [63](#63) | Example of generating a HTML list of titles, links and publication dates from a RSS feed |
| Generic | RSS | [64](#64) | Parses the Slashdot&#x27;s RSS feed news into a quick clickable HTML page in a browser |
| Generic | Template | [65](#65) | Given a meal name will search &#x27;The Meal DB&#x27; site for the corresponding recipe and render a markdown HTML of the corresponding recipe. |
| Generic | Text | [66](#66) | Get a json with lyrics of a song. |
| Generic | Text | [67](#67) | Search a word in the English dictionary returning phonetic, meanings, synonyms, antonyms, etc. |
| GitHub | Releases | [68](#68) | Builds a table of GitHub project releases |
| GitHub | Releases | [69](#69) | Parses the latest GitHub project release markdown notes |
| Grid | Java | [70](#70) | Parses a Java hsperf data + the current rss java process memory into a looping grid. |
| Grid | Java | [71](#71) | Parses a Java hsperf data into a looping grid. |
| Grid | Kubernetes | [72](#72) | Displays a continuous updating grid with a line chart with the number of CPU throtlles and bursts recorded in the Linux cgroup cpu stats of a container running in Kubernetes and the source cpu.stats data |
| Grid | Mac | [73](#73) | Shows a grid with the Mac network metrics and 4 charts for in, out packets and in, out bytes |
| Grid | Mac | [74](#74) | Shows a grid with the Mac storage metrics and 4 charts for read, write IOPS and read, write bytes per second |
| Grid | Unix | [75](#75) | On an Unix/Linux system supporting &#x27;ps&#x27; output formats %cpu and %mem, will output a chart with the percentage of cpu and memory usage of a provided pid (e.g. 12345) |
| JSON Schemas | Lists | [76](#76) | Get a list of JSON schemas from Schema Store catalog |
| Kubernetes | Containers | [77](#77) | Parse the Linux cgroup cpu stats on a container running in Kubernetes |
| Kubernetes | Kubectl | [78](#78) | Build an output table with Kubernetes pods with namespace, pod name, container name and corresponding resources using kubectl |
| Kubernetes | Kubectl | [79](#79) | Build an output table with Kubernetes pods with node, namespace, pod name, container name and corresponding resources using kubectl |
| Kubernetes | Kubectl | [80](#80) | Executes a recursive file list find command in a specific pod, namespace and path converting the result into a table. |
| Kubernetes | Kubectl | [81](#81) | Given the list of all Kubernetes objects will produce a list of objects per namespace, kind, apiVersiom, creation timestamp, name and owner. |
| Kubernetes | Kubectl | [82](#82) | List of Kubernetes CPU, memory and storage stats per node using kubectl |
| Kubernetes | Kubectl | [83](#83) | List of Kubernetes pods per namespace and kind using kubectl |
| Kubernetes | Kubectl | [84](#84) | Produces a list of pods&#x27; containers per namespace with the corresponding images and assigned nodes. |
| Kubernetes | PVC | [85](#85) | Produces a table with all Kubernetes persistent volume claims (PVCs) in use by pods. |
| Mac | Activity | [86](#86) | Uses the Mac terminal command &#x27;last&#x27; output to build an activity table with user, tty, from, login-time and logout-time |
| Mac | Brew | [87](#87) | List all the packages and corresponding versions installed in a Mac by brew. |
| Mac | Info | [88](#88) | Parses the current Mac OS hardware information |
| Mac | Info | [89](#89) | Parses the current Mac OS overview information |
| Mac | Safari | [90](#90) | Get a list of all Mac OS Safari bookmarks into a CSV file. |
| Network | Latency | [91](#91) | Given a host and a port will display a continuously updating line chart with network latency, in ms, between the current device and the target host and port |
| Ollama | List models | [92](#92) | Parses the list of models currently in an Ollama deployment |
| OpenAF | Channels | [93](#93) | Copy the json result of a command into an etcd database using OpenAF&#x27;s channels |
| OpenAF | Channels | [94](#94) | Getting all data stored in an etcd database using OpenAF&#x27;s channels |
| OpenAF | Channels | [95](#95) | Given a Prometheus database will query for a specific metric (go_memstats_alloc_bytes), during a defined period, every 5 seconds (step) will produce a static chart with the corresponding metric values. |
| OpenAF | Channels | [96](#96) | Perform a query to a metric &amp; label, with a start and end time, to a Prometheus server using OpenAF&#x27;s channels |
| OpenAF | Channels | [97](#97) | Retrieve all keys stores in a H2 MVStore file using OpenAF&#x27;s channels |
| OpenAF | Channels | [98](#98) | Store and retrieve data from a Redis database |
| OpenAF | Channels | [99](#99) | Store and retrieve data from a RocksDB database |
| OpenAF | Channels | [100](#100) | Store the json results of a command into a H2 MVStore file using OpenAF&#x27;s channels |
| OpenAF | Network | [101](#101) | List all MX (mail servers) network addresses from the current DNS server for a hostname using OpenAF |
| OpenAF | Network | [102](#102) | List all network addresses returned from the current DNS server for a hostname using OpenAF |
| OpenAF | OS | [103](#103) | Current OS information visible to OpenAF |
| OpenAF | OS | [104](#104) | Using OpenAF parse the current environment variables |
| OpenAF | OpenVPN | [105](#105) | Using OpenAF code to perform a more complex parsing of the OpenVPN status data running on an OpenVPN container (nmaguiar/openvpn) called &#x27;openvpn&#x27; |
| OpenAF | SFTP | [106](#106) | Generates a file list with filepath, size, permissions, create and last modified time from a SFTP connection with user and password |
| OpenAF | SFTP | [107](#107) | Generates a file list with filepath, size, permissions, create and last modified time from a SFTP connection with user, private key and password |
| OpenAF | TLS | [108](#108) | List the TLS certificates of a target host with a sorted alternative names using OpenAF |
| OpenAF | oJob.io | [109](#109) | Parses ojob.io/news results into a clickable news title HMTL page. |
| OpenAF | oJob.io | [110](#110) | Retrieves the list of oJob.io&#x27;s jobs and filters which start by &#x27;ojob.io/news&#x27; to display them in a rectangle |
| OpenAF | oPacks | [111](#111) | Listing all currently accessible OpenAF&#x27;s oPacks |
| OpenAF | oafp | [112](#112) | Filter the OpenAF&#x27;s oafp examples list by a specific word in the description |
| OpenAF | oafp | [113](#113) | List the OpenAF&#x27;s oafp examples by category, sub-category and description |
| OpenVPN | List | [114](#114) | When using the container nmaguiar/openvpn it&#x27;s possible to convert the list of all clients order by expiration/end date |
| Unix | Activity | [115](#115) | Uses the Linux command &#x27;last&#x27; output to build a table with user, tty, from and period of activity |
| Unix | Alpine | [116](#116) | List all installed packages in an Alpine system |
| Unix | Compute | [117](#117) | Parses the Linux /proc/cpuinfo into an array |
| Unix | Debian/Ubuntu | [118](#118) | List all installed packages in a Debian/Ubuntu system |
| Unix | Envs | [119](#119) | Converts the Linux envs command result into a table of environment variables and corresponding values |
| Unix | Files | [120](#120) | Converting the Linux&#x27;s /etc/os-release to SQL insert statements. |
| Unix | Files | [121](#121) | Converting the Unix&#x27;s syslog into a json output. |
| Unix | Files | [122](#122) | Executes a recursive file list find command converting the result into a table. |
| Unix | Files | [123](#123) | Parses the Linux /etc/passwd to a table order by uid and gid. |
| Unix | Generic | [124](#124) | Creates, in unix, a data.ndjson file where each record is formatted from json files in /some/data |
| Unix | Memory map | [125](#125) | Given an Unix process will output a table with process&#x27;s components memory address, size in bytes, permissions and owner |
| Unix | Network | [126](#126) | Loop over the current Linux active network connections |
| Unix | Network | [127](#127) | Parse the Linux &#x27;arp&#x27; command output |
| Unix | Network | [128](#128) | Parse the Linux &#x27;ip tcp_metrics&#x27; command |
| Unix | Network | [129](#129) | Parse the result of the Linux route command |
| Unix | OpenSuse | [130](#130) | List all installed packages in an OpenSuse system or zypper based system |
| Unix | RedHat | [131](#131) | List all installed packages in a RedHat system or rpm based system (use rpm --querytags to list all fields available) |
| Unix | Storage | [132](#132) | Converting the Unix&#x27;s df output |
| Unix | Storage | [133](#133) | Parses the result of the Unix ls command |
| Unix | SystemCtl | [134](#134) | Converting the Unix&#x27;s systemctl list-timers |
| Unix | SystemCtl | [135](#135) | Converting the Unix&#x27;s systemctl list-units |
| Unix | SystemCtl | [136](#136) | Converting the Unix&#x27;s systemctl list-units into an overview table |
| Unix | UBI | [137](#137) | List all installed packages in an UBI system |
| Unix | named | [138](#138) | Converts a Linux&#x27;s named log, for client queries, into a CSV |
| Windows | Network | [139](#139) | Output a table with the current route table using Windows&#x27; PowerShell |
| Windows | Network | [140](#140) | Output a table with the list of network interfaces using Windows&#x27; PowerShell |
| Windows | PnP | [141](#141) | Output a table with USB/PnP devices using Windows&#x27; PowerShell |
| Windows | Storage | [142](#142) | Output a table with the attached disk information using Windows&#x27; PowerShell |

## 📗 Examples

---

##### 1
### 📖 AI | Classification
Given a list of news titles with corresponding dates and sources add a category and sub-category field to each
```bash
export OAFP_MODEL="(type: ollama, model: 'llama3', url: 'http://ollama.local', timeout: 900000, temperature: 0)"
# get 10 news titles
RSS="https://news.google.com/rss" && oafp url="$RSS" path="rss.channel.item[].{title:title,date:pubDate,source:source._}" from="sort(-date)" out=json sql="select * limit 5" > news.json
# add category and sub-category
oafp news.json llmcontext="list a news titles with date and source" llmprompt="keeping the provided title, date and source add a category and sub-category fields to the provided list" out=json > newsCategorized.json
oafp newsCategorized.json getlist=true out=ctable
```
---

##### 2
### 📖 AI | Conversation
Send multiple requests to an OpenAI model keeping the conversation between interactions and setting the temperature parameter
```bash
export OAFP_MODEL="(type: openai, model: 'gpt-3.5-turbo-0125', key: ..., timeout: 900000, temperature: 0)"
echo "List all countries in the european union" | oafp in=llm out=ctree llmconversation=cvst.json
echo "Add the corresponding country capital" | oafp in=llm out=ctree llmconversation=cvst.json
rm cvst.json
```
---

##### 3
### 📖 AI | Generate data
Generates synthetic data using a LLM model and then uses the recorded conversation to generate more data respecting the provided instructions
```bash
export OAFP_MODEL="(type: ollama, model: 'llama3', url: 'https://models.local', timeout: 900000)"
oafp in=llm llmconversation=conversation.json data="Generate #5 synthetic transaction record data with the following attributes: transaction id - a unique alphanumeric code; date - a date in YYYY-MM-DD format; amount - a dollar amount between 10 and 1000; description - a brief description of the transaction" getlist=true out=ndjson > data.ndjson
oafp in=llm llmconversation=conversation.json data="Generate 5 more records" getlist=true out=ndjson >> data.ndjson
oafp data.ndjson ndjsonjoin=true out=ctable sql="select * order by transaction_id"
```
---

##### 4
### 📖 AI | Groq
Calculation
```bash
export OAFP_MODEL="(type: openai, model: 'llama3-70b-8192', key: '...', url: 'https://api.groq.com/openai', timeout: 900000, temperature: 0)"
oafp in=llm data="how much does light take to travel from Tokyo to Osaka in ms; return a 'time_in_ms' and a 'reasoning'"
```
---

##### 5
### 📖 AI | Mistral
List all available LLM models at mistral.ai
```bash
# export OAFP_MODEL="(type: openai, model: 'llama3', url: 'https://api.mistral.ai', key: '...', timeout: 900000, temperature: 0)"
oafp in=llmmodels data="()" path="sort([].id)"
```
---

##### 6
### 📖 AI | Ollama
Setting up access to Ollama and ask for data to an AI LLM model
```bash
export OAFP_MODEL="(type: ollama, model: 'mistral', url: 'https://models.local', timeout: 900000)"
echo "Output a JSON array with 15 cities where each entry has the 'city' name, the estimated population and the corresponding 'country'" | oafp input=llm output=json > data.json
oafp data.json output=ctable sql="select * order by population desc"
```
---

##### 7
### 📖 AI | OpenAI
Setting up the OpenAI LLM model and gather the data into a data.json file
```bash
export OAFP_MODEL="(type: openai, model: gpt-3.5-turbo, key: ..., timeout: 900000)"
echo "list all United Nations secretaries with their corresponding 'name', their mandate 'begin date', their mandate 'end date' and their corresponding secretary 'numeral'" | oafp input=llm output=json > data.json
```
---

##### 8
### 📖 AI | Prompt
Example of generating data from an AI LLM prompt
```bash
export OAFP_MODEL="(type: openai, model: 'gpt-3.5-turbo', key: '...', timeout: 900000)"
oafp in=llm data="produce a list of 25 species of 'flowers' with their english and latin name and the continent where it can be found" out=json > data.json
```
---

##### 9
### 📖 AI | Summarize
Use an AI LLM model to summarize the weather information provided in a JSON format
```bash
export OAFP_MODEL="(type: openai, model: 'gpt-3.5-turbo', key: '...', timeout: 900000)"
oafp url="https://wttr.in?format=j2" llmcontext="current and forecast weather" llmprompt="produce a summary of the current and forecasted weather" out=md
```
---

##### 10
### 📖 AI | TogetherAI
List all available LLM models at together.ai with their corresponding type and price components order by the more expensive, for input and output
```bash
# export OAFP_MODEL="(type: openai, model: 'meta-llama/Meta-Llama-3-70B', url: 'https://api.together.xyz', key: '...', timeout: 9000000, temperature: 0)"
oafp in=llmmodels data="()" path="[].{id:id,name:display_name,type:type,ctxLen:context_length,priceHour:pricing.hourly,priceIn:pricing.input,priceOut:pricing.output,priceBase:pricing.base,priceFineTune:pricing.finetune}" sql="select * order by priceIn desc,priceOut desc" out=ctable
```
---

##### 11
### 📖 APIs | NASA
Markdown table of near Earth objects by name, magnitude, if is potentially hazardous asteroids and corresponding distance
```bash
curl -s "https://api.nasa.gov/neo/rest/v1/feed?API_KEY=DEMO_KEY" | oafp path="near_earth_objects" maptoarray=true output=json | oafp path="[0][].{name:name,magnitude:absolute_magnitude_h,hazardous:is_potentially_hazardous_asteroid,distance:close_approach_data[0].miss_distance.kilometers}" sql="select * order by distance" output=mdtable
```
---

##### 12
### 📖 APIs | Network
Converting the Cloudflare DNS trace info
```bash
curl -s https://1.1.1.1/cdn-cgi/trace | oafp in=ini out=ctree
```
---

##### 13
### 📖 APIs | Network
Converting the Google DNS DoH query result
```bash
DOMAIN=yahoo.com && oafp path=Answer from="sort(data)" out=ctable url="https://8.8.8.8/resolve?name=$DOMAIN&type=a"
```
---

##### 14
### 📖 APIs | Network
Generating a simple map of the current public IP address
```bash
curl -s https://ifconfig.co/json | oafp flatmap=true out=map
```
---

##### 15
### 📖 APIs | Public Holidays
Return the public holidays for a given country on a given year
```bash
COUNTRY=US && YEAR=2024 && oafp url="https://date.nager.at/api/v2/publicholidays/$YEAR/$COUNTRY" path="[].{date:date,localName:localName,name:name}" out=ctable
```
---

##### 16
### 📖 APIs | Space
How many people are in space and in which craft currently in space
```bash
curl -s http://api.open-notify.org/astros.json | oafp path="people" sql="select \"craft\", count(1) \"people\" group by \"craft\"" output=ctable
```
---

##### 17
### 📖 APIs | iTunes
Search the Apple&#x27;s iTunes database for a specific term
```bash
TRM="Mozart" && oafp url="https://itunes.apple.com/search?term=$TRM" out=ctree
```
---

##### 18
### 📖 AWS | EC2
Given all AWS EC2 instances in an account produces a table with name, type, vpc and private ip sorted by vpc
```bash
aws ec2 describe-instances | oafp path="Reservations[].Instances[].{name:join('',Tags[?Key=='Name'].Value),type:InstanceType,vpc:VpcId,ip:PrivateIpAddress} | sort_by(@, &vpc)" output=ctable
```
---

##### 19
### 📖 AWS | EKS
Builds an excel spreadsheet with all persistent volumes associated with an AWS EKS &#x27;XYZ&#x27; with the corresponding Kubernetes namespace, pvc and pv names
```bash
# sudo yum install -y fontconfig
aws ec2 describe-volumes | oafp path="Volumes[?Tags[?Key=='kubernetes.io/cluster/XYZ']|[0].Value=='owned'].{VolumeId:VolumeId,Name:Tags[?Key=='Name']|[0].Value,KubeNS:Tags[?Key=='kubernetes.io/created-for/pvc/namespace']|[0].Value,KubePVC:Tags[?Key=='kubernetes.io/created-for/pvc/name']|[0].Value,KubePV:Tags[?Key=='kubernetes.io/created-for/pv/name']|[0].Value,AZ:AvailabilityZone,Size:Size,Type:VolumeType,CreateTime:CreateTime,State:State,AttachTime:join(',',nvl(Attachments[].AttachTime,from_slon('[]'))[]),InstanceId:join(',',nvl(Attachments[].InstanceId,from_slon('[]'))[])}" from="sort(KubeNS,KubePVC)" out=xls xlsfile=xyz_pvs.xlsx
```
---

##### 20
### 📖 AWS | Lambda
Prepares a table of AWS Lambda functions with their corresponding main details
```bash
aws lambda list-functions | oafp path="Functions[].{Name:FunctionName,Runtime:Runtime,Arch:join(',',Architectures),Role:Role,MemorySize:MemorySize,EphStore:EphemeralStorage.Size,CodeSize:CodeSize,LastModified:LastModified}" from="sort(Name)" out=ctable
```
---

##### 21
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

##### 22
### 📖 Azure | Bing
Given an Azure Bing Search API key and a query returns the corresponding search result from Bing.
```bash
QUERY="OpenAF" && KEY="12345" && curl -X GET "https://api.bing.microsoft.com/v7.0/search?q=$QUERY" -H "Ocp-Apim-Subscription-Key: $KEY" | oafp out=ctree
```
---

##### 23
### 📖 Chart | Unix
Output a chart with the current Unix load using uptime
```bash
oafp cmd="uptime" in=raw path="replace(trim(@), '.+ ([\d\.]+),? ([\d\.]+),? ([\d\.]+)\$', '', '\$1|\$2|\$3').split(@,'|')" out=chart chart="dec2 [0]:green:load -min:0" loop=1 loopcls=true
```
---

##### 24
### 📖 DB | H2
Perform a SQL query over a H2 database.
```bash
echo "select * from \"data\"" | oafp in=db indbjdbc="jdbc:h2:./data" indbuser=sa indbpass=sa out=ctable
```
---

##### 25
### 📖 DB | H2
Store the json result of a command into a H2 database table.
```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=db dbjdbc="jdbc:h2:./data" dbuser=sa dbpass=sa dbtable=data
```
---

##### 26
### 📖 DB | SQLite
Perform a query over a database using JDBC.
```bash
ojob ojob.io/db/getDriver op=install db=sqlite
echo "select * from data" | oafp in=db indbjdbc="jdbc:sqlite:data.db" indbtable=data indblib=sqlite out=ctable
```
---

##### 27
### 📖 DB | SQLite
Store the json result on a SQLite database table.
```bash
ojob ojob.io/db/getDriver op=install db=sqlite
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=db dbjdbc="jdbc:sqlite:data.db" dbtable=data dblib=sqlite
```
---

##### 28
### 📖 Diff | Envs
Given two JSON files with environment variables performs a diff and returns a colored result with the corresponding differences
```bash
env | oafp in=ini out=json > data1.json
# change one or more environment variables
env | oafp in=ini out=json > data2.json
oafp in=oafp data="[(file: data1.json)|(file: data2.json)]" diff="(a:'[0]',b:'[1]')" color=true
```
---

##### 29
### 📖 Diff | Lines
Performing a diff between two long command lines to spot differences
```bash
oafp diff="(a:before,b:after)" diffchars=true in=yaml color=true
# as stdin enter
before: URL="http://localhost:9090" && METRIC="go_memstats_alloc_bytes" && TYPE="bytes" && LABELS="job=\"prometheus\"" && START="2024-06-18T20:00:00Z" && END="2024-06-18T20:15:00Z" && STEP=5 && echo "{query:'max($METRIC{$LABELS})',start:'$START',end:'$END',step:$STEP}" | oafp in=ch inch="(type:prometheus,options:(urlQuery:'$URL'))" inchall=true out=json | oafp path="[].set(@, 'main').map(&{metric:'$METRIC',job:get('main').metric.job,timestamp:to_date(mul([0],\`1000\`)),value:to_number([1])}, values) | []" out=schart schart="$TYPE '[].value':green:$METRIC -min:0"

after: URL="http://localhost:9090" && METRIC="go_memstats_alloc_bytes" && TYPE="bytes" && LABELS="job=\"prometheus\"" && START="2024-06-18T20:00:00Z" && END="2024-06-18T20:15:00Z" && STEP=5 && echo "{query:'max($METRIC{$LABELS})',start:'$START',end:'$END',step:$STEP}" | oafp in=ch inch="(type:prometheus,options:(urlQuery:'$URL'))" inchall=true out=json | oafp path="[].set(@, 'main').map(&{metric:'$METRIC',job:get('main').metric.job,timestamp:to_date([0]),value:to_number([1])}, values) | []" out=schart schart="$TYPE '[].value':green:$METRIC -min:0"
#
# Ctrl^D 
# as the result the difference between before and after will appear as red characters
```
---

##### 30
### 📖 Diff | Path
Given two JSON files with the parsed PATH environment variable performs a diff and returns a colored result with the corresponding differences
```bash
env | oafp in=ini path="PATH.split(@,':')" out=json > data1.json
# export PATH=$PATH:/some/new/path
env | oafp in=ini path="PATH.split(@,':')" out=json > data2.json
oafp in=oafp data="[(file: data1.json)|(file: data2.json)]" diff="(a:'sort([0])',b:'sort([1])')" color=true
```
---

##### 31
### 📖 Docker | Containers
Output a table with the list of running containers.
```bash
oafp cmd="docker ps --format json" input=ndjson ndjsonjoin=true path="[].{id:ID,name:Names,state:State,image:Image,networks:Networks,ports:Ports,Status:Status}" sql="select * order by networks,state,name" output=ctable
```
---

##### 32
### 📖 Docker | Listing
List all containers with the docker-compose project, service name, file, id, name, image, creation time, status, networks and ports.
```bash
docker ps -a --format=json | oafp in=ndjson ndjsonjoin=true out=ctree path="[].insert(@,'Labels',sort_by(split(Labels,',')[].split(@,'=').{key:[0],value:[1]},&key))" out=json | oafp path="[].{dcProject:nvl(Labels[?key=='com.docker.compose.project']|[0].value,''),dcService:nvl(Labels[?key=='com.docker.compose.service']|[0].value,''),ID:ID,Names:Names,Image:Image,Created:RunningFor,Status:Status,Ports:Ports,Networks:Networks,dcFile:nvl(Labels[?key=='com.docker.compose.project.config_files']|[0].value,'')}" sql="select * order by dcProject,dcService,Networks,Names" out=ctable
```
---

##### 33
### 📖 Docker | Listing
List all containers with their corresponding labels parsed and sorted.
```bash
docker ps -a --format=json | oafp in=ndjson ndjsonjoin=true out=ctree path="[].insert(@,'Labels',sort_by(split(Labels,',')[].split(@,'=').{key:[0],value:[1]},&key))" out=ctree
```
---

##### 34
### 📖 Docker | Network
Output a table with the docker networks info.
```bash
docker network ls --format json | oafp in=ndjson ndjsonjoin=true out=ctable
```
---

##### 35
### 📖 Docker | Registry
List all a table of docker container images repository and corresponding tags of a private registry.
```bash
# opack install DockerRegistry
# check more options with 'oafp libs=dockerregistry help=dockerregistry' 
oafp libs=dockerregistry in=registryrepos data="()" inregistryurl=http://localhost:5000 inregistrytags=true out=ctable
```
---

##### 36
### 📖 Docker | Registry
List all the docker container image repositories of a private registry.
```bash
# opack install DockerRegistry
# check more options with 'oafp libs=dockerregistry help=dockerregistry' 
oafp libs=dockerregistry data="()" in=registryrepos inregistryurl=http://localhost:5000
```
---

##### 37
### 📖 Docker | Registry
List all the docker container image repository tags of a private registry.
```bash
# opack install DockerRegistry
# check more options with 'oafp libs=dockerregistry help=dockerregistry' 
oafp libs=dockerregistry data="library/nginx" in=registrytags inregistryurl=http://localhost:5000
```
---

##### 38
### 📖 Docker | Stats
Output a table with the docker stats broken down for each value.
```bash
oafp cmd="docker stats --no-stream" in=lines linesvisual=true linesjoin=true out=ctree path="[].{containerId:\"CONTAINER ID\",pids:PIDS,name:\"NAME\",cpuPerc:\"CPU %\",memory:\"MEM USAGE / LIMIT\",memPerc:\"MEM %\",netIO:\"NET I/O\",blockIO:\"BLOCK I/O\"}|[].{containerId:containerId,pids:pids,name:name,cpuPerc:replace(cpuPerc,'%','',''),memUsage:from_bytesAbbr(split(memory,' / ')[0]),memLimit:from_bytesAbbr(split(memory,' / ')[1]),memPerc:replace(memPerc,'%','',''),netIn:from_bytesAbbr(split(netIO,' / ')[0]),netOut:from_bytesAbbr(split(netIO,' / ')[1]),blockIn:from_bytesAbbr(split(blockIO,' / ')[0]),blockOut:from_bytesAbbr(split(blockIO,' / ')[1])}" out=ctable
```
---

##### 39
### 📖 Docker | Storage
Output a table with the docker volumes info.
```bash
docker volume ls --format json | oafp in=ndjson ndjsonjoin=true out=ctable
```
---

##### 40
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster nodes overview
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/nodes?format=json" $ES_EXTRA | oafp sql="select * order by ip" out=ctable
```
---

##### 41
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster per host data allocation
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/allocation?format=json&bytes=b" $ES_EXTRA | oafp sql="select * order by host" out=ctable
```
---

##### 42
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster settings flat
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cluster/settings?include_defaults=true&flat_settings=true" $ES_EXTRA | oafp out=ctree
```
---

##### 43
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster settings non-flatted
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cluster/settings?include_defaults=true" $ES_EXTRA | oafp out=ctree
```
---

##### 44
### 📖 ElasticSearch | Cluster
Get an ElasticSearch/OpenSearch cluster stats per node
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_nodes/stats/indices/search" $ES_EXTRA | oafp out=ctree
```
---

##### 45
### 📖 ElasticSearch | Cluster
Get an overview of an ElasticSearch/OpenSearch cluster health
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/health?format=json" $ES_EXTRA | oafp out=ctable
```
---

##### 46
### 📖 ElasticSearch | Indices
Get an ElasticSearch/OpenSearch count per index
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/kibana_sample_data_flights/_count" $ES_EXTRA | oafp
```
---

##### 47
### 📖 ElasticSearch | Indices
Get an ElasticSearch/OpenSearch indices overview
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/_cat/indices?format=json&bytes=b" $ES_EXTRA | oafp sql="select * order by index" out=ctable
```
---

##### 48
### 📖 ElasticSearch | Indices
Get an ElasticSearch/OpenSearch settings for a specific index
```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
curl -s "$ES_URL/kibana_sample_data_flights/_settings" $ES_EXTRA | oafp out=ctree
```
---

##### 49
### 📖 Generic | Arrays
Converting an array of strings into an array of maps
```bash
oafp -v path="java.params[].insert(from_json('{}'), 'param', @).insert(@, 'len', length(param))"
```
---

##### 50
### 📖 Generic | Avro
Given an Avro data file outputs it&#x27;s corresponding statistics
```bash
# opack install avro
oafp libs=avro data.avro inavrostats=true
```
---

##### 51
### 📖 Generic | Avro
Given an Avro data file outputs the correspoding schema
```bash
# opack install avro
oafp libs=avro data.avro inavroschema=true
```
---

##### 52
### 📖 Generic | Avro
Reads an Avro data file as input
```bash
# opack install avro
oafp data.avro libs=avro out=ctable
```
---

##### 53
### 📖 Generic | Avro
Write an Avro data file as an output
```bash
# opack install avro
oafp data.json libs=avro out=avro avrofile=data.avro
```
---

##### 54
### 📖 Generic | Base64
Encode/decode data (or text-like files) to/from gzip base64 representation for easier packing and transport.
```bash
# encode a data file to a gzip base64 representation
oafp data.json out=gb64json > data.gb64
# decode a gzip base64 representation back into a data file
oafp data.gb64 in=gb64json out=json > data.json
```
---

##### 55
### 📖 Generic | Excel
Building an Excel file with the AWS IPv4 and IPv6 ranges (1).
```bash
curl https://ip-ranges.amazonaws.com/ip-ranges.json > ip-ranges.json
```
---

##### 56
### 📖 Generic | Excel
Building an Excel file with the AWS IPv4 and IPv6 ranges (2).
```bash
oafp ip-ranges.json path=prefixes out=xls xlsfile=aws-ip-ranges.xlsx xlssheet=ipv4
```
---

##### 57
### 📖 Generic | Excel
Building an Excel file with the AWS IPv4 and IPv6 ranges (3).
```bash
oafp ip-ranges.json path=ipv6_prefixes out=xls xlsfile=aws-ip-ranges.xlsx xlssheet=ipv6
```
---

##### 58
### 📖 Generic | Excel
Processes each json file in /some/data creating and updating the data.xlsx file with a sheet for each file.
```bash
find /some/data -name "*.json" | xargs -I '{}' /bin/sh -c 'oafp file={} output=xls xlsfile=data.xlsx xlsopen=false xlssheet=$(echo {} | sed "s/.*\/\(.*\)\.json/\1/g" )'
```
---

##### 59
### 📖 Generic | Excel
Store and retrieve data from an Excel spreadsheet
```bash
# Storing data
oafp cmd="oaf -c \"sprint(listFilesRecursive('/usr/bin'))\"" out=xls xlsfile=data.xlsx
# Retrieve data
oafp in=xls file=data.xlsx xlscol=A xlsrow=1 out=pjson
```
---

##### 60
### 📖 Generic | HTML
Generate a HTML with table of emoticons/emojis by category, group, name, unicode and html code.
```bash
oafp url="https://emojihub.yurace.pro/api/all" path="[].{category:category,group:group,name:name,len:length(unicode),unicode:join('<br>',unicode),htmlCode:replace(join('<br>', htmlCode),'&','g','&amp;'),emoji:join('', htmlCode)}" out=mdtable | oafp in=md out=html
```
---

##### 61
### 📖 Generic | Hex
Outputs an hexadecimal representation of the characters of the file provided allowing to adjust how many per line/row.
```bash
oafp some.file in=rawhex inrawhexline=15 out=ctable
```
---

##### 62
### 📖 Generic | RSS
Builds an HTML file with the current linked news titles, publication date and source from Google News RSS.
```bash
RSS="https://news.google.com/rss" && oafp url="$RSS" path="rss.channel.item[].{title:replace(t(@,'[{{title}}]({{link}})'),'\|','g','\\|'),date:pubDate,source:source._}" from="sort(-date)" out=mdtable | oafp in=md out=html
```
---

##### 63
### 📖 Generic | RSS
Example of generating a HTML list of titles, links and publication dates from a RSS feed
```bash
oafp url="https://blog.google/rss" path="rss.channel.item" sql="select title, link, pubDate" output=html
```
---

##### 64
### 📖 Generic | RSS
Parses the Slashdot&#x27;s RSS feed news into a quick clickable HTML page in a browser
```bash
RSS="http://rss.slashdot.org/Slashdot/slashdot" && oafp url="$RSS" path="RDF.item[].{title:replace(t(@,'[{{title}}]({{link}})'),'\|','g','\\|'),department:department,date:date}" from="sort(-date)" out=mdtable | oafp in=md out=html
```
---

##### 65
### 📖 Generic | Template
Given a meal name will search &#x27;The Meal DB&#x27; site for the corresponding recipe and render a markdown HTML of the corresponding recipe.
```bash
MEAL="Pizza" && echo "# {{strMeal}}\n> {{strCategory}} | {{strArea}}\n<a href=\"{{strYoutube}}\"><img align=\"center\" width=1280 src=\"{{strMealThumb}}\"></a>\n\n## Ingredients\n\n| Ingredient | Measure |\n|---|---|\n{{#each ingredients}}|{{ingredient}}|{{measure}}|\n{{/each}}\n\n## Instructions\n\n\n\n{{{strInstructions}}}" > _template.hbs && oafp url="https://www.themealdb.com/api/json/v1/1/search.php?s=$MEAL" path="set(meals[0],'o').set(k2a(get('o'),'strIngredient','i',\`true\`),'is').set(k2a(get('o'),'strMeasure','m',\`true\`),'ms')|get('o').insert(get('o'),'ingredients',ranges(length(get('is')),\`0\`,\`1\`).map(&{ ingredient: geta('is',@).i, measure: geta('ms',@).m }, @))" out=json | oafp out=template template=_template.hbs | oafp in=md out=html htmlcompact=true
```
---

##### 66
### 📖 Generic | Text
Get a json with lyrics of a song.
```bash
curl -s https://api.lyrics.ovh/v1/Coldplay/Viva%20La%20Vida | oafp path="substring(lyrics,index_of(lyrics, '\n'),length(lyrics))"
```
---

##### 67
### 📖 Generic | Text
Search a word in the English dictionary returning phonetic, meanings, synonyms, antonyms, etc.
```bash
WORD="google" && oafp url="https://api.dictionaryapi.dev/api/v2/entries/en/$WORD"
```
---

##### 68
### 📖 GitHub | Releases
Builds a table of GitHub project releases
```bash
curl -s https://api.github.com/repos/openaf/openaf/releases | oafp sql="select name, tag_name, published_at order by published_at" output=ctable
```
---

##### 69
### 📖 GitHub | Releases
Parses the latest GitHub project release markdown notes
```bash
curl -s https://api.github.com/repos/openaf/openaf/releases | oafp path="[0].body" output=md
```
---

##### 70
### 📖 Grid | Java
Parses a Java hsperf data + the current rss java process memory into a looping grid.
```bash
JPID=12345 && HSPERF=/tmp/hsperfdata_openvscode-server/$JPID && oafp in=oafp data="[(file: $HSPERF, in: hsperf, path: java)|(cmd: 'ps -p $JPID -o rss=', path: '{ rss: mul(@,\`1024\`) }')]" merge=true out=grid grid="[[(title:Threads,type:chart,obj:'int threads.live:green:live threads.livePeak:red:peak threads.daemon:blue:daemon -min:0')|(title:RSS,type:chart,obj:'bytes rss:blue:rss')]|[(title:Heap,type:chart,obj:'bytes __mem.total:red:total __mem.used:blue:used -min:0')|(title:Metaspace,type:chart,obj:'bytes __mem.metaTotal:blue:total __mem.metaUsed:green:used -min:0')]]" loop=1
```
---

##### 71
### 📖 Grid | Java
Parses a Java hsperf data into a looping grid.
```bash
HSPERF=/tmp/hsperfdata_user/12345 && oafp $HSPERF in=hsperf path=java out=grid grid="[[(title:Threads,type:chart,obj:'int threads.live:green:live threads.livePeak:red:peak threads.daemon:blue:daemon -min:0')|(title:Class Loaders,type:chart,obj:'int cls.loadedClasses:blue:loaded cls.unloadedClasses:red:unloaded')]|[(title:Heap,type:chart,obj:'bytes __mem.total:red:total __mem.used:blue:used -min:0')|(title:Metaspace,type:chart,obj:'bytes __mem.metaTotal:blue:total __mem.metaUsed:green:used -min:0')]]" loop=1
```
---

##### 72
### 📖 Grid | Kubernetes
Displays a continuous updating grid with a line chart with the number of CPU throtlles and bursts recorded in the Linux cgroup cpu stats of a container running in Kubernetes and the source cpu.stats data
```bash
oafp cmd="cat /sys/fs/cgroup/cpu.stat | sed 's/ /: /g'" in=yaml out=grid grid="[[(title:cpu.stat,type:tree)|(title:chart,type:chart,obj:'int nr_throttled:red:throttled nr_bursts:blue:bursts -min:0 -vsize:10')]]" loop=1
```
---

##### 73
### 📖 Grid | Mac
Shows a grid with the Mac network metrics and 4 charts for in, out packets and in, out bytes
```bash
# opack install mac
sudo powermetrics --help > /dev/null
oafp libs=Mac cmd="sudo powermetrics --format=plist --show-initial-usage -n 0 --samplers network" in=plist path=network out=grid grid="[[(title:data,path:@,xsnap:2)]|[(title:in packets,type:chart,obj:'int ipackets:blue:in')|(title:out packets,type:chart,obj:'int opackets:red:out')]|[(title:in bytes,type:chart,obj:'int ibytes:blue:in')|(title:out bytes,type:chart,obj:'int obytes:red:out')]]" loop=1
```
---

##### 74
### 📖 Grid | Mac
Shows a grid with the Mac storage metrics and 4 charts for read, write IOPS and read, write bytes per second
```bash
# opack install mac
sudo powermetrics --help > /dev/null
oafp libs=Mac cmd="sudo powermetrics --format=plist --show-initial-usage -n 0 --samplers disk" in=plist path=disk out=grid grid="[[(title:data,path:@,xsnap:2)]|[(title:read iops,type:chart,obj:'dec3 rops_per_s:blue:read_iops')|(title:write iops,type:chart,obj:'dec3 wops_per_s:red:write_iops')]|[(title:read bytes per sec,type:chart,obj:'bytes rbytes_per_s:blue:read_bytes_per_sec')|(title:write bytes per sec,type:chart,obj:'bytes wbytes_per_s:red:write_bytes_per_sec')]]" loop=1
```
---

##### 75
### 📖 Grid | Unix
On an Unix/Linux system supporting &#x27;ps&#x27; output formats %cpu and %mem, will output a chart with the percentage of cpu and memory usage of a provided pid (e.g. 12345)
```bash
oafp cmd="ps -p 12345 -o %cpu,%mem" in=lines linesvisual=true linesvisualsepre="\\s+" out=chart chart="int '\"%CPU\"':red:cpu '\"%MEM\"':blue:mem -min:0 -max:100" loop=1 loopcls=true
```
---

##### 76
### 📖 JSON Schemas | Lists
Get a list of JSON schemas from Schema Store catalog
```bash
oafp cmd="curl https://raw.githubusercontent.com/SchemaStore/schemastore/master/src/api/json/catalog.json" path="schemas[].{name:name,description:description,files:to_string(fileMatch)}" out=ctable
```
---

##### 77
### 📖 Kubernetes | Containers
Parse the Linux cgroup cpu stats on a container running in Kubernetes
```bash
cat /sys/fs/cgroup/cpu.stat | sed 's/ /: /g' | oafp in=yaml out=ctree
```
---

##### 78
### 📖 Kubernetes | Kubectl
Build an output table with Kubernetes pods with namespace, pod name, container name and corresponding resources using kubectl
```bash
kubectl get pods -A -o json | oafp path="items[].amerge({ ns: metadata.namespace, pod: metadata.name, phase: status.phase }, spec.containers[].{ container: name, resources: to_slon(resources) })[]" sql="select ns, pod, container, phase, resources order by ns, pod, container" out=ctable
```
---

##### 79
### 📖 Kubernetes | Kubectl
Build an output table with Kubernetes pods with node, namespace, pod name, container name and corresponding resources using kubectl
```bash
kubectl get pods -A -o json | oafp path="items[].amerge({ node: spec.nodeName, ns: metadata.namespace, pod: metadata.name, phase: status.phase }, spec.containers[].{ container: name, resources: to_slon(resources) })[]" sql="select node, ns, pod, container, phase, resources order by node, ns, pod, container" out=ctable
```
---

##### 80
### 📖 Kubernetes | Kubectl
Executes a recursive file list find command in a specific pod, namespace and path converting the result into a table.
```bash
NS=default && POD=my-pod-5c9cfb87d4-r6dlp && LSPATH=/data && kubectl exec -n $NS $POD -- find $LSPATH -exec stat -c '{"t":"%F", "p": "%n", "s": %s, "m": "%Y", "e": "%A", "u": "%U", "g": "%G"}' {} \; | oafp in=ndjson ndjsonjoin=true path="[].{type:t,permissions:e,user:u,group:g,size:s,modifiedDate:to_date(mul(to_number(m),\`1000\`)),filepath:p}" from="sort(type,filepath)" out=ctable
```
---

##### 81
### 📖 Kubernetes | Kubectl
Given the list of all Kubernetes objects will produce a list of objects per namespace, kind, apiVersiom, creation timestamp, name and owner.
```bash
oafp cmd="kubectl get all -A -o json" path="items[].{ns:metadata.namespace,kind:kind,apiVersion:apiVersion,createDate:metadata.creationTimestamp,name:metadata.name,owner:metadata.join(',',map(&concat(kind, concat('/', name)), nvl(ownerReferences,from_json('[]'))))}" sql="select * order by ns, kind, name" out=ctable
```
---

##### 82
### 📖 Kubernetes | Kubectl
List of Kubernetes CPU, memory and storage stats per node using kubectl
```bash
oafp cmd="kubectl get nodes -o json" path="items[].{node:metadata.name,totalCPU:status.capacity.cpu,allocCPU:status.allocatable.cpu,totalMem:to_bytesAbbr(from_bytesAbbr(status.capacity.memory)),allocMem:to_bytesAbbr(from_bytesAbbr(status.allocatable.memory)),totalStorage:to_bytesAbbr(from_bytesAbbr(status.capacity.\"ephemeral-storage\")),allocStorage:to_bytesAbbr(to_number(status.allocatable.\"ephemeral-storage\")),conditions:join(\`, \`,status.conditions[].reason)}" output=ctable
```
---

##### 83
### 📖 Kubernetes | Kubectl
List of Kubernetes pods per namespace and kind using kubectl
```bash
oafp cmd="kubectl get pods -A -o json" path="items[].{ns:metadata.namespace,kind:metadata.ownerReferences[].kind,name:metadata.name,status:status.phase,restarts:sum(nvl(status.containerStatuses[].restartCount,from_slon('[0]'))),node:spec.nodeName,age:timeago(nvl(status.startTime,now(\`0\`)))}" sql="select * order by status,name" output=ctable
```
---

##### 84
### 📖 Kubernetes | Kubectl
Produces a list of pods&#x27; containers per namespace with the corresponding images and assigned nodes.
```bash
kubectl get pods -A -o json | oafp path="items[].amerge({namespace: metadata.namespace, pod: metadata.name, nodeName: spec.nodeName},spec.containers[].{container: name, image: image, pullPolicy: imagePullPolicy})[]" sql="select namespace, pod, container, image, pullPolicy, nodeName order by namespace, pod, container" out=ctable
```
---

##### 85
### 📖 Kubernetes | PVC
Produces a table with all Kubernetes persistent volume claims (PVCs) in use by pods.
```bash
oafp cmd="kubectl get pods -A -o json" path="items[].spec.set(@,'m').volumes[?persistentVolumeClaim].insert(@,'pname',get('m').containers[0].name).insert(@,'node',get('m').nodeName) | [].{pod:pname,node:node,pvc:persistentVolumeClaim.claimName}" from="sort(node,pod)" out=ctable
```
---

##### 86
### 📖 Mac | Activity
Uses the Mac terminal command &#x27;last&#x27; output to build an activity table with user, tty, from, login-time and logout-time
```bash
oafp cmd="last --libxo json" path="\"last-information\".last" out=ctable
```
---

##### 87
### 📖 Mac | Brew
List all the packages and corresponding versions installed in a Mac by brew.
```bash
brew list --versions | oafp in=lines linesjoin=true path="[].split(@,' ').{package:[0],version:[1]}|sort_by(@,&package)" out=ctable
```
---

##### 88
### 📖 Mac | Info
Parses the current Mac OS hardware information
```bash
system_profiler SPHardwareDataType -json | oafp path="SPHardwareDataType[0]" out=ctree
```
---

##### 89
### 📖 Mac | Info
Parses the current Mac OS overview information
```bash
system_profiler SPSoftwareDataType -json | oafp path="SPSoftwareDataType[0]" out=ctree
```
---

##### 90
### 📖 Mac | Safari
Get a list of all Mac OS Safari bookmarks into a CSV file.
```bash
# opack install mac
oafp ~/Library/Safari/Bookmarks.plist libs=Mac path="Children[].map(&{category:get('cat'),title:URIDictionary.title,url:URLString},setp(@,'Title','cat').nvl(Children,from_json('[]')))[][]" out=csv > bookmarks.csv
```
---

##### 91
### 📖 Network | Latency
Given a host and a port will display a continuously updating line chart with network latency, in ms, between the current device and the target host and port
```bash
HOST=1.1.1.1 && PORT=53 && oafp in=oaf data="ow.loadNet().testPortLatency('$HOST',$PORT)" out=chart chart="int @:red:latencyMS -min:0" loop=1 loopcls=true
```
---

##### 92
### 📖 Ollama | List models
Parses the list of models currently in an Ollama deployment
```bash
export OAFP_MODEL="(type: ollama, model: 'llama3', url: 'https://models.local', timeout: 900000)"
oafp in=llmmodels data="()" out=ctable path="[].{name:name,parameters:details.parameter_size,quantization:details.quantization_level,format:details.format,family:details.family,parent:details.parent,size:size}" sql="select * order by parent,family,format,parameters,quantization"
```
---

##### 93
### 📖 OpenAF | Channels
Copy the json result of a command into an etcd database using OpenAF&#x27;s channels
```bash
oaf -c "\$o(io.listFiles('.').files,{__format:'json'})" | oafp out=ch ch="(type: etcd3, options: (host: localhost, port: 2379), lib: 'etcd3.js')" chkey=canonicalPath
```
---

##### 94
### 📖 OpenAF | Channels
Getting all data stored in an etcd database using OpenAF&#x27;s channels
```bash
echo "" | oafp in=ch inch="(type: etcd3, options: (host: localhost, port: 2379), lib: 'etcd3.js')" out=ctable
```
---

##### 95
### 📖 OpenAF | Channels
Given a Prometheus database will query for a specific metric (go_memstats_alloc_bytes), during a defined period, every 5 seconds (step) will produce a static chart with the corresponding metric values.
```bash
URL="http://localhost:9090" && METRIC="go_memstats_alloc_bytes" && TYPE="bytes" && LABELS="job=\"prometheus\"" && START="2024-06-18T20:00:00Z" && END="2024-06-18T20:15:00Z" && STEP=5 && echo "{query:'max($METRIC{$LABELS})',start:'$START',end:'$END',step:$STEP}" | oafp in=ch inch="(type:prometheus,options:(urlQuery:'$URL'))" inchall=true out=json | oafp path="[].set(@, 'main').map(&{metric:'$METRIC',job:get('main').metric.job,timestamp:to_date(mul([0],\`1000\`)),value:to_number([1])}, values) | []" out=schart schart="$TYPE '[].value':green:$METRIC -min:0"
```
---

##### 96
### 📖 OpenAF | Channels
Perform a query to a metric &amp; label, with a start and end time, to a Prometheus server using OpenAF&#x27;s channels
```bash
oafp in=ch inch="(type:prometheus,options:(urlQuery:'http://prometheus.local'))" inchall=true data="(start:'2024-03-22T19:00:00.000Z',end:'2024-03-22T19:05:00.000Z',step:60,query:go_memstats_alloc_bytes_total{job=\"prometheus\"})" path="[].values[].{date:to_date(mul([0],to_number('1000'))),value:[1]}" out=ctable
```
---

##### 97
### 📖 OpenAF | Channels
Retrieve all keys stores in a H2 MVStore file using OpenAF&#x27;s channels
```bash
echo "" | oafp in=ch inch="(type: mvs, options: (file: data.db))" out=ctable
```
---

##### 98
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

##### 99
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

##### 100
### 📖 OpenAF | Channels
Store the json results of a command into a H2 MVStore file using OpenAF&#x27;s channels
```bash
oaf -c "\$o(listFilesRecursive('.'),{__format:'json'})" | oafp out=ch ch="(type: mvs, options: (file: data.db))" chkey=canonicalPath
```
---

##### 101
### 📖 OpenAF | Network
List all MX (mail servers) network addresses from the current DNS server for a hostname using OpenAF
```bash
DOMAIN=gmail.com && TYPE=MX && oaf -c "sprint(ow.loadNet().getDNS('$DOMAIN','$TYPE'))" | oafp from="sort(Address)" out=ctable
```
---

##### 102
### 📖 OpenAF | Network
List all network addresses returned from the current DNS server for a hostname using OpenAF
```bash
DOMAIN=yahoo.com && oaf -c "sprint(ow.loadNet().getDNS('$DOMAIN'))" | oafp from="sort(Address)" out=ctable
```
---

##### 103
### 📖 OpenAF | OS
Current OS information visible to OpenAF
```bash
oafp -v path=os
```
---

##### 104
### 📖 OpenAF | OS
Using OpenAF parse the current environment variables
```bash
oaf -c "sprint(getEnvs())" | oafp sortmapkeys=true out=ctree
```
---

##### 105
### 📖 OpenAF | OpenVPN
Using OpenAF code to perform a more complex parsing of the OpenVPN status data running on an OpenVPN container (nmaguiar/openvpn) called &#x27;openvpn&#x27;
```bash
oafp in=oaf data='(function(){return(b=>{var a=b.split("\n"),c=a.indexOf("ROUTING TABLE"),d=a.indexOf("GLOBAL STATS"),f=a.indexOf("END");b=$csv().fromInString($path(a,`[2:${c}]`).join("\n")).toOutArray();var g=$csv().fromInString($path(a,`[${c+1}:${d}]`).join("\n")).toOutArray();a=$csv().fromInString($path(a,`[${d+1}:${f}]`).join("\n")).toOutArray();return{list:b.map(e=>merge(e,$from(g).equals("Common Name",e["Common Name"]).at(0))),stats:a}})($sh("docker exec openvpn cat /tmp/openvpn-status.log").get(0).stdout)})()' path="list[].{user:\"Common Name\",ip:split(\"Real Address\",':')[0],port:split(\"Real Address\",':')[1],vpnAddress:\"Virtual Address\",bytesRx:to_bytesAbbr(to_number(\"Bytes Received\")),bytesTx:to_bytesAbbr(to_number(\"Bytes Sent\")),connectedSince:to_datef(\"Connected Since\",'yyyy-MM-dd HH:mm:ss'),lastReference:to_datef(\"Last Ref\",'yyyy-MM-dd HH:mm:ss')}" sql="select * order by lastReference" out=ctable
```
---

##### 106
### 📖 OpenAF | SFTP
Generates a file list with filepath, size, permissions, create and last modified time from a SFTP connection with user and password
```bash
HOST="my.server" && PORT=22 && LOGIN="user" && PASS=$"abc123" && LSPATH="." && oaf -c "sprint(\$ssh({host:'$HOST',login:'$LOGIN',pass:'$PASS'}).listFiles('$LSPATH'))" | oafp out=ctable path="[].{isDirectory:isDirectory,filepath:filepath,size:size,createTime:to_date(mul(createTime,\`1000\`)),lastModified:to_date(mul(lastModified,\`1000\`)),permissions:permissions}" from="sort(-isDirectory,filepath)"
```
---

##### 107
### 📖 OpenAF | SFTP
Generates a file list with filepath, size, permissions, create and last modified time from a SFTP connection with user, private key and password
```bash
HOST="my.server" && PORT=22 && PRIVID=".ssh/id_rsa" && LOGIN="user" && PASS=$"abc123" && LSPATH="." && oaf -c "sprint(\$ssh({host:'$HOST',login:'$LOGIN',pass:'$PASS',id:'$PRIVID'}).listFiles('$LSPATH'))" | oafp out=ctable path="[].{isDirectory:isDirectory,filepath:filepath,size:size,createTime:to_date(mul(createTime,\`1000\`)),lastModified:to_date(mul(lastModified,\`1000\`)),permissions:permissions}" from="sort(-isDirectory,filepath)"
```
---

##### 108
### 📖 OpenAF | TLS
List the TLS certificates of a target host with a sorted alternative names using OpenAF
```bash
DOMAIN=yahoo.com && oaf -c "sprint(ow.loadNet().getTLSCertificates('$DOMAIN',443))" | oafp path="[].{issuer:issuerDN,subject:subjectDN,notBefore:notBefore,notAfter:notAfter,alternatives:join(' | ',sort(map(&[1],nvl(alternatives,\`[]\`))))}" out=ctree
```
---

##### 109
### 📖 OpenAF | oJob.io
Parses ojob.io/news results into a clickable news title HMTL page.
```bash
ojob ojob.io/news/awsnews __format=json | oafp path="[].{title:replace(t(@,'[{{title}}]({{link}})'),'\|','g','\\|'),date:date}" from="sort(-date)" out=mdtable | oafp in=md out=html
```
---

##### 110
### 📖 OpenAF | oJob.io
Retrieves the list of oJob.io&#x27;s jobs and filters which start by &#x27;ojob.io/news&#x27; to display them in a rectangle
```bash
oafp url="https://ojob.io/index.json" path="sort(init.l)[].replace(@,'^https://(.+)\.(yaml|json)$','','\$1')|[?starts_with(@, 'ojob.io/news')]" out=map
```
---

##### 111
### 📖 OpenAF | oPacks
Listing all currently accessible OpenAF&#x27;s oPacks
```bash
oaf -c "sprint(getOPackRemoteDB())" | oafp maptoarray=true opath="[].{name:name,description:description,version:version}" from="sort(name)" out=ctable
```
---

##### 112
### 📖 OpenAF | oafp
Filter the OpenAF&#x27;s oafp examples list by a specific word in the description
```bash
oafp url="https://ojob.io/oafp-examples.yaml" in=yaml out=template path=data templatepath=tmpl sql="select * where d like '%something%'"
```
---

##### 113
### 📖 OpenAF | oafp
List the OpenAF&#x27;s oafp examples by category, sub-category and description
```bash
oafp url="https://ojob.io/oafp-examples.yaml" in=yaml path="data[].{category:c,subCategory:s,description:d}" from="sort(category,subCategory,description)" out=ctable
```
---

##### 114
### 📖 OpenVPN | List
When using the container nmaguiar/openvpn it&#x27;s possible to convert the list of all clients order by expiration/end date
```bash
oafp cmd="docker exec openvpn ovpn_listclients" in=csv path="[].{name:name,begin:to_datef(begin,'MMM dd HH:mm:ss yyyy z'),end:to_datef(end,'MMM dd HH:mm:ss yyyy z'),status:status}" out=ctable sql="select * order by end desc"
```
---

##### 115
### 📖 Unix | Activity
Uses the Linux command &#x27;last&#x27; output to build a table with user, tty, from and period of activity
```bash
oafp cmd="last" in=lines linesjoin=true path="[:-3]|[?contains(@,'no logout')==\`false\`&&contains(@,'system boot')==\`false\`].split_re(@,' \\s+').{user:[0],tty:[1],from:[2],period:join(' ',[3:])}" out=ctable
```
---

##### 116
### 📖 Unix | Alpine
List all installed packages in an Alpine system
```bash
apk list -I | oafp in=lines linesjoin=true path="[].replace(@,'(.+) (.+) {(.+)} \((.+)\) \[(.+)\]','','\$1|\$2|\$3|\$4').split(@,'|').{package:[0],arch:[1],source:[2],license:[3]}" out=ctable
```
---

##### 117
### 📖 Unix | Compute
Parses the Linux /proc/cpuinfo into an array
```bash
cat /proc/cpuinfo | sed "s/^$/---/mg" | oafp in=yaml path="[?not_null(@)]|[?type(processor)=='number']" out=ctree
```
---

##### 118
### 📖 Unix | Debian/Ubuntu
List all installed packages in a Debian/Ubuntu system
```bash
apt list --installed | sed "1d" | oafp in=lines linesjoin=true path="[].split(@,' ').{pack:split([0],'/')[0],version:[1],arch:[2]}" out=ctable
```
---

##### 119
### 📖 Unix | Envs
Converts the Linux envs command result into a table of environment variables and corresponding values
```bash
env | oafp in=ini path="map(&{key:@,value:to_string(get(@))},sort(keys(@)))" out=ctable
```
---

##### 120
### 📖 Unix | Files
Converting the Linux&#x27;s /etc/os-release to SQL insert statements.
```bash
oafp cmd="cat /etc/os-release" in=ini outkey=release path="[@]" sql="select '$HOSTNAME' \"HOST\", *" out=sql sqlnocreate=true
```
---

##### 121
### 📖 Unix | Files
Converting the Unix&#x27;s syslog into a json output.
```bash
cat syslog | oafp in=raw path="split(trim(@),'\n').map(&split(@, ' ').{ date: concat([0],concat(' ',[1])), time: [2], host: [3], process: [4], message: join(' ',[5:]) }, [])"
```
---

##### 122
### 📖 Unix | Files
Executes a recursive file list find command converting the result into a table.
```bash
LSPATH=/openaf && find $LSPATH -exec stat -c '{"t":"%F", "p": "%n", "s": %s, "m": "%Y", "e": "%A", "u": "%U", "g": "%G"}' {} \; | oafp in=ndjson ndjsonjoin=true path="[].{type:t,permissions:e,user:u,group:g,size:s,modifiedDate:to_date(mul(to_number(m),\`1000\`)),filepath:p}" from="sort(type,filepath)" out=ctable
```
---

##### 123
### 📖 Unix | Files
Parses the Linux /etc/passwd to a table order by uid and gid.
```bash
oafp cmd="cat /etc/passwd" in=csv inputcsv="(withHeader: false, withDelimiter: ':')" path="[].{user:f0,pass:f1,uid:to_number(f2),gid:to_number(f3),description:f4,home:f5,shell:f6}" out=json | oafp from="notStarts(user, '#').sort(uid, gid)" out=ctable
```
---

##### 124
### 📖 Unix | Generic
Creates, in unix, a data.ndjson file where each record is formatted from json files in /some/data
```bash
find /some/data -name "*.json" -exec oafp {} output=json \; > data.ndjson
```
---

##### 125
### 📖 Unix | Memory map
Given an Unix process will output a table with process&#x27;s components memory address, size in bytes, permissions and owner
```bash
pmap 12345 | sed '1d;$d' | oafp in=lines linesjoin=true path="[].split_re(@, '\\s+').{address:[0],size:from_bytesAbbr([1]),perm:[2],owner:join('',[3:])}" out=ctable
```
---

##### 126
### 📖 Unix | Network
Loop over the current Linux active network connections
```bash
oafp cmd="netstat -tun | sed \"1d\"" in=lines linesvisual=true linesjoin=true linesvisualsepre="\\s+(\\?\!Address)" out=ctable loop=1
```
---

##### 127
### 📖 Unix | Network
Parse the Linux &#x27;arp&#x27; command output
```bash
arp | oafp in=lines linesvisual=true linesjoin=true out=ctable
```
---

##### 128
### 📖 Unix | Network
Parse the Linux &#x27;ip tcp_metrics&#x27; command
```bash
ip tcp_metrics | sed 's/^/target: /g' | sed 's/$/\n\n---\n/g' | sed 's/ \([a-z]*\) /\n\1: /g' | head -n -2 | oafp in=yaml path="[].{target:target,age:from_timeAbbr(replace(age,'[sec|\.]','','')),cwnd:cwnd,rtt:from_timeAbbr(rtt),rttvar:from_timeAbbr(rttvar),source:source}" sql="select * order by target" out=ctable
```
---

##### 129
### 📖 Unix | Network
Parse the result of the Linux route command
```bash
route | sed "1d" | oafp in=lines linesjoin=true linesvisual=true linesvisualsepre="\s+" out=ctable
```
---

##### 130
### 📖 Unix | OpenSuse
List all installed packages in an OpenSuse system or zypper based system
```bash
zypper se -is | egrep "^i" | oafp in=lines linesjoin=true path="[].split(@,'|').{name:[1],version:[2],arch:[3],repo:[4]}" out=ctable
```
---

##### 131
### 📖 Unix | RedHat
List all installed packages in a RedHat system or rpm based system (use rpm --querytags to list all fields available)
```bash
rpm -qa --qf "%{NAME}|%{VERSION}|%{PACKAGER}|%{VENDOR}|%{ARCH}\n" | oafp in=lines linesjoin=true path="[].split(@,'|').{package:[0],version:[1],packager:[2],vendor:[3],arch:[4]}" from="sort(package)" out=ctable
```
---

##### 132
### 📖 Unix | Storage
Converting the Unix&#x27;s df output
```bash
df --output=target,fstype,size,used,avail,pcent | tail -n +2 | oafp in=lines linesjoin=true path="[].split_re(@, ' +').{filesystem:[0],type:[1],size:[2],used:[3],available:[4],use:[5]}" out=ctable
```
---

##### 133
### 📖 Unix | Storage
Parses the result of the Unix ls command
```bash
ls -lad --time-style="+%Y-%m-%d %H:%M" * | oafp in=lines path="map(&split_re(@,'\\s+').{permissions:[0],id:[1],user:[2],group:[3],size:[4],date:[5],time:[6],file:[7]},[])" linesjoin=true out=ctable
```
---

##### 134
### 📖 Unix | SystemCtl
Converting the Unix&#x27;s systemctl list-timers
```bash
systemctl list-timers | head -n -3 | oafp in=lines linesvisual=true linesjoin=true out=ctable
```
---

##### 135
### 📖 Unix | SystemCtl
Converting the Unix&#x27;s systemctl list-units
```bash
systemctl list-units | head -n -6 | oafp in=lines linesvisual=true linesjoin=true path="[].delete(@,'')" out=ctable
```
---

##### 136
### 📖 Unix | SystemCtl
Converting the Unix&#x27;s systemctl list-units into an overview table
```bash
systemctl list-units | head -n -6 | oafp in=lines linesvisual=true linesjoin=true path="[].delete(@,'')" sql="select \"LOAD\", \"ACTIVE SUB\", count(1) as \"COUNT\" group by \"LOAD\", \"ACTIVE SUB\"" sqlfilter=advanced out=ctable
```
---

##### 137
### 📖 Unix | UBI
List all installed packages in an UBI system
```bash
microdnf repoquery --setopt=cachedir=/tmp --installed | oafp in=lines linesjoin=true path="[].replace(@,'(.+)\.(\w+)\.(\w+)\$','','\$1|\$2|\$3').split(@,'|').{package:[0],dist:[1],arch:[2]}" out=ctable
```
---

##### 138
### 📖 Unix | named
Converts a Linux&#x27;s named log, for client queries, into a CSV
```bash
cat named.log | oafp in=lines linesjoin=true path="[?contains(@,' client ')==\`true\`].split(@,' ').{datetime:to_datef(concat([0],concat(' ',[1])),'dd-MMM-yyyy HH:mm:ss.SSS'),session:[3],sourceIP:replace([4],'(.+)#(\d+)','','\$1'),sourcePort:replace([4],'(.+)#(\d+)','','\$2'),target:replace([5],'\((.+)\):','','\$1'),query:join(' ',[6:])}" out=csv
```
---

##### 139
### 📖 Windows | Network
Output a table with the current route table using Windows&#x27; PowerShell
```bash
Get-NetRoute | ConvertTo-Json | .\oafp.bat path="[].{destination:DestinationPrefix,gateway:NextHop,interface:InterfaceAlias,metric:InterfaceMetric}" sql=select\ *\ order\ by\ interface,destination out=ctable
```
---

##### 140
### 📖 Windows | Network
Output a table with the list of network interfaces using Windows&#x27; PowerShell
```bash
Get-NetIPAddress | ConvertTo-Json | .\oafp.bat path="[].{ipAddress:IPAddress,prefixLen:PrefixLength,interface:InterfaceAlias}" sql=select\ *\ order\ by\ interface out=ctable
```
---

##### 141
### 📖 Windows | PnP
Output a table with USB/PnP devices using Windows&#x27; PowerShell
```bash
Get-PnpDevice -PresentOnly | ConvertTo-Csv -NoTypeInformation | .\oafp.bat in=csv path="[].{class:PNPClass,service:Service,name:FriendlyName,id:InstanceId,description:Description,deviceId:DeviceID,status:Status,present:Present}" sql=select\ *\ order\ by\ class,service out=ctable
```
---

##### 142
### 📖 Windows | Storage
Output a table with the attached disk information using Windows&#x27; PowerShell
```bash
Get-Disk | ConvertTo-Csv -NoTypeInformation | .\oafp.bat in=csv path="[].{id:trim(UniqueId),name:FriendlyName,isBoot:IsBoot,location:Location,size:to_bytesAbbr(to_number(Size)),allocSize:to_bytesAbbr(to_number(AllocatedSize)),sectorSize:LogicalSectorSize,phySectorSize:PhysicalSectorSize,numPartitions:NumberOfPartitions,partitioning:PartitionStyle,health:HealthStatus,bus:BusType,manufacturer:Manufacturer,model:Model,firmwareVersion:FirmwareVersion,serialNumber:SerialNumber}" out=ctable
```

