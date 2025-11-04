
# Hacking WordPress CheatSheet

## wpscan
```
wpscan --url http://<ip>/ -e vp,vt,u 
```
## Find Flugin && Themes
```
curl -s -X GET http://<ip> | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'wp-content/plugins/*' | cut -d"'" -f2

curl -s -X GET http://<ip> | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2
```

## Plugins Active Enumeration

```
curl -I -X GET http://<ip>/wp-content/plugins/mail-masta
```

## User Enumeration

- The **admin** user is usually assigned the user ID 1. We can confirm this by specifying the user ID for the **author** parameter in the URL.
```
http://<ip>/?author=1
curl -s -I http://blog.inlanefreight.com/?author=1
```
- **JSON** endpoint
```
curl http://blog.inlanefreight.com/wp-json/wp/v2/users | jq

```
