# include docker-compose .env file
include open5gs.env

.NOTPARALLEL:

.PHONY: base-open5gs \
        amf-open5gs \
		ausf-open5gs \
		bsf-open5gs \
		nrf-open5gs \
		nssf-open5gs \
		pcf-open5gs \
		scp-open5gs \
		sepp-open5gs \
		smf-open5gs \
		udm-open5gs \
		udr-open5gs \
		upf-open5gs \
		webui-open5gs \
		all-open5gs \
		clean-open5gs \
		base-ueransim \
		gnb-ueransim \
		ue-ueransim \
		all-ueransim \
		clean-ueransim \
		packetrusher \
		clean-packetrusher \
		mongodb \
		all clean \
		docker-prune-system

base-open5gs:
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/base-open5gs:${OPEN5GS_VERSION} ./images/base-open5gs
	
amf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/amf-open5gs:${OPEN5GS_VERSION} ./images/amf-open5gs

ausf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/ausf-open5gs:${OPEN5GS_VERSION} ./images/ausf-open5gs

bsf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/bsf-open5gs:${OPEN5GS_VERSION} ./images/bsf-open5gs

nrf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/nrf-open5gs:${OPEN5GS_VERSION} ./images/nrf-open5gs

nssf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/nssf-open5gs:${OPEN5GS_VERSION} ./images/nssf-open5gs

pcf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/pcf-open5gs:${OPEN5GS_VERSION} ./images/pcf-open5gs

scp-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/scp-open5gs:${OPEN5GS_VERSION} ./images/scp-open5gs

sepp-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/sepp-open5gs:${OPEN5GS_VERSION} ./images/sepp-open5gs

smf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/smf-open5gs:${OPEN5GS_VERSION} ./images/smf-open5gs

udm-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/udm-open5gs:${OPEN5GS_VERSION} ./images/udm-open5gs

udr-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/udr-open5gs:${OPEN5GS_VERSION} ./images/udr-open5gs

upf-open5gs: base-open5gs
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/upf-open5gs:${OPEN5GS_VERSION} ./images/upf-open5gs

webui-open5gs:
	docker build --build-arg NODE_VERSION=${NODE_VERSION} --build-arg OPEN5GS_VERSION=${OPEN5GS_VERSION} -t fgftk/webui-open5gs:${OPEN5GS_VERSION} ./images/webui-open5gs

base-ueransim:
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg UERANSIM_VERSION=${UERANSIM_VERSION} -t fgftk/base-ueransim:${UERANSIM_VERSION} ./images/base-ueransim

gnb-ueransim: base-ueransim
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg UERANSIM_VERSION=${UERANSIM_VERSION} -t fgftk/gnb-ueransim:${UERANSIM_VERSION} ./images/gnb-ueransim

ue-ueransim: base-ueransim
	docker build --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} --build-arg UERANSIM_VERSION=${UERANSIM_VERSION} -t fgftk/ue-ueransim:${UERANSIM_VERSION} ./images/ue-ueransim

mongodb:
	docker build --build-arg MONGODB_VERSION=${MONGODB_VERSION} -t fgftk/mongodb:${MONGODB_VERSION} ./images/mongodb

packetrusher:
	docker build --build-arg PACKETRUSHER_UBUNTU_VERSION=${PACKETRUSHER_UBUNTU_VERSION} --build-arg PACKETRUSHER_GO_VERSION=${PACKETRUSHER_GO_VERSION} --build-arg PACKETRUSHER_VERSION=${PACKETRUSHER_VERSION} -t fgftk/packetrusher:${PACKETRUSHER_VERSION} ./images/packetrusher

all-open5gs: base-open5gs amf-open5gs ausf-open5gs bsf-open5gs nrf-open5gs nssf-open5gs pcf-open5gs scp-open5gs sepp-open5gs smf-open5gs udm-open5gs udr-open5gs \
             upf-open5gs webui-open5gs

clean-open5gs:
	docker image remove fgftk/base-open5gs:${OPEN5GS_VERSION} fgftk/amf-open5gs:${OPEN5GS_VERSION} fgftk/ausf-open5gs:${OPEN5GS_VERSION} \
	fgftk/bsf-open5gs:${OPEN5GS_VERSION} fgftk/nrf-open5gs:${OPEN5GS_VERSION} fgftk/nssf-open5gs:${OPEN5GS_VERSION} fgftk/pcf-open5gs:${OPEN5GS_VERSION} \
	fgftk/scp-open5gs:${OPEN5GS_VERSION} fgftk/sepp-open5gs:${OPEN5GS_VERSION} fgftk/smf-open5gs:${OPEN5GS_VERSION} fgftk/udm-open5gs:${OPEN5GS_VERSION} \
	fgftk/udr-open5gs:${OPEN5GS_VERSION} fgftk/upf-open5gs:${OPEN5GS_VERSION} fgftk/webui-open5gs:${OPEN5GS_VERSION}

all-ueransim: base-ueransim gnb-ueransim ue-ueransim

clean-ueransim:
	docker image remove fgftk/base-ueransim:${UERANSIM_VERSION} fgftk/gnb-ueransim:${UERANSIM_VERSION} fgftk/ue-ueransim:${UERANSIM_VERSION}

clean-mongodb:
	docker image remove fgftk/mongodb:${MONGODB_VERSION}

clean-packetrusher:
	docker image remove fgftk/packetrusher:${PACKETRUSHER_VERSION}

all: all-open5gs all-ueransim mongodb packetrusher

clean: clean-open5gs clean-ueransim clean-mongodb clean-packetrusher

docker-prune-system:
	docker system prune -f