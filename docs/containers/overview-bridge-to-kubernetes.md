---
title: Comment fonctionne Bridge to Kubernetes
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Décrit les processus d’utilisation de Bridge vers Kubernetes pour connecter votre ordinateur de développement à votre cluster Kubernetes
keywords: Pont vers Kubernetes, Dockr, Kubernetes, Azure, conteneurs
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 838589e0dd81232de25b88989d621a07fb22f972
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043053"
---
# <a name="how-bridge-to-kubernetes-works"></a>Comment fonctionne Bridge to Kubernetes

Bridge vers Kubernetes vous permet d’exécuter et de déboguer du code sur votre ordinateur de développement, tout en étant connecté à votre cluster Kubernetes avec le reste de votre application ou de vos services. Par exemple, si vous avez une architecture de microservices importante avec de nombreux services et bases de données interdépendants, la réplication de ces dépendances sur votre ordinateur de développement peut s’avérer difficile. En outre, la création et le déploiement de code sur votre cluster Kubernetes pour chaque changement de code pendant le développement en boucle interne peuvent être lents, fastidieux et difficiles à effectuer avec un débogueur.

Bridge vers Kubernetes évite d’avoir à créer et déployer votre code dans votre cluster en créant une connexion directement entre votre ordinateur de développement et votre cluster. La connexion de votre ordinateur de développement à votre cluster pendant le débogage vous permet de tester et de développer rapidement votre service dans le contexte de l’application complète sans créer une configuration Docker ou Kubernetes.

Bridge to Kubernetes redirige le trafic entre votre cluster Kubernetes connecté et votre ordinateur de développement. Grâce à cette redirection du trafic, le code sur votre ordinateur de développement et les services en cours d’exécution dans votre cluster Kubernetes peuvent communiquer comme s’ils se trouvaient dans le même cluster Kubernetes. Bridge vers Kubernetes offre également un moyen de répliquer des variables d’environnement et des volumes montés disponibles pour les modules de votre cluster Kubernetes sur votre ordinateur de développement. L’accès aux variables d’environnement et aux volumes montés sur votre ordinateur de développement vous permet de travailler rapidement sur votre code sans avoir à répliquer ces dépendances manuellement.

> [!WARNING]
> Bridge vers Kubernetes est destiné à être utilisé uniquement dans les scénarios de développement et de test. Il n’est pas prévu ou pris en charge pour une utilisation avec des clusters de production ou des services actifs en cours d’utilisation.

