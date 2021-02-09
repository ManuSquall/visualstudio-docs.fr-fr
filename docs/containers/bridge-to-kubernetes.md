---
title: Utiliser Bridge to Kubernetes avec Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Découvrez comment utiliser Bridge pour Kubernetes avec Visual Studio pour connecter votre ordinateur de développement à un cluster Kubernetes
keywords: Bridge to Kubernetes, Azure Dev Spaces, dev Spaces, Dockr, Kubernetes, Azure, containers
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: 23d060489a13aa8e02316e253d9367e9e3372bbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859630"
---
# <a name="use-bridge-to-kubernetes"></a>Utiliser Bridge pour Kubernetes

Vous pouvez utiliser Bridge to Kubernetes pour rediriger le trafic entre votre cluster Kubernetes et le code qui s’exécute sur votre ordinateur de développement. Ce guide fournit également un script pour le déploiement d’un exemple d’application volumineux avec plusieurs microservices sur un cluster Kubernetes.

## <a name="before-you-begin"></a>Avant de commencer

Ce guide utilise l' [exemple d’application de partage de vélos][bike-sharing-github] pour illustrer la connexion de votre ordinateur de développement à un cluster Kubernetes. Si vous disposez déjà de votre propre application s’exécutant sur un cluster Kubernetes, vous pouvez toujours suivre les étapes ci-dessous et utiliser les noms de vos propres services.

### <a name="prerequisites"></a>Prérequis

