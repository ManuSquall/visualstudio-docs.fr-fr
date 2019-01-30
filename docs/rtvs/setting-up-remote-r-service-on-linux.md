---
title: Configuration de Service R à distance pour Linux
description: Guide pratique pour configurer Service R à distance sur Ubuntu et le sous-système Windows pour Linux.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d73f6df65c1ce1b78448a7582330741c887f7768
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020202"
---
# <a name="remote-r-service-for-linux"></a>Service R à distance pour Linux

Service R à distance pour Linux est actuellement fourni en tant que rtvs-daemon. Le démon est pris en charge et testé sur Ubuntu 16.04, 16.10 LTS Desktop, Server et le sous-système Windows pour Linux exécutant Ubuntu. L’essentiel de cet article fournit des instructions pour configurer Service R à distance sur ces différents systèmes.

Une fois que vous avez configuré l’ordinateur distant, les étapes suivantes connectent les outils R pour Visual Studio (RTVS) à ce service :

1. Sélectionnez **Outils R** > **Windows** > **Espaces de travail** pour ouvrir la fenêtre **Espaces de travail**.
1. Sélectionnez **Ajouter une connexion**.
1. Donnez un nom à la connexion et indiquez son URL, par exemple `https://localhost:5444` (sous-système Windows pour Linux) ou `https://public-ip:5444` (conteneur Azure). Sélectionnez **Enregistrer** lorsque vous avez terminé.
1. Sélectionnez l’icône de connexion ou double-cliquez sur l’élément de connexion.
1. Fournissez des informations d’identification de connexion. Le nom d’utilisateur doit avoir pour préfixe `<<unix>>\` comme dans `<<unix>>\ruser1` (comme exigé pour toutes les connexions aux ordinateurs distants Linux).
1. Si vous utilisez un certificat auto-signé, vous pouvez voir un avertissement. Le message fournit des instructions pour corriger l’avertissement.

## <a name="set-up-remote-r-service"></a>Configuration de Service R à distance

Cette section décrit les options suivantes :

- [Ordinateur Ubuntu physique](#physical-ubuntu-computer)
- [Machine virtuelle Ubuntu Server ou machine virtuelle de science des données sur Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Conteneur Docker local ou distant (build propre)](#local-or-remote-docker-container-clean-build)
- [Conteneur s’exécutant sur Azure Container Instances](#container-running-on-azure-container-instances)

Dans chaque cas, les interpréteurs R suivants doivent être installés sur l’ordinateur distant :

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R pour Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Ordinateur Ubuntu physique

1. Une fois connecté à l’ordinateur, téléchargez le tarball rtvs-daemon :

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Exécutez le script d’installation :

    ```bash
    sudo ./rtvs-install
    ```

    Pour une automatisation sans assistance, utilisez `sudo ./rtvs-install -s`.

1. Activez et démarrez le service :

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Configurez le certificat SSL (requis pour la production). Par défaut, rtvs-daemon utilise les `ssl-cert-snakeoil.pem` et `ssl-cert-snakeoil.pem` générés par le package `ssl-cert`. Pendant l’installation, ils sont combinés dans `ssl-cert-snakeoil.pfx`. À des fins de production, utilisez le certificat SSL fourni par votre administrateur. Le certificat SSL peut être configuré en fournissant un fichier *.pfx* et un mot de passe d’importation facultatif dans : */etc/rtvs/rtvsd.config.json*.

1. (Facultatif) Vérifiez que le service est en cours d’exécution :

    ```bash
    ps -A -f | grep rtvsd
    ```

    Si vous ne voyez pas de processus en cours d’exécution sous le nom d’utilisateur `rtvssvc`. Démarrez-le à l’aide de la commande suivante :

    ```bash
    sudo systemctl start rtvsd
    ```

1. Pour configurer rtvs-daemon, consultez `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Machine virtuelle Ubuntu Server ou machine virtuelle de science des données sur Azure

#### <a name="create-a-vm"></a>Créer une machine virtuelle

