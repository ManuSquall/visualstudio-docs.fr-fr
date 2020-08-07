---
title: Didacticiel sur les outils Kubernetes | Microsoft Docs
ms.date: 06/08/2018
ms.topic: tutorial
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 7778019e73119a4b8b1a5842bb7a8c04ef017143
ms.sourcegitcommit: 50bbb62525c91c5a31bab57e1caf37c5638872c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87913301"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Prise en main des outils Kubernetes de Visual Studio

Les outils de Kubernetes de Visual Studio permettent de rationaliser le développement d’applications en conteneur ciblant Kubernetes. Visual Studio peut créer automatiquement les fichiers de configuration en tant que code nécessaires pour prendre en charge le déploiement de Kubernetes, tels que les graphiques fichiers dockerfile et Helm. Vous pouvez déboguer votre code dans un cluster Azure Kubernetes service (AKS) en direct à l’aide d’Azure Dev Spaces ou publier directement sur un cluster AKS à partir de Visual Studio.

Ce didacticiel décrit l’utilisation de Visual Studio pour ajouter la prise en charge de Kubernetes à un projet et sa publication sur AKS. Si vous êtes principalement intéressé par l’utilisation de [Azure dev Spaces](/azure/dev-spaces/) pour déboguer et tester votre projet s’exécutant dans AKS, vous pouvez accéder au [didacticiel Azure dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio) à la place.

## <a name="prerequisites"></a>Prérequis

Pour tirer parti de cette nouvelle fonctionnalité, vous avez besoin des éléments suivants :

