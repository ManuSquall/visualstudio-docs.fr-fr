---
title: Installer Build Tools dans un conteneur | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 95b60369350ad099e53b143ff85adbcef250b8b9
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="install-build-tools-into-a-container"></a>Installer Build Tools dans un conteneur

Vous pouvez installer Visual Studio Build Tools dans un conteneur Windows pour prendre en charge les flux de travail d’intégration continue (CI) et de livraison continue(CD). Cet article vous explique comment procéder aux modifications nécessaires de la configuration Docker, et vous donne les [charges de travail et composants](workload-component-id-vs-build-tools.md) que vous pouvez installer dans un conteneur.

Les [conteneurs](https://www.docker.com/what-container) sont un excellent moyen d’empaqueter un système de génération cohérent, que vous pouvez utiliser non seulement dans un environnement serveur CI/CD, mais également dans un environnement de développement. Vous pouvez, par exemple, monter votre code source dans un conteneur pour qu’il soit généré par un environnement personnalisé, tout en continuant d’utiliser Visual Studio ou d’autres outils pour écrire votre code. Si votre flux de travail CI/CD utilise la même image de conteneur, vous avez la garantie que votre code est généré de manière cohérente. Vous pouvez également utiliser des conteneurs pour obtenir une cohérence d’exécution, ce qui est courant pour les microservices qui utilisent plusieurs conteneurs avec un système d’orchestration. Cependant, cela dépasse le cadre de cet article.

Si Visual Studio Build Tools n’a pas ce dont vous avez besoin pour générer votre code source, vous pouvez utiliser ces étapes pour d’autres produits Visual Studio. Notez, toutefois, que les conteneurs Windows ne prennent pas en charge les interfaces utilisateur interactives, et que toutes les commandes doivent être automatisées.

## <a name="overview"></a>Vue d'ensemble

À l’aide de [Docker](https://www.docker.com/what-docker), vous créez une image à partir de laquelle vous pouvez créer des conteneurs qui génèrent votre code source. L’exemple de fichier Dockerfile installe la dernière version de Visual Studio Build Tools 2017, ainsi que d’autres programmes utiles souvent utilisés pour la génération de code source. Vous pouvez modifier davantage votre propre fichier Dockerfile en y ajoutant d’autres outils et scripts pour exécuter des tests, publier la sortie de génération, et bien plus encore.

Si vous avez déjà installé Docker pour Windows, vous pouvez passer à l’étape 3.

## <a name="step-1-enable-hyper-v"></a>Étape 1. Activer Hyper-V

Hyper-V n’est pas activé par défaut. Il doit être activé au démarrage de Docker pour Windows, puisque seule l’isolation Hyper-V est prise en charge par Windows 10.

* [Activer Hyper-V sur Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Activer Hyper-V sur Windows Server 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> La virtualisation doit être activée sur votre machine. Elle est généralement activée par défaut. Toutefois, si l’installation d’Hyper-V échoue, reportez-vous à la documentation de votre système pour savoir comment activer la virtualisation.

## <a name="step-2-install-docker-for-windows"></a>Étape 2. Installer Docker pour Windows

Si vous utilisez Windows 10, vous pouvez télécharger et installer [Docker Community Edition pour Windows](https://www.docker.com/docker-windows). Vous pouvez utiliser PowerShell pour [installer Docker Enterprise Edition pour Windows Server 2016](https://docs.docker.com/engine/installation/windows/docker-ee) à l’aide de la configuration DSC ou d’un [fournisseur de package](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) pour une installation unique.

## <a name="step-3-switch-to-windows-containers"></a>Étape 3. Passer aux conteneurs Windows

Vous pouvez uniquement installer Build Tools 2017 sur Windows, ce qui vous oblige à [passer aux conteneurs Windows](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Dans Windows 10, les conteneurs Windows prennent uniquement en charge [l’isolation Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), alors que dans Windows Server 2016, les conteneurs Windows prennent en charge à la fois l’isolation Hyper-V et l’isolation des processus.

## <a name="step-4-expand-maximum-container-disk-size"></a>Étape 4. Augmenter la taille maximale du disque du conteneur

Visual Studio Build Tools, et plus généralement Visual Studio, nécessitent une grande quantité d’espace disque pour tous les outils à installer. Même si notre exemple de fichier Dockerfile désactive le cache du package, la taille du disque des images conteneurs doit être augmentée en fonction de l’espace nécessaire. Dans Windows, vous pouvez uniquement augmenter la taille du disque en modifiant la configuration de Docker.

**Sur Windows 10** :

1. [Cliquez sur l’icône de Docker pour Windows](https://docs.docker.com/docker-for-windows/#docker-settings) dans la barre d’état système, puis cliquez sur **Paramètres...**.
2. [Cliquez sur la section Démon](https://docs.docker.com/docker-for-windows/#docker-daemon).
3. [Cliquez sur le bouton **De base**](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) pour basculer en mode **Avancé**.
4. Ajoutez la propriété de tableau JSON suivante pour définir l’espace disque sur 120 Go (ce qui est plus que suffisant pour Build Tools et vous permet d’ajouter d’autres programmes).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Cette propriété vient s’ajouter à ce qui est déjà défini. Par exemple, après avoir appliqué ces modifications au fichier de configuration du démon par défaut, vous devez voir ce qui suit :

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Cliquez sur **Appliquer**.

**Sur Windows Server 2016** :

1. Arrêtez le service « docker » :

   ```shell
   sc.exe stop docker
   ```

2. À partir d’une invite de commandes avec élévation de privilèges, modifiez « %ProgramData%\Docker\config\daemon.json » (ou ce que vous avez spécifié sur `dockerd --config-file`).
3. Ajoutez la propriété de tableau JSON suivante pour définir l’espace disque sur 120 Go (ce qui est plus que suffisant pour Build Tools et vous permet d’ajouter d’autres programmes).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Cette propriété vient s’ajouter à ce qui est déjà défini.
4. Enregistrez et fermez le fichier.
5. Démarrez le service « docker » :

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Étape 5. Créer et générer le fichier Dockerfile

Vous devez enregistrer l’exemple de fichier Dockerfile suivant dans un nouveau fichier, sur votre disque. Si le fichier se nomme simplement « Dockerfile », il est reconnu par défaut.

> [!NOTE]
> Cet exemple de fichier Dockerfile exclut uniquement les anciens SDK Windows qui ne peuvent pas être installés dans des conteneurs. Les versions plus anciennes font échouer la commande de génération.

1. Ouvrez une invite de commandes.
2. Créez un répertoire (recommandé) :

   ```shell
   mkdir C:\BuildTools
   ```

3. Remplacez les répertoires par ce nouveau répertoire :

   ```shell
   cd C:\BuildTools
   ```

3. Enregistrez le contenu suivant dans C:\BuildTools\Dockerfile.

   ```dockerfile
   # Use the latest Windows Server Core image.
   FROM microsoft/windowsservercore

   # Download useful tools to C:\Bin.
   ADD https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe C:\\Bin\\nuget.exe

   # Download the Build Tools bootstrapper outside of the PATH.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\TEMP\\vs_buildtools.exe

   # Add C:\Bin to PATH and install Build Tools excluding workloads and components with known issues.
   RUN setx /m PATH "%PATH%;C:\Bin" \
    && C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache --installPath C:\BuildTools --all \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 \
       --remove Microsoft.VisualStudio.Component.Windows81SDK \
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

4. Exécutez la commande suivante dans ce répertoire.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Cette commande génère le fichier Dockerfile dans le répertoire actuel, en utilisant 2 Go de mémoire. La valeur par défaut de 1 Go ne suffit pas lorsque certaines charges de travail sont installées. Toutefois, il est possible que vous puissiez le générer avec 1 Go de mémoire en fonction des besoins de votre build.

   L’image finale est marquée comme « buildtools2017:latest » pour que vous puissiez aisément l’exécuter dans un conteneur en tant que « buildtools2017 », puisque la marque « latest » est la valeur par défaut lorsqu’aucune marque n’est spécifiée. Si vous souhaitez utiliser une version spécifique de Visual Studio Build Tools 2017 dans un [scénario avancé](advanced-build-tools-container.md), marquez le conteneur avec un numéro de build Visual Studio spécifique et avec « latest », pour que les conteneurs puissent utiliser la même version.

## <a name="step-6-using-the-built-image"></a>Étape 6. Utilisation de l’image générée

Maintenant que vous avez créé une image, vous pouvez l’exécuter dans un conteneur pour effectuer des générations automatisées et interactives. L’exemple utilise l’invite de commandes développeur. Votre chemin (PATH) et autres variables d’environnement sont donc déjà configurés.

1. Ouvrez une invite de commandes.
2. Exécutez le conteneur pour démarrer un environnement PowerShell avec toutes les variables d’environnement développeur définies :

   ```shell
   docker run -it buildtools2017
   ```

Si vous souhaitez utiliser cette image pour votre flux de travail CI/CD, vous pouvez la publier dans votre propre instance [Azure Container Registry](https://azure.microsoft.com/services/container-registry) ou dans un autre [registre Docker](https://docs.docker.com/registry/deploying) interne, pour que les serveurs n’aient plus qu’à la tirer (pull).

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :
* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) et y poser des questions et obtenir des réponses.
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio)  (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [Exemple avancé pour les conteneurs](advanced-build-tools-container.md)
* [Problèmes de conteneurs connus](build-tools-container-issues.md)
* [ID de composant et de charge de travail de Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
