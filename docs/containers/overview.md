---
title: Outils de conteneur Visual Studio sur Windows
description: Découvrir les outils disponibles dans Visual Studio pour travailler avec Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: b60e5df4d94c290ca8aa7bf56471b5fed6c1879a
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568909"
---
# <a name="container-tools-in-visual-studio"></a>Outils de conteneur dans Visual Studio

Les outils inclus dans Visual Studio pour le développement avec des conteneurs sont faciles à utiliser et simplifient considérablement la création, le débogage et le déploiement d’applications conteneurisées. Vous pouvez utiliser un conteneur dans un seul projet, ou opter pour une orchestration de conteneur avec Docker Compose, Service Fabric ou Kubernetes afin d’utiliser plusieurs services dans des conteneurs.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Prérequis

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail **Développement web**, **Azure Tools** et/ou la charge de travail **Développement multiplateforme .NET Core**
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous pour obtenir un essai gratuit](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Prise en charge de Docker dans Visual Studio

La prise en charge de Docker est disponible pour les projets ASP.NET, les projets ASP.NET Core, et les projets de console .NET Core et .NET Framework.

La prise en charge de Docker dans Visual Studio a été modifiée sur un certain nombre de versions pour répondre aux besoins des clients. Il existe deux niveaux de prise en charge de Docker que vous pouvez ajouter à un projet, et les options prises en charge varient selon le type de projet et la version de Visual Studio. Pour certains types de projets pris en charge, si vous souhaitez utiliser un conteneur dans un seul projet, sans orchestration, ajoutez la prise en charge de Docker.  Le niveau suivant est la prise en charge de l’orchestration de conteneur, qui ajoute les fichiers de prise en charge appropriés pour l’orchestrateur spécifique que vous choisissez.  

Avec Visual Studio 2017, vous pouvez utiliser Docker Compose et Service Fabric comme services d’orchestration de conteneur.  Vous pouvez également utiliser Kubernetes si vous installez [Visual Studio Tools pour Kubernetes](https://aka.ms/get-vsk8stools).

> [!NOTE]
> Si vous utilisez une version de Visual Studio 2017 antérieure à 15.8, ou si vous utilisez le modèle de projet .NET Framework (et non pas .NET Core), lorsque vous ajoutez la prise en charge de Docker, la prise en charge de l’orchestration à l’aide de Docker Compose est automatiquement ajoutée. La prise en charge de l’orchestration de conteneur, via Docker Compose, est automatiquement ajoutée dans Visual Studio 2017 versions 15.0 à 15.7 et dans les projets .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Prérequis

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail **Développement web**, **Outils Azure** et/ou la charge de travail **Développement multiplateforme .NET Core** installée
* [Outils de développement .NET core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pour le développement avec .NET Core 2.2
* Pour publier sur Azure Container Registry, un abonnement Azure. [Inscrivez-vous pour obtenir un essai gratuit](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Prise en charge de Docker dans Visual Studio

La prise en charge de Docker est disponible pour les projets ASP.NET, les projets ASP.NET Core, et les projets de console .NET Core et .NET Framework.

La prise en charge de Docker dans Visual Studio a été modifiée sur un certain nombre de versions pour répondre aux besoins des clients. Il existe deux niveaux de prise en charge de Docker que vous pouvez ajouter à un projet, et les options prises en charge varient selon le type de projet et la version de Visual Studio. Pour certains types de projets pris en charge, si vous souhaitez utiliser un conteneur dans un seul projet, sans orchestration, ajoutez la prise en charge de Docker.  Le niveau suivant est la prise en charge de l’orchestration de conteneur, qui ajoute les fichiers de prise en charge appropriés pour l’orchestrateur spécifique que vous choisissez.  


Visual Studio 2019 vous permet d’utiliser Docker Compose, Kubernetes et Service Fabric comme services d’orchestration de conteneur.

> [!NOTE]
> Si vous utilisez le modèle de projet de console .NET Framework complet, lorsque vous ajoutez la prise en charge de Docker, la prise en charge de l’orchestration à l’aide de Docker Compose est automatiquement ajoutée.
::: moniker-end

### <a name="adding-docker-support"></a>Ajout de la prise en charge de Docker

Vous pouvez activer la prise en charge de Docker lors de la création d’un projet en sélectionnant **Activer la prise en charge de Docker**, comme illustré dans la capture d’écran suivante :

::: moniker range="vs-2017"
![Activer la prise en charge de Docker pour une nouvelle application web ASP.NET Core dans Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Activer la prise en charge de Docker pour une nouvelle application web ASP.NET Core dans Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Pour les projets .NET Framework (pas .NET Core), seuls les conteneurs Windows sont disponibles.

Vous pouvez ajouter la prise en charge de Docker à un projet existant en sélectionnant **Ajouter** > **Prise en charge de Docker** dans l’**Explorateur de solutions**. Les commandes **Ajouter > Prise en charge de Docker** et **Ajouter > Prise en charge des orchestrateurs de conteneurs** se trouvent dans le contextuel du nœud du projet pour un projet ASP.NET Core dans l’**Explorateur de solutions**, comme illustré dans la capture d’écran suivante :

![Option de menu Ajouter la prise en charge de Docker dans Visual Studio](./media/overview/add-docker-support-menu.png)

Lorsque vous ajoutez ou activez la prise en charge de Docker, Visual Studio ajoute les éléments suivants au projet :

- un fichier *Dockerfile*
- un fichier .dockerignore
- une référence de package NuGet pour Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
Une fois la prise en charge de Docker ajoutée, la solution ressemble à ceci :

![Capture d’écran de l’Explorateur de solutions avec les fichiers Dockerfile et .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Lorsque vous activez la prise en charge de Docker lors de la création d’un projet ASP.NET (.NET Framework, et non pas .NET Core) comme indiqué dans la capture d’écran suivante, la prise en charge de l’orchestration de conteneur est également ajoutée.

![Activer la prise en charge de Docker Compose pour un projet ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Prise en charge de Docker Compose

Pour composer une solution à plusieurs conteneurs avec Docker Compose, ajoutez la prise en charge de l’orchestration de conteneur à vos projets. Cela vous permet d’exécuter et de déboguer simultanément un groupe de conteneurs (une solution complète ou un groupe de projets), si ces conteneurs sont définis dans le même fichier *docker-compose.yml*.

Pour ajouter la prise en charge de l’orchestration de conteneur à l’aide de Docker Compose, cliquez sur le nœud de la solution ou du projet dans l’**Explorateur de solutions**, puis choisissez **Ajouter > Prise en charge des orchestrateurs de conteneurs**. Choisissez ensuite **Docker Compose** pour gérer les conteneurs.

Après avoir ajouté la prise en charge de l’orchestration de conteneur à votre projet, un fichier *Dockerfile* est ajouté au projet (le cas échéant) et un dossier **docker-compose** est ajouté à la solution dans l’**Explorateur de solutions**, comme illustré ici :

![Fichiers Docker dans l’Explorateur de solutions de Visual Studio](media/overview/docker-support-solution-explorer.png)

Si le fichier *docker-compose.yml* existe déjà, Visual Studio ajoute simplement les lignes de code de configuration requises.

Répétez le processus avec les autres projets que vous souhaitez contrôler à l’aide de Docker Compose.

## <a name="kubernetes-support"></a>Prise en charge de Kubernetes

::: moniker range="vs-2017"
Pour ajouter la prise en charge de Kubernetes, installez [Visual Studio Tools pour Kubernetes](https://aka.ms/get-vsk8stools).
::: moniker-end

Avec la prise en charge de Kubernetes, vous pouvez établir une connexion entre votre projet local et un cluster Kubernetes exécuté dans [Azure Kubernetes Service (AKS)](/azure/aks) et ainsi modifier et déboguer vos services en cours d’exécution dans AKS à l’aide de Visual Studio.  Ce service est fourni par [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). Azure Dev Spaces vous permet également de définir des branches distinctes de vos services Kubernetes, appelées *dev spaces*, à des fins de développement, et ainsi d’isoler efficacement les services de production des versions en cours de développement, tout en séparant de façon nette les différentes modifications.

Pour ajouter la prise en charge de Kubernetes à vos projets, choisissez **Kubernetes/Helm** lorsque vous ajoutez la prise en charge de l’orchestration de conteneur. Plusieurs fichiers sont ajoutés à votre projet, y compris *azds.yaml*, qui configure Azure Dev Spaces, ainsi que des graphiques Helm qui décrivent la structure de vos services Kubernetes.

## <a name="service-fabric-support"></a>Prise en charge de Service Fabric

Grâce aux outils Service Fabric dans Visual Studio, vous pouvez développer et déboguer pour Azure Service Fabric, mais aussi exécuter et déboguer localement et déployer sur Azure.

::: moniker range="vs-2017"
Visual Studio 2017 version 15.9 ou ultérieure avec charge de travail de développement Azure installée prend en charge le développement de microservices conteneurisés à l’aide de conteneurs Windows et de l’orchestration Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 prend en charge le développement de microservices conteneurisés à l’aide de conteneurs Windows et de l’orchestration Service Fabric.
::: moniker-end

Pour obtenir un didacticiel détaillé, consultez [Didacticiel : déployer une application .net dans un conteneur Windows sur Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Pour plus d’informations sur Azure Service Fabric, consultez [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Livraison continue et intégration continue (CI/CD)

Visual Studio s’intègre facilement à Azure Pipelines pour offrir une intégration et une livraison continues et automatisées des modifications apportées au code et la configuration de votre service. Pour commencer, consultez [Créer votre premier pipeline](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Pour Service Fabric, consultez [Didacticiel : déployer votre application ASP.net core dans Azure Service fabric à l’aide de Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Pour Kubernetes, consultez [Déployer une application de conteneur Docker sur Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’implémentation des services et l’utilisation des outils Visual Studio avec des conteneurs, lisez les articles suivants :

[Débogage d’applications dans un conteneur Docker local](edit-and-refresh.md)

[Déployer un conteneur ASP.NET sur un registre de conteneurs avec Visual Studio](hosting-web-apps-in-docker.md)