1. Connectez-vous au [portail Azure](https://portal.azure.com).
1. Accédez aux machines virtuelles, puis sélectionnez **Ajouter**.
1. Dans la liste des images de machine virtuelle disponibles, recherchez et sélectionnez un des éléments suivants :
    - Ubuntu Server : `Ubuntu Server 16.04 LTS`
    - Machine virtuelle de science des données : `Linux Data Science` (Consultez [Machines virtuelles de science des données](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) pour plus d’informations.)
1. Affectez au modèle de déploiement la valeur `Resource manager` et sélectionnez **Créer**.
1. Choisissez un nom pour la machine virtuelle, fournissez un nom d’utilisateur et un mot de passe (le mot de passe est obligatoire, car la connexion par clé publique SSH n’est pas prise en charge).
1. Apportez les autres modifications souhaitées à la configuration de la machine virtuelle.
1. Choisissez une taille de machine virtuelle, vérifiez la configuration et sélectionnez **Créer**. Une fois que la machine virtuelle est créée, passez à la section suivante.

#### <a name="configure-the-vm"></a>Configurer la machine virtuelle

1. Dans la section **Réseau** de la machine virtuelle, ajoutez 5444 comme port d’entrée autorisé. Pour utiliser un port différent, modifiez le paramètre dans le fichier de configuration du démon RTVS (*/etc/rtvs/rtvsd.config.json*).
1. (Facultatif) Définissez un nom DNS ; vous pouvez également utiliser l’adresse IP.
1. Connectez-vous à la machine virtuelle à l’aide d’un client SSH, comme PuTTY pour Windows.
1. Suivez les instructions relatives à un [ordinateur Ubuntu physique](#physical-ubuntu-computer) ci-dessus.

### <a name="windows-subsystem-for-linux-wsl"></a>Sous-système Windows pour Linux (WSL)

1. Suivez les instructions d’installation WSL pour [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) ou [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Démarrez Bash sur Windows et suivez les instructions précédentes relatives à un [ordinateur Ubuntu physique](#physical-ubuntu-computer) à une exception près. Dans l’étape 3, démarrez le service plutôt à l’aide de la commande `rtvsd`, car WSL ne prend actuellement pas en charge les interfaces systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Conteneur Docker local ou distant (build propre)

1. Créez un fichier Docker avec le contenu ci-dessous, qui installe le démon de Service R à distance et la dernière version de R. **Remarque** : ce script crée un utilisateur nommé « ruser1 » avec le mot de passe « foobar », que vous pouvez modifier à votre gré dans les deux dernières instructions `RUN`.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Générez et exécutez le fichier Docker :

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Pour vous connecter au contenu de RTVS, utilisez `https://localhost:5444` comme chemin, le nom d’utilisateur `<<unix>>\ruser1` et le mot de passe `foobar`. Si le conteneur est en cours d’exécution sur un ordinateur distant, utilisez plutôt `https://remote-host-name:5444` en tant que chemin. Le port peut être changé en mettant à jour */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Conteneur s’exécutant sur Azure Container Instances

1. Suivez les instructions indiquées dans [Conteneur Docker local ou distant (build propre)](#local-or-remote-docker-container-clean-build) pour créer l’image.
1. Transmettez le conteneur au Hub Docker ou à Azure Container Repository.
1. Démarrez Azure CLI et connectez-vous en utilisant la commande `az login`.
1. Utilisez la commande `az container create` pour créer le conteneur, en utilisant `--command-line "rtvsd"` si vous n’avez pas configuré le conteneur pour exécuter `rtvsd` en tant que service `systemd`. Dans la commande ci-dessous, l’image est censée se trouver sur le Hub Docker. Vous pouvez également utiliser Azure Container Repository en ajoutant des arguments d’informations d’identification Container Repository à la ligne de commande.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```
1. Utilisez la commande `az container list` pour vérifier l’état. Recherchez `provisioningState` : `Succeeded`.
1. Si le provisionnement a réussi, vous pouvez maintenant vous connecter au conteneur. Recherchez l’adresse IP publique, dans le champ `ipAddress`, que vous utilisez avec les informations d’identification incluses dans le fichier Docker pour vous connecter au conteneur à partir de RTVS.
