# docker_study


1. docker pull
  docker pull osrf/ros:noetic-desktop-full
2. run
vi docker_ros.sh
  PS_NAME=ros_noetic
  xhost +
  xhost + ${homename}
  export HOSTNAME=`hostname`
  
  docker stop $PS_NAME 2>/dev/null
  docker rm $PS_NAME 2>/dev/null
  
  docker run -it --privileged \
  --env="QT_X11_NO_MITSHM=1" \
  -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
  -v /dev:/dev:rw \
  -v=/Users/apple/workspace:/workspace \
  -e DISPLAY=host.docker.internal:0 \
  --hostname $(hostname) \
  --group-add dialout \
  --user root \
  --shm-size 4096m \
  --name $PS_NAME ros_noetic bas

3. docker commit
docker commit {CONTAINER ID} {MY IMAGE NAME:TAG}를 하면 컨테이너가 이미지로 저장된다.
