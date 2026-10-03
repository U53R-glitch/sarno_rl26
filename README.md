# sarno_rl26 — Robotics Lab 2026

Repository per il Classwork 0 del corso Robotics Lab 2026 (Prof. Mario Selvaggio).
Contiene l'ambiente Docker per lo sviluppo con ROS 2 Humble.

## Prerequisiti

- Linux (Ubuntu 22.04 nativo, WSL2 o VM)
- Docker installato e configurato per esecuzione non-root
- Git installato

## Struttura del repository

sarno_rl26/
├── docker_scripts/
│   ├── Dockerfile
│   ├── docker_build_image.sh
│   ├── docker_run_container.sh
│   └── docker_connect.sh
├── src/
│   └── .gitkeep
└── README.md

## Come buildare e avviare il container

1. Clonare il repository:

   git clone https://github.com/<tuo-username>/sarno_rl26.git
   cd sarno_rl26

2. Rendere eseguibili gli script:

   chmod +x docker_scripts/*.sh

3. Buildare l'immagine Docker:

   ./docker_scripts/docker_build_image.sh

4. Avviare il container:

   ./docker_scripts/docker_run_container.sh

5. Collegare un terminale aggiuntivo:

   ./docker_scripts/docker_connect.sh

## Verifica installazione

Dentro il container eseguire:

   echo $ROS_DISTRO          # Output atteso: humble
   ros2 pkg list             # Mostra i pacchetti installati

## Verifica persistenza dei volumi

Dentro il container:

   touch /home/user/ros2_ws/src/test_persistence.txt
   exit

Dopo aver fermato e rimosso il container:

   docker container prune -f

Verificare che il file test_persistence.txt sia ancora presente nella
cartella src/ dell'host.