Vous trouverez des informations sur les fonctionnalités actuellement prises en charge et une future feuille de route pour Bridge to Kubernetes dans la feuille [de route Bridge to Kubernetes](https://github.com/microsoft/mindaro/projects/1).

## <a name="using-bridge-to-kubernetes"></a>Utilisation de Bridge pour Kubernetes

Pour utiliser Bridge to Kubernetes dans Visual Studio, vous avez besoin de [Visual studio 2019][visual-studio] version 16,7 Preview 4 ou d’une version ultérieure s’exécutant sur Windows 10 avec la charge de travail de *développement Web et ASP.net* installée, ainsi que le [pont sur lequel l’extension Kubernetes][btk-extension] est installée. Quand vous utilisez Bridge to Kubernetes pour établir une connexion à votre cluster Kubernetes, vous avez la possibilité de rediriger tout le trafic vers et à partir d’un pod existant dans le cluster vers votre ordinateur de développement.

> [!NOTE]
> Lorsque vous utilisez Bridge pour Kubernetes, vous êtes invité à indiquer le nom du service à rediriger vers votre ordinateur de développement. Cette option est un moyen pratique d’identifier un pod pour la redirection. Toute redirection entre votre cluster Kubernetes et votre ordinateur de développement est destinée à un pod.

Lorsque Bridge to Kubernetes établit une connexion à votre cluster, il :

* Il vous invite à configurer le service à remplacer sur votre cluster, le port sur votre ordinateur de développement à utiliser pour votre code et la tâche de lancement de votre code en tant qu’action ponctuelle.
* Il remplace le conteneur du pod sur le cluster par un conteneur d’agent distant qui redirige le trafic vers votre ordinateur de développement.
* Elle exécute la commande [kubectl port-forward][kubectl-port-forward] sur votre ordinateur de développement pour transférer le trafic de celui-ci vers l’agent distant s’exécutant dans votre cluster.
* Elle collecte les informations d’environnement de votre cluster à l’aide de l’agent distant. Ces informations d’environnement incluent les variables d’environnement, les services visibles, les montages de volumes et les montages de secrets.
* Configure l’environnement dans Visual Studio afin que le service sur votre ordinateur de développement puisse accéder aux mêmes variables que s’il s’exécutait sur le cluster.
* Il met à jour votre fichier hosts pour mapper les services sur votre cluster à des adresses IP locales sur votre ordinateur de développement. Ces entrées de fichier hosts permettent au code s’exécutant sur votre ordinateur de développement d’adresser des demandes à d’autres services s’exécutant dans votre cluster. Pour mettre à jour votre fichier hosts, Bridge to Kubernetes demande l’accès administrateur sur votre ordinateur de développement lors de la connexion à votre cluster.
* Il démarre l’exécution et le débogage de votre code sur votre ordinateur de développement. Si nécessaire, Bridge to Kubernetes libère les ports requis sur votre ordinateur de développement en arrêtant les services ou les processus qui utilisent actuellement ces ports.

Après avoir établi une connexion à votre cluster, vous pouvez exécuter et déboguer du code en mode natif sur votre ordinateur, sans conteneur, et le code peut interagir directement avec le reste de votre cluster. Tout trafic réseau que l’agent distant reçoit est redirigé vers le port local spécifié pendant la connexion, de sorte que votre code s’exécutant en mode natif peut accepter et traiter ce trafic. Les variables d’environnement, volumes et secrets de votre cluster sont mis à la disposition du code s’exécutant sur votre ordinateur de développement. En outre, en raison des entrées de fichier des hôtes et du réacheminement de port ajoutés à votre ordinateur de développement par Bridge to Kubernetes, votre code peut envoyer le trafic réseau vers les services exécutés sur votre cluster à l’aide des noms de service de votre cluster, et ce trafic est transféré aux services qui s’exécutent dans votre cluster. Le trafic est routé entre votre ordinateur de développement et votre cluster pendant toute la durée de votre connexion.

En outre, Bridge to Kubernetes permet de répliquer des variables d’environnement et des fichiers montés disponibles pour les modules de votre cluster sur votre ordinateur de développement par le biais du `KubernetesLocalProcessConfig.yaml` fichier. Vous pouvez également utiliser ce fichier pour créer des variables d’environnement et des montages de volume.

> [!NOTE]
> Pour la durée de la connexion au cluster (15 minutes supplémentaires), Bridge to Kubernetes exécute un processus appelé *EndpointManager* avec des autorisations d’administrateur sur votre ordinateur local.

> [!NOTE]
> Vous pouvez déboguer en parallèle, avec plusieurs services, mais vous devez lancer autant d’instances de Visual Studio que de services que vous souhaitez déboguer. Assurez-vous que vos services écoutent sur des ports différents localement, puis configurez-les et déboguez-les séparément. L’isolation n’est pas prise en charge dans ce scénario.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Configuration supplémentaire avec KubernetesLocalProcessConfig. YAML

Le `KubernetesLocalProcessConfig.yaml` fichier vous permet de répliquer des variables d’environnement et des fichiers montés disponibles pour vos Pod dans votre cluster. Lors de l’utilisation du développement de Visual Studio pour Bridge vers Kubernetes, le fichier KubernetesLocalConfig. YAML doit se trouver dans le même répertoire que le fichier projet pour le service que vous redirigez. Pour plus d’informations sur les options de configuration supplémentaires, voir [configure Bridge to Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Utilisation des fonctionnalités de routage pour le développement en isolation

Par défaut, Bridge to Kubernetes redirige tout le trafic d’un service vers votre ordinateur de développement. Vous avez également la possibilité d’utiliser les fonctionnalités de routage pour rediriger uniquement les demandes vers un service provenant d’un sous-domaine vers votre ordinateur de développement. Ces fonctionnalités de routage vous permettent d’utiliser Bridge to Kubernetes pour développer de manière isolée et éviter de perturber le reste du trafic dans votre cluster.

L’animation suivante montre deux développeurs qui travaillent sur le même cluster de manière isolée :

![GIF animé illustrant l’isolation](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Lorsque vous activez l’isolation, Bridge to Kubernetes effectue les opérations suivantes en plus de la connexion à votre cluster Kubernetes :

* Vérifie que Azure Dev Spaces n’est pas activé pour le cluster Kubernetes.
* Réplique le service choisi dans le cluster dans le même espace de noms et ajoute une étiquette *Routing.VisualStudio.IO/route-from=service_name* et *Routing.VisualStudio.IO/route-on-Header=kubernetes-route-As : GENERATED_NAME* annotation.
* Configure et démarre le gestionnaire de routage dans le même espace de noms sur le cluster Kubernetes. Le gestionnaire de routage utilise un sélecteur d’étiquette pour Rechercher l’étiquette *Routing.VisualStudio.IO/route-from=service_name* et l’annotation  *Routing.VisualStudio.IO/route-on-Header=kubernetes-route-As : GENERATED_NAME* lors de la configuration du routage dans votre espace de noms.

Si Bridge to Kubernetes détecte que Azure Dev Spaces est activé sur votre cluster Kubernetes, vous êtes invité à désactiver Azure Dev Spaces avant de pouvoir utiliser Bridge to Kubernetes.

Le gestionnaire de routage effectue les opérations suivantes au démarrage :

* Duplique toutes les entrées (y compris les entrées de l’équilibreur de charge) trouvées dans l’espace de noms à l’aide de la *GENERATED_NAME* pour le sous-domaine.
* Crée un bloc d’envoi pour chaque service associé à des entrées en double avec le sous-domaine *GENERATED_NAME* .
* Crée un complément d’envoi supplémentaire pour le service sur lequel vous travaillez en isolation. Cela permet d’acheminer les demandes avec le sous-domaine vers votre ordinateur de développement.
* Configure les règles de routage pour chaque envoi de bloc afin de gérer le routage pour les services avec le sous-domaine.

Le diagramme suivant illustre un cluster Kubernetes avant que Bridge to Kubernetes se connecte à votre cluster :

![Diagramme du cluster sans pont vers Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

Le diagramme suivant montre le même cluster avec Bridge to Kubernetes activé en mode d’isolation. Ici, vous pouvez voir le service dupliqué et les Pod Envoy qui prennent en charge le routage de manière isolée.

![Diagramme du cluster avec pont vers Kubernetes activé](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Lorsqu’une demande avec le sous-domaine *GENERATED_NAME* est reçue sur le cluster, un en-tête *kubernetes-route-As = GENERATED_NAME* est ajouté à la demande. Les Pod Envoy gèrent le routage qui demande au service approprié dans le cluster. Si la demande est routée vers le service sur lequel le travail est en cours d’isolation, cette demande est redirigée vers votre ordinateur de développement par l’agent distant.

Lorsqu’une demande sans le sous-domaine *GENERATED_NAME* est reçue sur le cluster, aucun en-tête n’est ajouté à la demande. Les Pod Envoy gèrent le routage qui demande au service approprié dans le cluster. Si la demande est routée vers le service qui est remplacé, cette demande est routée vers le service d’origine au lieu de l’agent distant.

> [!IMPORTANT]
> Chaque service de votre cluster doit transférer l’en-tête *kubernetes-route-As = GENERATED_NAME lors de* l’exécution de demandes supplémentaires. Par exemple, lorsque *servicea* reçoit une demande, il envoie ensuite une requête à *serviceB* avant de renvoyer une réponse. Dans cet exemple, *servicea* doit transférer l’en-tête *kubernetes-route-As = GENERATED_NAME* dans sa demande à *serviceB*. Certains langages, tels que [ASP.net][asp-net-header], peuvent avoir des méthodes pour gérer la propagation d’en-tête.

Lorsque vous vous déconnectez de votre cluster, par défaut, Bridge to Kubernetes supprime tous les Pod d’envoi et le service dupliqué.

> [!NOTE]
> Le déploiement et le service du gestionnaire de routage resteront en cours d’exécution dans votre espace de noms. Pour supprimer le déploiement et le service, exécutez les commandes suivantes pour votre espace de noms.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostics et journalisation

Lorsque vous utilisez Bridge to Kubernetes pour vous connecter à votre cluster, les journaux de diagnostic de votre cluster sont enregistrés dans le répertoire *temp* de votre ordinateur de développement dans le dossier du *pont vers Kubernetes* .

## <a name="rbac-authorization"></a>Autorisation RBAC

Kubernetes fournit des Access Control basées sur les rôles (RBAC) pour gérer les autorisations pour les utilisateurs et les groupes. Pour plus d’informations, consultez la [documentation Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) . vous pouvez définir les autorisations pour un cluster RBAC en créant un fichier YAML et en utilisant `kubectl` pour l’appliquer au cluster. 

Pour définir des autorisations sur le cluster, créez ou modifiez un fichier YAML tel que *Permissions. yml* comme suit, à l’aide de votre propre espace de noms pour `<namespace>` et des sujets (utilisateurs et groupes) qui ont besoin d’un accès.

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: bridgetokubernetes-<namespace>
  namespace: development
subjects:
  - kind: User
    name: jane.w6wn8.k8s.ginger.eu-central-1.aws.gigantic.io
    apiGroup: rbac.authorization.k8s.io
  - kind: Group
    name: dev-admin
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: admin
  apiGroup: rbac.authorization.k8s.io
```

Appliquez les autorisations à l’aide de la commande :

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Limites

Bridge vers Kubernetes présente les limitations suivantes :

* Un pod ne peut avoir qu’un seul conteneur en cours d’exécution dans ce Pod pour que Bridge puisse se connecter à Kubernetes.
* Actuellement, les gousses de pont à Kubernetes doivent être des conteneurs Linux. Les conteneurs Windows ne sont pas pris en charge.
* Bridge to Kubernetes a besoin d’autorisations élevées pour s’exécuter sur votre ordinateur de développement afin de modifier votre fichier hosts.
* Bridge to Kubernetes ne peut pas être utilisé sur des clusters avec Azure Dev Spaces activé.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Pont vers Kubernetes et clusters avec Azure Dev Spaces activé

Vous ne pouvez pas utiliser Bridge pour Kubernetes sur un cluster avec Azure Dev Spaces activé. Si vous souhaitez utiliser Bridge pour Kubernetes sur un cluster avec Azure Dev Spaces activé, vous devez désactiver Azure Dev Spaces avant de vous connecter à votre cluster.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à utiliser Bridge to Kubernetes pour vous connecter à votre ordinateur de développement local à votre cluster, consultez [utiliser Bridge to Kubernetes](bridge-to-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md
