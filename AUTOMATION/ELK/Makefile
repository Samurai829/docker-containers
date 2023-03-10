#----------------------------------------------------------------------------------------
# CONTRUCCION DE ELK MEDIANTE MAKEFILE
#----------------------------------------------------------------------------------------

#----------------------------------------------------------------------------------------
# Construccion y Despligue de varios contenedores para ELK
# Visualizacion de contenedores de ELK
# Detencion de los contenedores de ELK
# Eliminacion de los contenedores ELK
# Eliminacion profunda de ELK
#----------------------------------------------------------------------------------------

# Variables
NAME = ELK

IMAGE_LOGSTASH = logstash:7.9.2
IMAGE_ELASTIC = elasticsearch:7.9.2
IMAGE_KIBANA = kibana:7.9.2


#----------------------------------------------------------------------------------------
# CONSTRUCCION DE ELK
#----------------------------------------------------------------------------------------
build_elk: ## Construccion y Ejecucion de los contenedores de ELK
	@echo 'Construcion del Servicio $(NAME)'
	docker-compose build
	@echo 'Despliegue del Servicio $(NAME)'
	docker-compose up -d
	$(MAKE) show_containers


#----------------------------------------------------------------------------------------
# VISUALIZACION DE TODO
#----------------------------------------------------------------------------------------
show_containers: ## Muesta contenedores en ejecucion
	@echo 'Visualizacion de CONTENEDORES en ejecucion'
	docker ps --filter "status=running"

show_all: ## Muesta images y contenedores
	@echo 'Visualizacion de IMAGENES'
	docker images -a 
	@echo 'Visualizacion de CONTENEDORES en ejecucion'
	docker ps --filter "status=running"
	@echo 'CONTENEDORES fuera de ejecucion'
	docker ps --filter "status=exited"


#----------------------------------------------------------------------------------------
# DETENCION DE ELK
#----------------------------------------------------------------------------------------
stop_elk: ## Detencion de todos los contenedores de ELK
	@echo 'Detencion del Servicio $(NAME)'
	docker-compose stop
	$(MAKE) show_containers


#----------------------------------------------------------------------------------------
# INICIA DE ELK
#----------------------------------------------------------------------------------------
start_elk: ## Inicia todos los contenedores de ELK
	@echo 'Inicio del Servicio $(NAME)'
	docker-compose start
	$(MAKE) show_containers


#----------------------------------------------------------------------------------------
# REINICIA DE ELK
#----------------------------------------------------------------------------------------
restart_elk: ## Inicia todos los contenedores de ELK
	@echo 'Reinicio del Servicio $(NAME)'
	$(MAKE) stop_elk
	$(MAKE) start_elk
	$(MAKE) show_containers


#----------------------------------------------------------------------------------------
# ELIMINACION DE ELK
#----------------------------------------------------------------------------------------
delete_images: ## Eliminacion de todas las imagenes de ELK
	@echo 'Eliminacion de imagenes de $(NAME)'
	docker images $(IMAGE_ELASTIC) 
	docker images $(IMAGE_LOGSTASH)
	docker images $(IMAGE_KIBANA)
	docker rmi $(IMAGE_ELASTIC) $(IMAGE_LOGSTASH) $(IMAGE_KIBANA)

delete_elk: ## Eliminacion de todos los contenedores de ELK
	@echo 'Eliminacion del Servicio $(NAME)'
	docker-compose down
	$(MAKE) show_all

deep_delete: ## Elimanacion de todo ELK
	@echo 'Eliminando Imagenes, Contenedores y Networks de $(NAME)'
	$(MAKE) delete_elk
	$(MAKE) delete_images
	docker network rm elk_default





#----------------------------------------------------------------------------------------
# COMANDO DE AYUDA
.PHONY: help
help: ## Comando de ayuda
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//
#----------------------------------------------------------------------------------------
	