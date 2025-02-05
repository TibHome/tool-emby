#!/bin/bash
source function_common

SERVICE_NAME="emby"
SERVICE_IMAGE_NAME="emby/embyserver"
SERVICE_IMAGE_VERSION="latest"

start_container(){
    ${DOCKER_PATH} \
    run --name ${SERVICE_NAME} -d \
        --restart=always \
        --privileged \
        --network=host \
        -v {{ installDir }}/${SERVICE_NAME}/configuration:/config \
        -v {{ installDir }}/${SERVICE_NAME}/data:/data \
        -v /etc/localtime:/etc/localtime:ro \
        -p 8096:8096 \
        --health-cmd "echo 'test' > /dev/null" \
        --health-interval=5s \
        ${SERVICE_IMAGE_NAME}:${SERVICE_IMAGE_VERSION} \
        || exit 1
    
    log_succe "Container ${SERVICE_NAME} deployed"
}

main $@