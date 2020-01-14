---
title: Didacticiel sur les outils Kubernetes | Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: f5868f97301eba62d16ea68cdaa0c97c8e20edd1
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916947"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Prise en main des outils Kubernetes de Visual Studio

Les outils de Kubernetes de Visual Studio permettent de rationaliser le développement d’applications en conteneur ciblant Kubernetes. Visual Studio peut créer automatiquement les fichiers de configuration en tant que code nécessaires pour prendre en charge le déploiement de Kubernetes, tels que les graphiques fichiers dockerfile et Helm. Vous pouvez déboguer votre code dans un cluster Azure Kubernetes service (AKS) en direct à l’aide d’Azure Dev Spaces ou publier directement sur un cluster AKS à partir de Visual Studio.

Ce didacticiel décrit l’utilisation de Visual Studio pour ajouter la prise en charge de Kubernetes à un projet et sa publication sur AKS. Si vous êtes principalement intéressé par l’utilisation de [Azure dev Spaces](/azure/dev-spaces/) pour déboguer et tester votre projet s’exécutant dans AKS, vous pouvez accéder au [didacticiel Azure dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio) à la place.

## <a name="prerequisites"></a>Configuration requise

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

    1. Helm CLI installée sur votre station de travail de développement. Pour plus d’informations, consultez [installation de Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. Helm configuré sur votre cluster AKS à l’aide de la commande `helm init`. Pour plus d’informations sur la procédure à suivre, voir [How to configure Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Créer un nouveau projet Kubernetes

::: moniker range="vs-2017"

Une fois que vous avez installé les outils appropriés, lancez Visual Studio et créez un nouveau projet. Sous **Cloud**, choisissez le type **de projet application conteneur pour Kubernetes** . Sélectionnez ce type de projet et choisissez **OK**.

![Screenshot of creating a new Kubernetes app project](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Dans la fenêtre de démarrage de Visual Studio, recherchez *Kubernetes*, puis choisissez l' **application conteneur pour Kubernetes**.

![Screenshot of creating a new Kubernetes app project](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Provide the project name.

![Screenshot of creating a new Kubernetes app project](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

You can then choose which type of ASP.NET Core web application to create. Choisissez **Application web**. The usual **Enable Docker Support** option does not appear on this dialog.  Docker support is enabled by default for a container application for Kubernetes.

::: moniker range="vs-2017"

![Screenshot of web app selection](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot of web app selection](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Add Kubernetes support to an existing project

Alternatively, you can add Kubernetes support to an existing ASP.NET Core web application project. To do this, right-click on the project, and choose **Add** > **Container Orchestrator Support**.

::: moniker range="vs-2017"

![Screenshot of Add Container Orchestrator menu item](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot of Add Container Orchestrator menu item](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

In the dialog box, select **Kubernetes/Helm** and choose **OK**.

![Screenshot of Add Container Orchestrator dialog box](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>What Visual Studio creates for you

After creating a new **Container Application for Kubernetes** project or adding Kubernetes container orchestrator support to an existing project, you see some additional files in your project that facilitate deploying to Kubernetes.

::: moniker range="vs-2017"

![Screenshot of Solution Explorer after adding Container Orchestrator support](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Screenshot of Solution Explorer after adding Container Orchestrator support](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

The added files are:

- a Dockerfile, which allows you to generate a Docker container image hosting this web application. As you'll see, the Visual Studio tooling leverages this Dockerfile when debugging and deploying to Kubernetes. If you prefer to work directly with the Docker image, you can right-click on the Dockerfile and choose **Build Docker Image**.

   ![Screenshot of Build Docker Image option](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- a Helm chart, and a *charts* folder. These yaml files make up the Helm chart for the application, which you can use to deploy it to Kubernetes. For more information on Helm, see [https://www.helm.sh](https://www.helm.sh).

- *azds.yaml*. This contains settings for Azure Dev Spaces, which provides a rapid, iterative debugging experience in Azure Kubernetes Service. For more information, see [the Azure Dev Spaces documentation](/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publish to Azure Kubernetes Service (AKS)

With all these files in place, you can use the Visual Studio IDE to write and debug your application code, just as you always have. You can also use [Azure Dev Spaces](/azure/dev-spaces/) to quickly run and debug your code running live in an AKS cluster. For more information, please reference the [Azure Dev Spaces tutorial](/azure/dev-spaces/get-started-netcore-visualstudio)

Once you have your code running the way you want, you can publish directly from Visual Studio to an AKS cluster.

To do this, you first need to double-check that you've installed everything as described in the [Prerequisites](#prerequisites) section under the item for publishing to AKS, and run through all the command line steps given in the links. Then, set up a publish profile that publishes your container image to Azure Container Registry (ACR). Then AKS can pull your container image from ACR and deploy it into the cluster.

1. In **Solution Explorer**, right-click on your *project* and choose **Publish**.

   ![Screenshot of Publish menu item](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. In the **Publish** screen, choose **Container Registry** as the publish target, and follow the prompts to select your container registry. If you don't already have a container registry, choose **Create New Azure Container Registry** to create one from Visual Studio. For more information, see [Publish your container to Azure Container Registry](hosting-web-apps-in-docker.md).

   ![Screenshot of Pick a publish target screen](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Back in Solution Explorer, right click on your *solution* and click **Publish to Azure AKS**.

   ![Screenshot of Publish to Azure AKS menu item](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Choose your subscription and your AKS cluster, along with the ACR publish profile that you just created. Cliquez ensuite sur **OK**.

   ![Screenshot of Publish to AKS screen](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   This takes you to the **Publish to Azure AKS** screen.

5. Choose the **Configure Helm** link to update the command line used to install the Helm charts on the server.

   ![Screenshot of Configure Helm link](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Updating the command line is useful if there are custom command line arguments that you wish to specify, such as a different Kubernetes context or chart name.

   ![Screenshot of Helm configure screen](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. When you are ready to deploy, click the **Publish** button to publish your application to AKS.

   ![Screenshot of publish to Azure AKS screen](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Félicitations ! You can now use the full power of Visual Studio for all your Kubernetes app development.

## <a name="next-steps"></a>Étapes suivantes :

Pour en savoir plus sur le développement Kubernetes sur Azure, consultez la [documentation de AKS](/azure/aks).

En savoir plus sur Azure Dev Spaces en lisant la [documentation de Azure dev Spaces](/azure/dev-spaces/)
