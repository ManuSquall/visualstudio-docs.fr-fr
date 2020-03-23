---
title: Kubernetes outils tutoriel (fr) Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: f5868f97301eba62d16ea68cdaa0c97c8e20edd1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916947"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Lancez-vous avec Visual Studio Kubernetes Tools

Les outils Visual Studio Kubernetes aident à rationaliser le développement d’applications conteneurisées ciblant Kubernetes. Visual Studio peut créer automatiquement les fichiers de configuration en code nécessaires pour prendre en charge le déploiement de Kubernetes, tels que les cartes Dockerfiles et Helm. Vous pouvez déboiffer votre code dans un cluster Azure Kunetes Service (AKS) en direct à l’aide d’Azure Dev Spaces, ou publier directement sur un cluster AKS depuis Visual Studio.

Ce tutoriel couvre l’utilisation de Visual Studio pour ajouter le support Kubernetes à un projet et de publier à AKS. Si vous êtes principalement intéressé à utiliser [Azure Dev Spaces](/azure/dev-spaces/) pour déboguer et tester votre projet en cours d’exécution dans AKS, vous pouvez sauter à l’Azure [Dev Spaces tutoriel](/azure/dev-spaces/get-started-netcore-visualstudio) à la place.

## <a name="prerequisites"></a>Conditions préalables requises

Pour tirer parti de cette nouvelle fonctionnalité, vous aurez besoin :

