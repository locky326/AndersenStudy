# Scripting assignments
## Turn this one-liner into a nice script:
```sh
sudo netstat -tunapl | awk '/firefox/ {print $5}' | cut -d: -f1 | sort | uniq -c | sort | tail -n5 | grep -oP '(\d+\.){3}\d+' | while read IP ; do whois $IP | awk -F':' '/^Organization/ {print $2}' ; done
```
* 1 point for parametrization: you might want to enter PID or name of another process as an argument
* 1 point for parametrization: you might want to see more results
* 1 point for parametrization: you might want to see other connection states
* 1 point for securing script execution and nice error messages
* 2 points for writing a README.md for what your script does
* 2 points for adding count of connections per organization to the final output
* 2 points for rewriting the functionality differently, say using `ss`, `sed`, built-ins like `"${VAR%%:*}"` (might be a separate script)

### Hints
* you probably should start with `sudo netstat -tunapl | less` # mnemonic is 'tuna, please'
* progress through pipes until it becomes clear what the thing is doing
