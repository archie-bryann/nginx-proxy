https://chatgpt.com/c/6900a146-fc50-8332-9e41-f8827758e13d
https://chatgpt.com/s/t_6900b847eba08191b2271acb8ac7b97e

# Important Todo

On your **self-hosted runner server** (deployment server). Run it once:

```bash
sudo docker network create app-network
```

Then all your apps (nginx, rails, react) running on that server will connect to it.
