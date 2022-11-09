# docker-jira-worklogs

To get the project up and running see the below instructions:

1. To obtain the text plain source code you must decrypt the .enc files. If interested, contact me for a decryption password.

```
openssl enc -aes-256-cbc -d -in panel.py.enc -out panel.py
openssl enc -aes-256-cbc -d -in auth.py.enc -out auth.py
openssl enc -aes-256-cbc -d -in Dockerfile.enc -out Dockerfile
```

2. Run docker build

```
docker build -t devel-worklog .
```

3. Create .jira-credentials file (use template below, just replace the placeholders with your information)

```
#!/bin/bash

export JIRA_URL=REPLACEME
export JIRA_USER=REPLACEME
export JIRA_PASSWD=REPLACEME
```

4. Launch container

```
docker run -it --mount type=bind,source=$PWD/.jira-credentials,target=/opt/jira-client/.jira-credentials devel-worklog bash
```