::: moniker range="vs-2017"
- La dernière version de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) avec la charge de travail *développement Web et ASP.net* .
- [Kubernetes Tools pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponible en téléchargement séparé.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) avec la charge de travail *Développement ASP.NET et web*.
::: moniker-end
- [Bureau](https://store.docker.com/editions/community/docker-ce-desktop-windows) de station d’accueil installé sur votre station de travail de développement (autrement dit, dans lequel vous exécutez Visual Studio), si vous souhaitez générer des images de station d’accueil, déboguer des conteneurs d’ancrage en local ou publier sur AKS. (L’ancrage n’est *pas* requis pour la génération et le débogage des conteneurs d’ancrage dans AKS à l’aide de Azure dev Spaces.)
::: moniker range="vs-2017"
- Si vous souhaitez publier sur AKS à partir de Visual Studio (*non* requis pour le débogage dans AKS à l’aide de Azure dev Spaces) :

    1. Les [outils de publication AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibles sous forme de téléchargement distinct.

    1. Cluster Azure Kubernetes Service. Pour plus d’informations, consultez [création d’un cluster AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Veillez à [vous connecter au cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) à partir de votre station de travail de développement.

    1. Helm CLI installée sur votre station de travail de développement. Pour plus d’informations, consultez [installation de Helm](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Helm configuré sur votre cluster AKS à l’aide de la `helm init` commande. Pour plus d’informations sur la procédure à suivre, voir [How to configure Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Créer un nouveau projet Kubernetes

::: moniker range="vs-2017"

Une fois que vous avez installé les outils appropriés, lancez Visual Studio et créez un nouveau projet. Sous **Cloud**, choisissez le type **de projet application conteneur pour Kubernetes** . Sélectionnez ce type de projet et choisissez **OK**.

![Capture d’écran de la création d’un projet d’application Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Dans la fenêtre de démarrage de Visual Studio, recherchez *Kubernetes*, puis choisissez l' **application conteneur pour Kubernetes**.

![Capture d’écran de la création d’un projet d’application Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Indiquez le nom du projet.

![Capture d’écran de la création d’un projet d’application Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Vous pouvez ensuite choisir le type d’ASP.NET Core application Web à créer. Choisissez **Application web**. L’option d’activation de la **prise en charge de l’ancrer** habituelle n’apparaît pas dans cette boîte de dialogue.  La prise en charge de l’ancrage est activée par défaut pour une application de conteneur pour Kubernetes.

::: moniker range="vs-2017"

![Capture d’écran de la sélection de l’application Web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Capture d’écran de la sélection de l’application Web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Ajouter la prise en charge de Kubernetes à un projet existant

Vous pouvez également ajouter la prise en charge de Kubernetes à un projet d’application Web ASP.NET Core existant. Pour ce faire, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**la  >  **prise en charge de Container Orchestrator**.

::: moniker range="vs-2017"

![Capture d’écran de l’élément de menu Add Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Capture d’écran de l’élément de menu Add Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

Dans la boîte de dialogue, sélectionnez **Kubernetes/Helm** , puis choisissez **OK**.

![Capture d’écran de la boîte de dialogue Ajouter un conteneur d’Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Ce que Visual Studio crée pour vous

Après avoir créé une nouvelle **application conteneur pour** le projet Kubernetes ou ajouté la prise en charge d’Orchestrator de conteneur Kubernetes à un projet existant, vous voyez des fichiers supplémentaires dans votre projet qui facilitent le déploiement dans Kubernetes.

::: moniker range="vs-2017"

![Capture d’écran de Explorateur de solutions après l’ajout de la prise en charge de Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Capture d’écran de Explorateur de solutions après l’ajout de la prise en charge de Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Les fichiers ajoutés sont les suivants :

- un fichier dockerfile, qui vous permet de générer une image de conteneur d’ancrage qui héberge cette application Web. Comme vous le verrez, les outils Visual Studio tirent parti de ce fichier dockerfile lors du débogage et du déploiement sur Kubernetes. Si vous préférez travailler directement avec l’image de l’Ancreur, vous pouvez cliquer avec le bouton droit sur le fichier dockerfile et choisir générer une image de l' **ancreur**.

   ![Capture d’écran de l’option de l’image de la station de conception](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- un graphique Helm et un dossier *Charts* . Ces fichiers YAML composent le graphique Helm de l’application, que vous pouvez utiliser pour le déployer sur Kubernetes. Pour plus d’informations sur Helm, consultez [https://www.helm.sh](https://www.helm.sh) .

- *azds.yaml*. Il contient les paramètres de Azure Dev Spaces, qui offre une expérience de débogage rapide et itérative dans le service Azure Kubernetes. Pour plus d’informations, consultez [la documentation Azure dev Spaces](/azure/dev-spaces/azure-dev-spaces).

:::moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publier sur le service Azure Kubernetes (AKS)

Une fois tous ces fichiers en place, vous pouvez utiliser l’IDE de Visual Studio pour écrire et déboguer votre code d’application, comme vous le feriez toujours. Vous pouvez également utiliser [Azure dev Spaces](/azure/dev-spaces/) pour exécuter et déboguer rapidement votre code qui s’exécute en temps réel dans un cluster AKS. Pour plus d’informations, veuillez vous référer au [didacticiel Azure dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio)

Une fois que votre code fonctionne comme vous le souhaitez, vous pouvez le publier directement à partir de Visual Studio vers un cluster AKS.

Pour ce faire, vous devez d’abord vérifier que vous avez installé tout ce qui est décrit dans la section [conditions préalables](#prerequisites) sous l’élément à publier dans AKS et exécuter toutes les étapes de la ligne de commande indiquées dans les liens. Puis, configurez un profil de publication qui publie votre image conteneur sur Azure Container Registry (ACR). Ensuite, AKS peut extraire votre image de conteneur de ACR et la déployer dans le cluster.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre *projet* et choisissez **publier**.

   ![Capture d’écran de l’élément de menu publier](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Dans l’écran **publier** , choisissez **Container Registry** comme cible de publication, puis suivez les invites pour sélectionner votre registre de conteneurs. Si vous ne disposez pas déjà d’un registre de conteneurs, choisissez **créer un nouveau Azure Container Registry** pour en créer un à partir de Visual Studio. Pour plus d’informations, consultez [publier votre conteneur sur Azure Container Registry](hosting-web-apps-in-docker.md).

   ![Capture d’écran de l’écran choisir une cible de publication](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Dans Explorateur de solutions, cliquez avec le bouton droit sur votre *solution* , puis cliquez sur **publier sur Azure AKS**.

   ![Capture d’écran de l’élément de menu publier sur Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Choisissez votre abonnement et votre cluster AKS, ainsi que le profil de publication ACR que vous venez de créer. Cliquez ensuite sur **OK**.

   ![Capture d’écran de l’écran publier sur AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Vous accédez à l’écran **publier sur Azure AKS** .

5. Cliquez sur le lien **configurer Helm** pour mettre à jour la ligne de commande utilisée pour installer les graphiques Helm sur le serveur.

   ![Capture d’écran du lien configurer Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   La mise à jour de la ligne de commande est utile si vous souhaitez spécifier des arguments de ligne de commande personnalisés, tels qu’un contexte de Kubernetes ou un nom de graphique différent.

   ![Capture d’écran de l’écran de configuration de Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Lorsque vous êtes prêt à effectuer le déploiement, cliquez sur le bouton **publier** pour publier votre application sur AKS.

   ![Capture d’écran de l’écran publier sur Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Félicitations ! Vous pouvez maintenant utiliser toute la puissance de Visual Studio pour l’ensemble de votre développement d’applications Kubernetes.

## <a name="remove-kubernetes-support"></a>Supprimer la prise en charge de Kubernetes

1. Dans **Explorateur de solutions**, sous **propriétés**, ouvrez *launchSettings.js*.

1. Supprimez le **conteneur de section dans Kubernetes**.

1. Si vous revenez à Dockr compose, sélectionnez ce projet dans **Explorateur de solutions**, cliquez avec le bouton droit et choisissez **définir comme projet de démarrage**.

1. Facultatif Vous pouvez également supprimer les autres artefacts répertoriés précédemment dans l’article, tels que le dossier **graphiques** et *azds. YAML*.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le développement Kubernetes sur Azure, consultez la [documentation de AKS](/azure/aks).

En savoir plus sur Azure Dev Spaces en lisant la [documentation de Azure dev Spaces](/azure/dev-spaces/)
