# NorthStar C2 agent RCE via stored XSS
Agent RCE PoC for CVE-2024-28741, a stored XSS vulnerability in NorthStar C2.

This exploit works by sending multiple malicious agent registration requests to the teamserver to incrementally build a functioning javascript payload in the logs web page. This XSS can be leveraged to execute commands on NorthStar C2 agents

Full explanation: https://blog.chebuya.com/posts/discovering-cve-2024-28741-remote-code-execution-on-northstar-c2-agents-via-pre-auth-stored-xss/


https://github.com/chebuya/CVE-2024-28741-northstar-agent-rce-poc/assets/146861503/182070a5-1a70-4875-b440-867ee3f43c6f

