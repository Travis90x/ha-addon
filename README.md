# Source Code Link

-   [FrontEnd](https://github.com/CoolKit-Technologies/ha-addon-frontEnd)
-   [BackEnd](https://github.com/CoolKit-Technologies/ha-addon-backEnd)

# Home-Assistant-AddOn

## ADD-ON:

-   Refer to [Wiki](https://bit.ly/eWeLinkaddon)

## DOCKER:

-   **Use host network to discover and control DIY and LAN devices.**
-   **Currently, port forwarding is not supported, please make sure that port 3000 is idle.**

Delete old container
`sudo docker rm -f ewelink_smart_home` and `docker rmi ewelink_smart_home`


1. `git clone https://github.com/Travis90x/ha-addon.git`
2. `cd ha-addon/eWeLink_Smart_Home/`
3. ` docker buildx build --platform linux/arm/v7 -t ewelink_smart_home:armv7 .`
4. Run the code below. Replace `yourHomeAssistantUrl` with your current Home Assisant URL.

```
docker run -d \
    --restart=unless-stopped \
    --network host \
    -e HA_URL=yourHomeAssistantUrl \
    -e SUPERVISOR_TOKEN=yourHomeAssitantLongLivedAccessToken \
    -v ./volume:/data \
    --name ewelink_smart_home \
    ewelink_smart_home:armv7
```

-   Example:

```
  docker run -d \
  --restart=unless-stopped \
  --network host \
  -e HA_URL=http://192.168.1.100:8123 \
  -e SUPERVISOR_TOKEN=eyJ~iJ9.eyJ~jF9.CkQ~Lho \
  -v ./volume:/data \
  --name ewelink_smart_home \
  ewelink_smart_home:armv7
```

5. Access port `3000`.
