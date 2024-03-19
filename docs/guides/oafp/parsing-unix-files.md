---
layout: default
title: oafp to parse Unix files
parent: oafp
grand_parent: Guides
---

# oafp to parse Unix files

List of examples of use of oafp to parse unix files:

### Converting the Unix’s syslog into a json output

```bash
cat syslog | oafp in=raw path="split(trim(@),'\n').map(&split(@, ' ').{ date: concat([0],concat(' ',[1])), time: [2], host: [3], process: [4], message: join(' ',[5:]) }, [])"
```

### Converting /etc/os-release to SQL insert statements

```bash
oafp cmd="cat /etc/os-release" in=ini outkey=release path="[@]" sql="select '$HOSTNAME' \"HOST\", *" out=sql sqlnocreate=true
```

### Parses the /etc/passwd to a table order by uid and gid

```bash
oafp cmd="cat /etc/passwd" in=csv inputcsv="(withHeader: false, withDelimiter: ':')" path="[].{user:f0,pass:f1,uid:to_number(f2),gid:to_number(f3),description:f4,home:f5,shell:f6}" sql="select * order by uid,gid" out=ctable
```

or

```bash
oafp cmd="cat /etc/passwd" in=csv inputcsv="(withHeader: false, withDelimiter: ':')" path="[].{user:f0,pass:f1,uid:to_number(f2),gid:to_number(f3),description:f4,home:f5,shell:f6}" out=json | oafp from="notStarts(user, '#').sort(uid, gid)" out=ctable
```

Result:

```
  user  │pass│ uid │ gid │           description            │     home      │      shell      
────────┼────┼─────┼─────┼──────────────────────────────────┼───────────────┼─────────────────
root    │x   │0    │0    │root                              │/root          │/bin/bash        
daemon  │x   │1    │1    │daemon                            │/usr/sbin      │/usr/sbin/nologin
bin     │x   │2    │2    │bin                               │/bin           │/usr/sbin/nologin
sys     │x   │3    │3    │sys                               │/dev           │/usr/sbin/nologin
sync    │x   │4    │65534│sync                              │/bin           │/bin/sync        
games   │x   │5    │60   │games                             │/usr/games     │/usr/sbin/nologin
man     │x   │6    │12   │man                               │/var/cache/man │/usr/sbin/nologin
lp      │x   │7    │7    │lp                                │/var/spool/lpd │/usr/sbin/nologin
mail    │x   │8    │8    │mail                              │/var/mail      │/usr/sbin/nologin
news    │x   │9    │9    │news                              │/var/spool/news│/usr/sbin/nologin
uucp    │x   │10   │10   │uucp                              │/var/spool/uucp│/usr/sbin/nologin
proxy   │x   │13   │13   │proxy                             │/bin           │/usr/sbin/nologin
www-data│x   │33   │33   │www-data                          │/var/www       │/usr/sbin/nologin
backup  │x   │34   │34   │backup                            │/var/backups   │/usr/sbin/nologin
list    │x   │38   │38   │Mailing List Manager              │/var/list      │/usr/sbin/nologin
irc     │x   │39   │39   │ircd                              │/run/ircd      │/usr/sbin/nologin
gnats   │x   │41   │41   │Gnats Bug-Reporting System (admin)│/var/lib/gnats │/usr/sbin/nologin
_apt    │x   │100  │65534│                                  │/nonexistent   │/usr/sbin/nologin
nobody  │x   │65534│65534│nobody                            │/nonexistent   │/usr/sbin/nologin
[#19 rows]
```