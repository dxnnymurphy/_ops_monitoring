#####################################################################
### make
#####################################################################
all: init

#####################################################################
### make init
#####################################################################

.PHONY: init
init: init-secret

.PHONY: init-secret
init-secret: 
	mkdir -p .secret/__envrc.d
	cp -rf $(HOME)/.cheuvreux/var/secret/keplercheuvreux/kc-dataengineering/monitoring-grafana/__envrc.d .secret/

#####################################################################
### make activate
#####################################################################
.PHONY: activate
activate: activate-grafana-alerting-addons

.PHONY: activate-grafana-alerting-addons
activate-grafana-alerting-addons:
	#cp -f config/_ops_monitoring_grafana/provisioning/alerting.disabled/2-alerting-rules-operation-datasource-2-ingestion-pipeline-algofeedtracer-hits.yml  config/_ops_monitoring_grafana/provisioning/alerting
	cp -f config/_ops_monitoring_grafana/provisioning/alerting.disabled/3-alerting-rules-operation-datasource-1-ullink-bridge-statistics-health-check-spot.yml  config/_ops_monitoring_grafana/provisioning/alerting

#####################################################################
### make deactivate
#####################################################################
.PHONY: deactivate
deactivate: deactivate-grafana-alerting-addons

.PHONY: deactivate-grafana-alerting-addons
deactivate-grafana-alerting-addons:
	#rm -f config/_ops_monitoring_grafana/provisioning/alerting/2-alerting-rules-operation-datasource-2-ingestion-pipeline-algofeedtracer-hits.yml
	rm -f config/_ops_monitoring_grafana/provisioning/alerting/3-alerting-rules-operation-datasource-1-ullink-bridge-statistics-health-check-spot.yml