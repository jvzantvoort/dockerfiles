
NAME ?= "jvzantvoort/centos7:1"

build:
	docker rmi $(NAME) || echo "oke"
	docker build -t $(NAME) --file Dockerfile --rm .

all: build
	 docker run -it --rm -u 1085:1085 -v /home/jvzantvoort/rpmbuild:/home/rpmbuild/rpmbuild jvzantvoort/centos7:1  rpmbuild rpmbuild/SPECS/nagiosmsg.spec
