---
title: 'Didacticiel : connecter des machines de développement avec Bridge à Kubernetes'
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: Connectez votre ordinateur de développement à un cluster Kubernetes avec Bridge to Kubernetes avec Visual Studio.
keywords: Bridge to Kubernetes, Azure Dev Spaces, dev Spaces, Dockr, Kubernetes, Azure, containers
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046116"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>Didacticiel : utiliser Bridge pour Kubernetes pour connecter vos clusters et vos ordinateurs de développement

Dans ce didacticiel, vous allez apprendre à utiliser Bridge to Kubernetes pour rediriger le trafic entre votre cluster Kubernetes et le code qui s’exécute sur votre ordinateur de développement. 

Ce guide fournit également un script pour le déploiement d’un exemple d’application volumineux avec plusieurs microservices sur un cluster Kubernetes.

En savoir plus sur Bridge to Kubernetes avec l’article [How Bridge to Kubernetes Works](overview-bridge-to-kubernetes.md).

## <a name="prerequisites"></a>Prérequis

- Un cluster Kubernetes
- [Visual Studio 2019][visual-studio] version 16,7 Preview 4 ou une version ultérieure s’exécutant sur Windows 10.
- [Extension de pont vers Kubernetes installée][btk-extension]

## <a name="about-the-data"></a>À propos des données