::: moniker range="vs-2017"
- La dernière version de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail *ASP.NET et le développement web.*
- Les [outils Kubernetes pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibles en téléchargement séparé.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail *Développement ASP.NET et web*.
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) installé sur votre poste de travail de développement (c’est-à-dire où vous exécutez Visual Studio), si vous souhaitez construire des images Docker, déboguer des conteneurs Docker fonctionnant localement ou publier sur AKS. (Docker *n’est pas* nécessaire pour la construction et le débogage des conteneurs Docker dans AKS en utilisant Azure Dev Spaces.)
::: moniker range="vs-2017"
- Si vous souhaitez publier à AKS de Visual Studio *(pas* nécessaire pour débogage dans AKS en utilisant Azure Dev Spaces):

    1. Les [outils de publication AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibles en téléchargement séparé.

    1. Cluster Azure Kubernetes Service. Pour plus d’informations, voir [Création d’un cluster AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Assurez-vous de [vous connecter au cluster à](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) partir de votre poste de travail de développement.

    1. Helm CLI installé sur votre poste de travail de développement. Pour plus d’informations voir [Installing Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. Casque configuré contre votre cluster `helm init` AKS en utilisant la commande. Pour plus d’informations sur la façon de le faire, voir [Comment configurer Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Créer un nouveau projet Kubernetes

::: moniker range="vs-2017"

Une fois que vous avez installé les outils appropriés, lancez Visual Studio et créez un nouveau projet. Sous **Cloud**, choisissez la demande de conteneurs pour le type de projet **Kubernetes.** Sélectionnez ce type de projet et choisissez **OK**.

![Capture d’écran de la création d’un nouveau projet d’application Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Dans la fenêtre de démarrage Visual Studio, recherchez *Kubernetes*et choisissez **l’application de conteneurs pour Kubernetes**.

![Capture d’écran de la création d’un nouveau projet d’application Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Fournir le nom du projet.

![Capture d’écran de la création d’un nouveau projet d’application Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Vous pouvez alors choisir le type d’application Web ASP.NET Core à créer. Choisissez **Application web**. L’option habituelle **Enable Docker Support** n’apparaît pas sur ce dialogue.  Le support Docker est activé par défaut pour une application de conteneurs pour Kubernetes.

::: moniker range="vs-2017"

![Capture d’écran de la sélection d’applications web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Capture d’écran de la sélection d’applications web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Ajouter le soutien de Kubernetes à un projet existant

Vous pouvez également ajouter le support Kubernetes à un projet d’application Web ASP.NET Core existant. Pour ce faire, cliquez à droite sur le projet, et choisissez **Add** > **Container Orchestrator Support**.

::: moniker range="vs-2017"

![Capture d’écran de l’élément du menu Add Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Capture d’écran de l’élément du menu Add Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

Dans la boîte de dialogue, sélectionnez **Kubernetes/Helm** et choisissez **OK**.

![Capture d’écran de Add Container Orchestrator dialog box](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Ce que Visual Studio crée pour vous

Après avoir créé une nouvelle application de conteneurs pour le projet **Kubernetes** ou ajouté le support orchestrateur de conteneurs Kubernetes à un projet existant, vous voyez des fichiers supplémentaires dans votre projet qui facilitent le déploiement à Kubernetes.

::: moniker range="vs-2017"

![Capture d’écran de Solution Explorer après avoir ajouté le support De Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Capture d’écran de Solution Explorer après avoir ajouté le support De Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Les fichiers ajoutés sont les :

- un Dockerfile, qui vous permet de générer une image de conteneur Docker hébergeant cette application web. Comme vous le verrez, l’outillage Visual Studio tire parti de ce Dockerfile lors du débogage et du déploiement à Kubernetes. Si vous préférez travailler directement avec l’image Docker, vous pouvez cliquer directement sur le Dockerfile et choisir **Build Docker Image**.

   ![Capture d’écran de Build Docker Image option](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- un graphique Helm, et un dossier *graphique.* Ces fichiers yaml constituent le graphique Helm pour l’application, que vous pouvez utiliser pour le déployer à Kubernetes. Pour plus d’informations [https://www.helm.sh](https://www.helm.sh)sur Helm, voir .

- *azds.yaml*. Cela contient des paramètres pour Azure Dev Spaces, qui offre une expérience de débogage rapide et itérative dans Azure Kubernetes Service. Pour plus d’informations, consultez [la documentation Azure Dev Spaces](/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publier sur Azure Kubernetes Service (AKS)

Avec tous ces fichiers en place, vous pouvez utiliser l’IDE Visual Studio pour écrire et déboquer votre code d’application, comme vous l’avez toujours fait. Vous pouvez également utiliser [Azure Dev Spaces](/azure/dev-spaces/) pour exécuter et déboguer rapidement votre code en direct dans un cluster AKS. Pour plus d’informations, veuillez consulter le [tutoriel Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio)

Une fois que votre code fonctionne comme vous le souhaitez, vous pouvez publier directement de Visual Studio à un cluster AKS.

Pour ce faire, vous devez d’abord vérifier que vous avez tout installé tel que décrit dans la section [Conditions préalables](#prerequisites) sous l’élément pour la publication à AKS, et exécuter à travers toutes les étapes de la ligne de commande donnée dans les liens. Ensuite, configurez un profil de publication qui publie votre image de conteneur au Registre des conteneurs Azure (ACR). Ensuite, AKS peut tirer votre image de conteneur à partir d’ACR et la déployer dans le cluster.

1. Dans **Solution Explorer**, cliquez à droite sur votre *projet* et choisissez **Publish**.

   ![Capture d’écran de l’élément du menu publier](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Dans l’écran **Publier,** choisissez **le registre des conteneurs** comme cible de publication et suivez les invites à sélectionner votre registre des conteneurs. Si vous n’avez pas déjà de registre des conteneurs, choisissez **Create New Azure Container Registry** pour en créer un à partir de Visual Studio. Pour plus d’informations, consultez [Le registre des conteneurs Azure .](hosting-web-apps-in-docker.md)

   ![Capture d’écran de Pick un écran cible de publication](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. De retour dans Solution Explorer, cliquez à droite sur votre *solution* et cliquez sur **Publier sur Azure AKS**.

   ![Capture d’écran de l’élément de menu AkS d’Azure](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Choisissez votre abonnement et votre cluster AKS, ainsi que le profil de publication ACR que vous venez de créer. Cliquez sur **OK**.

   ![Capture d’écran de Publish to AKS screen](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Cela vous emmène à l’écran **Publish to Azure AKS.**

5. Choisissez le lien **Configure Helm** pour mettre à jour la ligne de commande utilisée pour installer les graphiques Helm sur le serveur.

   ![Capture d’écran du lien Configure Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   La mise à jour de la ligne de commande est utile s’il existe des arguments personnalisés de ligne de commande que vous souhaitez spécifier, comme un contexte ou un nom de graphique différents de Kubernetes.

   ![Capture d’écran de l’écran configuré Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Lorsque vous êtes prêt à vous déployer, cliquez sur le bouton **Publier** pour publier votre application sur AKS.

   ![Capture d’écran de la publication sur l’écran AkS Azure](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Félicitations ! Vous pouvez maintenant utiliser la pleine puissance de Visual Studio pour tout le développement de votre application Kubernetes.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur le développement de Kubernetes sur Azure en lisant la [documentation AKS](/azure/aks).

En savoir plus sur Azure Dev Spaces en lisant la [documentation Azure Dev Spaces](/azure/dev-spaces/)
