_DOCKER_IMAGE_NAMESPACE ?= localhost/kc-dataengineering-monitoring-grafana
_DOCKER_IMAGE_NAME      ?= grafana
_DOCKER_IMAGE_TAG       ?= 9.1.6

all: build

.PHONY: build
build: build-manifest-on-host build-docker

.PHONY: build-manifest-on-host
build-manifest-on-host: init-manifest-on-host
	cp hostfs/var/data/monitoring/grafana/grafana.db.default hostfs/var/data/monitoring/grafana/grafana.db
	sqlite3 hostfs/var/data/monitoring/grafana/grafana.db < hostfs/var/manifest/monitoring/grafana/1-rename_main_org.grafana.sql
	sqlite3 hostfs/var/data/monitoring/grafana/grafana.db < hostfs/var/manifest/monitoring/grafana/2A-add_org.algoquant.grafana.sql
	sqlite3 hostfs/var/data/monitoring/grafana/grafana.db < hostfs/var/manifest/monitoring/grafana/2B-add_org.equitysupport.grafana.sql
	sqlite3 hostfs/var/data/monitoring/grafana/grafana.db < hostfs/var/manifest/monitoring/grafana/3A-add_org_admin_user.algoquant.grafana.sql
	sqlite3 hostfs/var/data/monitoring/grafana/grafana.db < hostfs/var/manifest/monitoring/grafana/3B-add_org_admin_user.equitysupport.grafana.sql

.PHONY: build-docker
build-docker:
	echo "Building docker image - $(_DOCKER_IMAGE_NAMESPACE)/$(_DOCKER_IMAGE_NAME):$(_DOCKER_IMAGE_TAG)"
	docker build \
				--no-cache \
				-f .hack/build/docker/Dockerfile \
				-t $(_DOCKER_IMAGE_NAMESPACE)/$(_DOCKER_IMAGE_NAME):$(_DOCKER_IMAGE_TAG) \
				.


.PHONY: init
init: init-manifest-on-host

.PHONY: init-manifest-on-host
init-manifest-on-host:
	sudo yum install -y epel-release
	sudo yum install -y sqlite
