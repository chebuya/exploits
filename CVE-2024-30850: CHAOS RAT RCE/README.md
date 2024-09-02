https://github.com/chebuya/CVE-2024-30850-chaos-rat-rce-poc/assets/146861503/ac03c8c7-54b3-4280-9f29-719c44af5192
# CHAOS RAT v5.01 web panel RCE (CVE-2024-30850, CVE-2024-31839)
https://github.com/tiagorlampert/CHAOS <br>

This exploit works by spoofing an agent callback for an XSS (CVE-2024-31839), and leveraging the XSS to exploit a command injection vulnerability (CVE-2024-30850) in the admin web panel.  This leads to compromise of the RAT server and rickrolling of RAT panel operators.

Full explaination: https://blog.chebuya.com/posts/remote-code-execution-on-chaos-rat-via-spoofed-agents/ <br>

```
python3 exploit.py exploit -h                                                               
usage: exploit.py exploit [-h] [-f FILE] [-t TARGET] [-c COMMAND] [-v VIDEO_NAME] [-j JWT] -l LOCAL_IP [-p LOCAL_PORT] [-H HOSTNAME] [-u USERNAME] [-o OS]
                          [-m MAC] [-i IP]

options:
  -h, --help            show this help message and exit
  -f FILE, --file FILE  The path to the CHAOS client
  -t TARGET, --target TARGET
                        The url of the CHAOS server (127.0.0.1:8080)
  -c COMMAND, --command COMMAND
                        The command to use
  -v VIDEO_NAME, --video-name VIDEO_NAME
                        The video name to use
  -j JWT, --jwt JWT     The JWT token to use
  -l LOCAL_IP, --local-ip LOCAL_IP
                        The local IP to use for serving bash script and mp4
  -p LOCAL_PORT, --local-port LOCAL_PORT
                        The local port to use for serving bash script and mp4
  -H HOSTNAME, --hostname HOSTNAME
                        The hostname to use for the spoofed client
  -u USERNAME, --username USERNAME
                        The username to use for the spoofed client
  -o OS, --os OS        The OS to use for the spoofed client
  -m MAC, --mac MAC     The MAC address to use for the spoofed client
  -i IP, --ip IP        The IP address to use for the spoofed client
```
![oopsec](https://github.com/chebuya/CVE-2024-30850-chaos-rat-rce-poc/assets/146861503/25835d48-d967-495a-8e84-756153a82246)


