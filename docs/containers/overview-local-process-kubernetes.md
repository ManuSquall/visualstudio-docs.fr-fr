---
title: Fonctionnement de Processus local avec Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Décrit les processus d’utilisation de Processus local avec Kubernetes pour connecter votre ordinateur de développement à votre cluster Kubernetes
keywords: Processus local avec Kubernetes, docker, Kubernetes, Azure, conteneurs
monikerRange: '>=vs-2019'
ms.openlocfilehash: adde9d8ecab93bdb6f0aebbd74730ef60bd80cf6
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454334"
---
# <a name="how-local-process-with-kubernetes-works"></a>Fonctionnement de Processus local avec Kubernetes

Processus local avec Kubernetes vous permet d’exécuter et de déboguer votre code sur votre ordinateur de développement tout en restant connecté à votre cluster Kubernetes avec le reste de votre application ou de vos services. Par exemple, si vous avez une architecture de microservices importante avec de nombreux services et bases de données interdépendants, la réplication de ces dépendances sur votre ordinateur de développement peut s’avérer difficile. En outre, la création et le déploiement de code sur votre cluster Kubernetes pour chaque changement de code pendant le développement en boucle interne peuvent être lents, fastidieux et difficiles à effectuer avec un débogueur.

Local Process with Kubernetes vous évite d’avoir à créer et à déployer votre code sur votre cluster en créant une connexion directement entre votre ordinateur de développement et votre cluster. La connexion de votre ordinateur de développement à votre cluster pendant le débogage vous permet de tester et de développer rapidement votre service dans le contexte de l’application complète sans créer une configuration Docker ou Kubernetes.

Local Process with Kubernetes redirige le trafic entre votre cluster Kubernetes connecté et votre ordinateur de développement. Grâce à cette redirection du trafic, le code sur votre ordinateur de développement et les services en cours d’exécution dans votre cluster Kubernetes peuvent communiquer comme s’ils se trouvaient dans le même cluster Kubernetes. Local Process with Kubernetes offre également un moyen de répliquer des variables d’environnement et des volumes montés disponibles pour les pods dans votre cluster Kubernetes sur votre ordinateur de développement. L’accès aux variables d’environnement et aux volumes montés sur votre ordinateur de développement vous permet de travailler rapidement sur votre code sans avoir à répliquer ces dépendances manuellement.

## <a name="using-local-process-with-kubernetes"></a>Utilisation de Processus local avec Kubernetes

Pour utiliser le processus local avec Kubernetes dans Visual Studio, vous avez besoin de [Visual studio 2019][visual-studio] version 16,7 Preview 4 ou d’une version ultérieure s’exécutant sur Windows 10 avec la charge de travail de *développement Web et ASP.net* installée, et l' [extension Kubernetes de processus local][lpk-extension] installée. Lorsque vous utilisez Processus local avec Kubernetes pour établir une connexion à votre cluster Kubernetes, vous avez la possibilité de rediriger tout le trafic à destination et en provenance d’un pod existant dans le cluster vers votre ordinateur de développement.

> [!NOTE]
> Lorsque vous utilisez Processus local avec Kubernetes, vous êtes invité à indiquer le nom du service pour la redirection vers votre ordinateur de développement. Cette option est un moyen pratique d’identifier un pod pour la redirection. Toute redirection entre votre cluster Kubernetes et votre ordinateur de développement est destinée à un pod.

Lorsque Processus local avec Kubernetes établit une connexion à votre cluster :

* Il vous invite à configurer le service à remplacer sur votre cluster, le port sur votre ordinateur de développement à utiliser pour votre code et la tâche de lancement de votre code en tant qu’action ponctuelle.
* Il remplace le conteneur du pod sur le cluster par un conteneur d’agent distant qui redirige le trafic vers votre ordinateur de développement.
* Elle exécute la commande [kubectl port-forward][kubectl-port-forward] sur votre ordinateur de développement pour transférer le trafic de celui-ci vers l’agent distant s’exécutant dans votre cluster.
* Elle collecte les informations d’environnement de votre cluster à l’aide de l’agent distant. Ces informations d’environnement incluent les variables d’environnement, les services visibles, les montages de volumes et les montages de secrets.
* Configure l’environnement dans Visual Studio afin que le service sur votre ordinateur de développement puisse accéder aux mêmes variables que s’il s’exécutait sur le cluster.  
* Il met à jour votre fichier hosts pour mapper les services sur votre cluster à des adresses IP locales sur votre ordinateur de développement. Ces entrées de fichier hosts permettent au code s’exécutant sur votre ordinateur de développement d’adresser des demandes à d’autres services s’exécutant dans votre cluster. Pour mettre à jour votre fichier hosts, Processus local avec Kubernetes vous demande un accès administrateur sur votre ordinateur de développement lors de la connexion à votre cluster.
* Il démarre l’exécution et le débogage de votre code sur votre ordinateur de développement. Si nécessaire, Processus local avec Kubernetes libère les ports requis sur votre ordinateur de développement en arrêtant les services ou les processus qui utilisent actuellement ces ports.

Après avoir établi une connexion à votre cluster, vous pouvez exécuter et déboguer du code en mode natif sur votre ordinateur, sans conteneur, et le code peut interagir directement avec le reste de votre cluster. Tout trafic réseau que l’agent distant reçoit est redirigé vers le port local spécifié pendant la connexion, de sorte que votre code s’exécutant en mode natif peut accepter et traiter ce trafic. Les variables d’environnement, volumes et secrets de votre cluster sont mis à la disposition du code s’exécutant sur votre ordinateur de développement. Par ailleurs, en raison des entrées de fichier hosts et du transfert de port que le Processus local avec Kubernetes a ajoutés à votre ordinateur de développement, votre code peut envoyer le trafic réseau à des services s’exécutant sur votre cluster en utilisant les noms de service de votre cluster, et ce trafic est transféré aux services s’exécutant dans votre cluster. Le trafic est routé entre votre ordinateur de développement et votre cluster pendant toute la durée de votre connexion.

## <a name="diagnostics-and-logging"></a>Diagnostics et journalisation

Lorsque vous utilisez Processus local avec Kubernetes pour vous connecter à votre cluster, les journaux de diagnostic de votre cluster sont enregistrés dans le [répertoire temporaire][azds-tmp-dir] de votre ordinateur de développement.

## <a name="limitations"></a>Limites

Un processus local avec Kubernetes présente les limitations suivantes :

* Un processus local avec Kubernetes redirige le trafic pour un seul service vers votre ordinateur de développement. Vous ne pouvez pas utiliser un processus local avec Kubernetes pour rediriger plusieurs services en même temps.
* Pour pouvoir se connecter à un service, celui-ci doit être sauvegardé par un seul pod. Vous ne pouvez pas vous connecter à un service comportant plusieurs pod, tel qu’un service avec des réplicas.
* Un pod ne peut comprendre qu’un seul conteneur en cours d’exécution pour qu’un processus local avec Kubernetes se connecte correctement. Un processus local avec Kubernetes ne peut pas se connecter à des services comportant des pods ayant des conteneurs supplémentaires, tels que des conteneurs sidecar injectés par des mailles de services.
* Un processus local avec Kubernetes a besoin d’autorisations élevées pour s’exécuter sur votre ordinateur de développement afin de modifier votre fichier hosts.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à utiliser le processus local avec Kubernetes pour vous connecter à votre ordinateur de développement local à votre cluster, consultez [utiliser le processus local avec Kubernetes](local-process-kubernetes.md).

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro