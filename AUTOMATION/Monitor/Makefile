#----------------------------------------------------------------------------------------
# AUTOMATIZACION HERRAMIENTAS DE MONITORIZACION 
#----------------------------------------------------------------------------------------
# CREACION Y DESPLIEGUE DE CONTENEDORES PARA MONITORIZACION
# VISUALIZACION DE CONTENEDORES
# DETENCION, INICIACION Y ELIMINACION DE TODO MONITOR
#----------------------------------------------------------------------------------------


# VARIABLES
NAME_1 = prometheus
NAME_2 = grafana
NAME_3 = redis
NAME_4 = redis-exporter

IMAGE_PROMETHEUS = prom/prometheus
IMAGE_GRAFANA = grafana/grafana
IMAGE_REDIS = redis:alpine3.16
IMAGE_EXPORTER = oliver006/redis_exporter 

#----------------------------------------------------------------------------------------
# CONSTRUCCION Y DESPLIEGUE DE MONITOR
#----------------------------------------------------------------------------------------
build_prometheus:
	@echo 'Construccion y ejecucion de $(NAME_1)'
	cd prometheus && docker-compose up -d
	

build_grafana:
	@echo 'Construccion y ejecucion de $(NAME_2)'
	cd grafana && docker-compose up -d
	

build_redis:
	@echo 'Construccion y ejecucion de $(NAME_3)'
	cd redis && docker-compose up -d
	

build_exporter:
	@echo 'Construccion y ejecucion de $(NAME_4)'
	cd redis-exporter && docker-compose up -d
	

# EJECUCION DE TODO MONITOR EN UN SOLO COMANDO
build_monitor: ## Construccion y Ejecucion de los contenedores de Monitor
	@echo 'Levantamiento de todo MONITOR'
	$(MAKE) build_prometheus
	$(MAKE) build_grafana
	$(MAKE) build_redis
	$(MAKE) build_exporter
	$(MAKE) show_containers
	

#----------------------------------------------------------------------------------------
# VISUALIZACION 
#----------------------------------------------------------------------------------------
show_containers: ## Muesta contenedores en ejecucion
	@echo 'Visualizacion de contenedores en Ejecucion'
	docker ps --filter "status=running"

show_all: ## Muesta images y contenedores
	@echo 'Visualizacion de IMAGENES'
	docker images -a 
	@echo 'Visualizacion de CONTENEDORES en ejecucion'
	docker ps --filter "status=running"
	@echo 'CONTENEDORES fuera de ejecucion'
	docker ps --filter "status=exited"


#----------------------------------------------------------------------------------------
# DETENCION DE MONITOR
#----------------------------------------------------------------------------------------
stop_prometheus:
	@echo 'Detencion de ejecucion del servicio $(NAME_1)'
	cd prometheus && docker-compose stop $(NAME_1)

stop_grafana:
	@echo 'Detencion de ejecucion del servicio $(NAME_2)'
	cd grafana && docker-compose stop $(NAME_2)

stop_redis:
	@echo 'Detencion de ejecucion del servicio $(NAME_3)'
	cd redis && docker-compose stop $(NAME_3)

stop_exporter:
	@echo 'Detencion de ejecucion del servicio $(NAME_4)'
	cd prometheus && docker-compose stop $(NAME_4)


# DETENCION DE TODO LOS CONTENEDORES DE MONITOR EN UN SOLO COMANDO
stop_monitor: ## Detencion de los contenedores de Monitor
	@echo 'Detencion de todos los servicios MONITOR'
	$(MAKE) stop_prometheus
	$(MAKE) stop_grafana
	$(MAKE) stop_redis
	$(MAKE) stop_exporter
	$(MAKE) show_containers		
	@echo 'Todos los servicios de MONITOR fueron detenidos'


#----------------------------------------------------------------------------------------
# INICIA DE ELK
#----------------------------------------------------------------------------------------
start_prometheus:
	@echo 'Detencion de ejecucion del servicio $(NAME_1)'
	cd prometheus && docker-compose start $(NAME_1)

start_grafana:
	@echo 'Detencion de ejecucion del servicio $(NAME_2)'
	cd grafana && docker-compose start $(NAME_2)

start_redis:
	@echo 'Detencion de ejecucion del servicio $(NAME_3)'
	cd redis && docker-compose start $(NAME_3)

start_exporter:
	@echo 'Detencion de ejecucion del servicio $(NAME_4)'
	cd prometheus && docker-compose start $(NAME_4)


# INICIACION DE TODO LOS CONTENEDORES DE MONITOR EN UN SOLO COMANDO
start_monitor: ## Detencion de los contenedores de Monitor
	@echo 'Inicio de todos los servicios MONITOR'
	$(MAKE) start_prometheus
	$(MAKE) start_grafana
	$(MAKE) start_redis
	$(MAKE) stop_exporter
	$(MAKE) start_exporter		
	@echo 'Todos los servicios de MONITOR fueron detenidos'

#----------------------------------------------------------------------------------------
# REINICIA DE ELK
#----------------------------------------------------------------------------------------
restart_monitor: ## Inicia todos los contenedores de Monitor
	@echo 'Reinicio del Servicio $(NAME)'
	$(MAKE) stop_monitor
	$(MAKE) start_monitor
	$(MAKE) show_containers


#----------------------------------------------------------------------------------------
# ELIMINACION DE MONITOR
#----------------------------------------------------------------------------------------
delete_prometheus:
	@echo 'Eliminacion de $(NAME_1)'
	cd prometheus && docker-compose down
	@echo 'Servicio eliminado'

delete_grafana:
	@echo 'Eliminacion de $(NAME_2)'
	cd grafana && docker-compose down
	@echo 'Servicio eliminado'

delete_redis:
	@echo 'Eliminacion de $(NAME_3)'
	cd redis && docker-compose down
	@echo 'Servicio eliminado'

delete_exporter:
	@echo 'Eliminacion de $(NAME_4)'
	cd redis-exporter && docker-compose down
	@echo 'Servicio eliminado'
	
# ELIMINACION DE TODOS LOS CONTENEDORES DE MONITOR EN UN SOLO COMANDO
delete_monitor: ## Eliminacion de los contenedores de Monitor
	@echo 'Eliminacion de todo MONITOR'
	$(MAKE) delete_exporter
	$(MAKE) delete_redis
	$(MAKE) delete_prometheus
	$(MAKE) delete_grafana
	$(MAKE) show_containers
	@echo 'Todos los servicios MONITOR fueron eliminados'

# ELIMINACION DE TODAS LAS IMAGENES DE MONITOR EN UN SOLO COMANDO
delete_images: ## Eliminacion de todas las imagenes de Monitor
	@echo 'Eliminacion de imagenes de MONITOR'
	docker rmi $(IMAGE_PROMETHEUS) $(IMAGE_GRAFANA) $(IMAGE_REDIS) $(IMAGE_EXPORTER)

# ELIMINACION DE TODOS MONITOR EN UN SOLO COMANDO
deep_delete: ## Eliminacion de todo Monitor
	@echo 'Eliminando Imagenes y Contenedores de MONITOR'
	$(MAKE) delete_monitor
	$(MAKE) delete_images


#----------------------------------------------------------------------------------------
# COMANDO DE AYUDA
.PHONY: help
help: ## Comando de ayuda
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//
#----------------------------------------------------------------------------------------
	