Ce didacticiel utilise Bridge to Kubernetes pour développer une version de microservice d’un exemple d’application TODO simple sur un cluster Kubernetes. Cet [exemple d’application todo][todo-app-github], à l’aide de Visual Studio, a été adapté à partir du code fourni par [TodoMVC](http://todomvc.com). 

 Ces étapes doivent fonctionner avec n’importe quel cluster Kubernetes. Par conséquent, si vous avez déjà votre propre application en cours d’exécution sur un cluster Kubernetes, vous pouvez toujours suivre les étapes ci-dessous et utiliser les noms de vos propres services.

L’exemple d’application TODO est constitué d’un serveur frontal et d’un backend qui fournit un stockage persistant. Cet exemple étendu ajoute un composant de statistiques et décompose l’application en plusieurs microservices, en particulier :

- Le serveur frontal appelle l’API de base de données pour conserver et mettre à jour les éléments TODO ;
- Le service de l’API de base de données s’appuie sur une base de données Mongo pour conserver les éléments TODO ;
- Le serveur frontal écrit les événements Add, Complete et Delete dans une file d’attente RabbitMQ ;
- Un travailleur des statistiques reçoit les événements de la file d’attente RabbitMQ et met à jour un cache ReDim ;
- Une API de statistiques expose les statistiques mises en cache pour le serveur frontal à afficher.

En tout, cette application TODO étendue est composée de six composants reliés entre eux.


## <a name="check-the-cluster"></a>Vérifier le cluster

Ouvrez une invite de commandes et vérifiez que l' `kubectl` est installé et sur le chemin d’accès, le cluster que vous souhaitez utiliser est disponible et prêt, puis définissez le contexte sur ce cluster.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

où {Context-Name} est le nom du contexte pour le cluster que vous souhaitez utiliser pour l’exemple todo-App.

## <a name="deploy-the-application"></a>Déployer l’application

Clonez le [référentiel mindaro](https://github.com/Microsoft/mindaro) et ouvrez une fenêtre de commande avec le dossier de travail en cours dans *Samples/todo-App*.

Créez un espace de noms pour l’exemple.

```cmd
kubectl create namespace todo-app
```

Ensuite, appliquez le manifeste de déploiement :

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Il s’agit d’un déploiement simple qui expose le serveur frontal à l’aide d’un service de type `LoadBalancer` . Attendez que toutes les Pod soient en cours d’exécution et que l’adresse IP externe du `frontend` service soit disponible.

Si vous effectuez un test avec MiniKube, vous devrez utiliser `minikube tunnel` pour résoudre une adresse IP externe. Si vous utilisez AKS ou un autre fournisseur Kubernetes basé sur le Cloud, une adresse IP externe est attribuée automatiquement. Utilisez la commande suivante pour surveiller le `frontend` service en attente jusqu’à ce qu’il soit opérationnel :

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Accédez à l’application à l’aide de l’adresse IP externe et du port local (le premier numéro de la colonne PORT (S)).

```
http://{external-ip}:{local-port}
```

Testez l’application en cours d’exécution dans le navigateur. À mesure que vous ajoutez, terminez et supprimez des éléments TODO, vous remarquerez que la page de statistiques est mise à jour avec les métriques attendues.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Connexion à votre cluster et débogage d’un service

Ouvrez *samples\todo-app\database-api\database-API.csproj* dans Visual Studio. Dans le projet, sélectionnez **pont vers Kubernetes** dans la liste déroulante paramètres de lancement, comme indiqué ci-dessous.

![Choisir un pont vers Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Cliquez sur le bouton Démarrer en regard de *pont vers Kubernetes*. Dans la boîte de dialogue **créer un profil pour Bridge to Kubernetes** :

- Sélectionnez le nom de votre cluster.
- Sélectionnez *TODO-App* pour votre espace de noms.
- Sélectionnez *Database-API* pour le service à rediriger.
- Sélectionnez la même URL que celle utilisée précédemment pour lancer votre navigateur, http://{External-IP} : {local-port}

![Choisir un pont de pont vers un cluster Kubernetes](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Indiquez si vous souhaitez ou non utiliser l’isolation, ce qui signifie que les autres personnes qui utilisent le cluster ne seront pas affectées par vos modifications. Ce mode d’isolation s’effectue en acheminant vos demandes vers votre copie de chaque service affecté, mais en acheminant normalement tout le reste du trafic. Vous trouverez plus d’explications sur le [fonctionnement de Bridge to Kubernetes][btk-overview-routing].

Cliquez sur **OK**. Tout le trafic du cluster Kubernetes est redirigé pour le service *de l’API de base de données* vers la version de votre application en cours d’exécution sur votre ordinateur de développement. Bridge to Kubernetes achemine également tout le trafic sortant de l’application vers votre cluster Kubernetes.

> [!NOTE]
> Vous serez invité à autoriser l’exécution du *EndpointManager* avec élévation de privilèges et à modifier votre fichier hosts.

Votre ordinateur de développement est connecté lorsque la barre d’État indique que vous êtes connecté au `database-api` service.

![Ordinateur de développement connecté](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Lors des lancements suivants, vous ne serez pas invité à utiliser la boîte **de dialogue créer un profil pour Bridge to Kubernetes** . Vous mettez à jour ces paramètres dans le **débogage** dans les propriétés du projet.

Une fois votre ordinateur de développement connecté, le trafic commence à être redirigé vers votre ordinateur de développement pour le service que vous remplacez.

> [!NOTE]
> Pour modifier le profil de débogage ultérieurement, par exemple, si vous souhaitez effectuer un test avec un autre service Kubernetes, choisissez **Déboguer** les  >  **Propriétés de débogage**, puis cliquez sur le bouton **modifier** .

## <a name="set-a-break-point"></a>Définir un point d’arrêt

Ouvrez MongoHelper. cs et cliquez n’importe où sur la ligne 68 dans la méthode CreateTask pour y placer votre curseur. Définissez un point d’arrêt en appuyant sur *F9* ou **en sélectionnant**  >  **basculer le point d’arrêt**.

Accédez à l’exemple d’application en ouvrant l’URL publique (l’adresse IP externe du service frontal). Pour reprendre le service, appuyez sur **F5** ou cliquez sur **Déboguer**  >  **Continuer**.

Supprimez le point d’arrêt en plaçant votre curseur sur la ligne avec le point d’arrêt et en appuyant sur **F9**.

> [!NOTE]
> Par défaut, l’arrêt de la tâche de débogage déconnecte également votre ordinateur de développement de votre cluster Kubernetes. Vous pouvez modifier ce comportement en modifiant **déconnecter après le débogage** `false` dans la section **outils de débogage Kubernetes** de la   >  boîte de dialogue **options** des outils. Après la mise à jour de ce paramètre, votre ordinateur de développement reste connecté lorsque vous arrêtez et démarrez le débogage. Pour déconnecter votre ordinateur de développement de votre cluster, cliquez sur le bouton **Déconnecter** de la barre d’outils.
>
>![Capture d’écran des options de débogage Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Configuration supplémentaire

Bridge vers Kubernetes peut gérer le trafic de routage et répliquer les variables d’environnement sans aucune configuration supplémentaire. Si vous devez télécharger des fichiers montés sur le conteneur de votre cluster Kubernetes, tel qu’un fichier élément configmap, vous pouvez créer un `KubernetesLocalProcessConfig.yaml` pour télécharger ces fichiers sur votre ordinateur de développement. Pour plus d’informations, consultez [utilisation de KubernetesLocalProcessConfig. YAML pour une configuration supplémentaire avec pour Bridge vers Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Utilisation de la journalisation et des diagnostics

Vous pouvez trouver les journaux de diagnostic dans le `Bridge to Kubernetes` répertoire dans le répertoire *temp* de votre ordinateur de développement.

## <a name="next-steps"></a>Étapes suivantes

Découvrez le fonctionnement de Bridge to Kubernetes.

> [!div class="nextstepaction"]
> [Fonctionnement de la solution Bridge to Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
