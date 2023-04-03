FROM grafana/grafana:9.1.6
COPY --chown=grafana:root hostfs/var/data/monitoring/grafana/grafana.db /var/lib/grafana/
### Transitive ENTRYPOINT
ENTRYPOINT ["/run.sh"]