* Un abonnement Azure. Si vous n’avez pas d’abonnement Azure, vous pouvez créer un [compte gratuit](https://azure.microsoft.com/free).
* [Azure CLI][azure-cli].
* [Visual Studio 2019][visual-studio] version 16,7 Preview 4 ou une version ultérieure s’exécutant sur Windows 10 avec la charge de travail de *développement Azure* installée.
* [Extension de pont vers Kubernetes installée][btk-extension].

En outre, pour les applications console .NET, installez le package NuGet *Microsoft.VisualStudio.Azure.Kubernetes.Tools.Targets*.

## <a name="create-a-kubernetes-cluster"></a>Créer un cluster Kubernetes

Créez un cluster AKS dans une [région prise en charge][supported-regions]. Les commandes ci-dessous créent un groupe de ressources nommé *MyResourceGroup* et un cluster AKS nommé *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Installation de l’exemple d’application

Installez l’exemple d’application sur votre cluster à l’aide du script fourni. Vous pouvez exécuter ce script à l’aide de l' [Azure Cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Accédez à l’exemple d’application s’exécutant sur votre cluster en ouvrant son URL publique, qui est affichée dans la sortie du script d’installation.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

Dans l’exemple ci-dessus, l’URL publique est `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Connexion à votre cluster et débogage d’un service

Sur votre ordinateur de développement, téléchargez et configurez la CLI Kubernetes pour vous connecter à votre cluster Kubernetes avec [az aks get-credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

À partir de l' [application exemple de partage de bicyclette][bike-sharing-github] référentiel dans GitHub, utilisez la liste déroulante du bouton de **code** vert, puis choisissez **ouvrir dans Visual Studio** pour cloner le référentiel localement et ouvrir le dossier dans Visual Studio. Ensuite, utilisez **fichier**  >  **ouvrir un projet** pour ouvrir le projet **app. csproj** dans le dossier *Samples/BikeSharingApp/ReservationEngine* .

Dans votre projet, sélectionnez **pont vers Kubernetes** dans la liste déroulante paramètres de lancement, comme indiqué ci-dessous.

![Choisir un pont vers Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Cliquez sur le bouton Démarrer en regard de *pont vers Kubernetes*. Dans la boîte de dialogue **créer un profil pour Bridge to Kubernetes** :

* Sélectionnez votre abonnement.
* Sélectionnez *MyAKS* pour votre cluster.
* Sélectionnez *bikeapp* pour votre espace de noms.
* Sélectionnez *reservationengine* pour le service à rediriger.
* Sélectionnez *app* pour le profil de lancement.
* Sélectionnez `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` pour l’URL de lancement de votre navigateur.

![Choisir un pont de pont vers un cluster Kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Vous ne pouvez rediriger que les services qui n’ont qu’un seul pod.

Indiquez si vous souhaitez ou non utiliser l’isolation, ce qui signifie que les autres personnes qui utilisent le cluster ne seront pas affectées par vos modifications. Ce mode d’isolation s’effectue en acheminant vos demandes vers votre copie de chaque service affecté, mais en acheminant normalement tout le reste du trafic. Vous trouverez plus d’explications sur le [fonctionnement de Bridge to Kubernetes][btk-overview-routing].

Cliquez sur **Enregistrer et commencer le débogage**.

Tout le trafic dans le cluster Kubernetes est redirigé pour le service *reservationengine* vers la version de votre application s’exécutant sur votre ordinateur de développement. Bridge to Kubernetes achemine également tout le trafic sortant de l’application vers votre cluster Kubernetes.

> [!NOTE]
> Vous serez invité à autoriser l’exécution du *EndpointManager* avec élévation de privilèges et à modifier votre fichier hosts.

Votre ordinateur de développement est connecté lorsque la barre d’État indique que vous êtes connecté au `reservationengine` service.

![Ordinateur de développement connecté](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Lors des lancements suivants, vous ne serez pas invité à utiliser la boîte **de dialogue créer un profil pour Bridge to Kubernetes** . Vous mettez à jour ces paramètres dans le **débogage** dans les propriétés du projet.

Une fois votre ordinateur de développement connecté, le trafic commence à être redirigé vers votre ordinateur de développement pour le service que vous remplacez.

## <a name="set-a-break-point"></a>Définir un point d’arrêt

Ouvrez [BikesHelper.cs][bikeshelper-cs-breakpoint], puis cliquez quelque part sur la ligne 26 pour y placer votre curseur. Définissez un point d’arrêt en appuyant sur *F9* ou **en sélectionnant**  >  **basculer le point d’arrêt**.

Accédez à l’exemple d’application en ouvrant l’URL publique. Sélectionnez **Aurelia Briggs (client)** en tant qu’utilisateur, puis sélectionnez un vélo à louer. Choisissez **louer vélo**. Revenez à Visual Studio et notez que la ligne 26 est mise en surbrillance. Le point d’arrêt que vous avez défini a suspendu le service à la ligne 26. Pour reprendre le service, appuyez sur **F5** ou cliquez sur **Déboguer**  >  **Continuer**. Revenez à votre navigateur et vérifiez que la page indique que vous avez loué le vélo.

Supprimez le point d’arrêt en plaçant votre curseur sur la ligne 26 dans `BikesHelper.cs` et en appuyant sur **F9**.

> [!NOTE]
> Par défaut, l’arrêt de la tâche de débogage déconnecte également votre ordinateur de développement de votre cluster Kubernetes. Vous pouvez modifier ce comportement en modifiant **déconnecter après le débogage** `false` dans la section **Outils** de débogage Kubernetes des options de débogage. Après la mise à jour de ce paramètre, votre ordinateur de développement reste connecté lorsque vous arrêtez et démarrez le débogage. Pour déconnecter votre ordinateur de développement de votre cluster, cliquez sur le bouton **Déconnecter** de la barre d’outils.

## <a name="additional-configuration"></a>Configuration supplémentaire

Bridge vers Kubernetes peut gérer le trafic de routage et répliquer les variables d’environnement sans aucune configuration supplémentaire. Si vous devez télécharger des fichiers montés sur le conteneur de votre cluster Kubernetes, tel qu’un fichier élément configmap, vous pouvez créer un `KubernetesLocalProcessConfig.yaml` pour télécharger ces fichiers sur votre ordinateur de développement. Pour plus d’informations, consultez [utilisation de KubernetesLocalProcessConfig. YAML pour une configuration supplémentaire avec pour Bridge vers Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Utilisation de la journalisation et des diagnostics

Vous pouvez trouver les journaux de diagnostic dans le `Bridge to Kubernetes` répertoire dans le répertoire *temp* de votre ordinateur de développement. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Supprimer l’exemple d’application de votre cluster

Utilisez le script fourni pour supprimer l’exemple d’application de votre cluster.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez le fonctionnement de Bridge to Kubernetes.

> [!div class="nextstepaction"]
> [Fonctionnement de la solution Bridge to Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation