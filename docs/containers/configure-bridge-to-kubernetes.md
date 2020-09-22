---
title: Utilisation de KubernetesLocalProcessConfig. YAML pour une configuration supplémentaire avec pour Bridge vers Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Décrit les options de configuration supplémentaires pour Bridge to Kubernetes à l’aide de KubernetesLocalProcessConfig. YAML
keywords: Bridge to Kubernetes, Azure Dev Spaces, dev Spaces, Dockr, Kubernetes, Azure, AKS, Azure Kubernetes service, containers
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: bd28921b7812689554e1dd707c500434bb021c9c
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845871"
---
# <a name="configure-bridge-to-kubernetes"></a>Configurer Bridge sur Kubernetes

Le `KubernetesLocalProcessConfig.yaml` fichier vous permet de répliquer des variables d’environnement et des fichiers montés disponibles pour vos Pod dans votre cluster AKS. Vous pouvez spécifier les actions suivantes dans un `KubernetesLocalProcessConfig.yaml` fichier :

* Téléchargez un volume et définissez le chemin d’accès à ce volume en tant que variable d’environnement.
* Rendre un service en cours d’exécution sur votre cluster disponible pour les processus en cours d’exécution sur votre ordinateur de développement.
* Créez une variable d’environnement avec une valeur de constante.

Un fichier par défaut `KubernetesLocalProcessConfig.yaml` n’est pas créé automatiquement. vous devez donc le créer manuellement à la racine de votre projet.

## <a name="download-a-volume"></a>Télécharger un volume

Sous *env*, spécifiez un *nom* et une *valeur* pour chaque volume que vous souhaitez télécharger. Le *nom* est la variable d’environnement qui sera utilisée sur votre ordinateur de développement. La *valeur* est le nom du volume et un chemin d’accès sur votre ordinateur de développement. La valeur de la *valeur* prend la forme *$ (volumeMounts : VOLUME_NAME)/Path/to/Files*.

Par exemple :

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

L’exemple ci-dessus télécharge le volume *allow-List* à partir du conteneur et définit cet emplacement ainsi que le chemin d’accès à la variable d’environnement *ALLOW_LIST_PATH*. Le comportement par défaut consiste à télécharger les fichiers vers le chemin d’accès que vous spécifiez dans un répertoire temporaire sur votre ordinateur de développement. Dans l’exemple ci-dessus, *ALLOW_LIST_PATH* a la valeur `/TEMPORARY_DIR/allow-list` . 

> [!NOTE]
> Le téléchargement d’un volume permet de télécharger tout le contenu de ce volume, quel que soit le chemin d’accès que vous avez défini. Le chemin d’accès est utilisé uniquement pour définir la variable d’environnement à utiliser sur l’ordinateur de développement. L’ajout de */allow-List* ou */path/to/Files* à la fin du jeton n’affecte en fait pas l’emplacement où le volume est rendu persistant. La variable d’environnement n’est qu’une pratique si votre application a besoin d’une référence à un fichier spécifique à l’intérieur de ce volume.

Vous avez également la possibilité de spécifier un emplacement pour télécharger le montage de volume sur votre ordinateur de développement au lieu d’utiliser un répertoire temporaire. Sous *volumeMounts*, spécifiez un *nom* et *LocalPath* pour chaque emplacement spécifique. Le *nom* est le nom de volume que vous souhaitez faire correspondre, et *LocalPath* est le chemin d’accès absolu sur votre ordinateur de développement. Par exemple :

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

L’exemple ci-dessus utilise l’entrée dans *env* pour télécharger un volume correspondant à un * \* jeton par défaut*, tel que *default-Token-1111* ou *default-Token-1234-5678-90abcdef*. Dans les cas où plusieurs volumes correspondent, le premier volume correspondant est utilisé. Tous les fichiers sont téléchargés sur `/var/run/secrets/kubernetes.io/serviceaccount` votre ordinateur de développement à l’aide de l’entrée dans *volumeMounts*. La variable d’environnement *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* a la valeur `/var/run/secrets/kubernetes.io/serviceaccount` .

## <a name="make-a-service-available"></a>Rendre un service disponible

Sous *env*, spécifiez un *nom* et une *valeur* pour chaque service que vous souhaitez rendre disponible sur votre ordinateur de développement. Le *nom* est la variable d’environnement qui sera utilisée sur votre ordinateur de développement. La *valeur* est le nom du service à partir de votre cluster et un chemin d’accès. La valeur de la *valeur* prend la forme *$ (services : service_name)/Path*.

Par exemple :

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

L’exemple ci-dessus rend le service *MyApp1* disponible pour votre ordinateur de développement et la variable d’environnement *MYAPP1_SERVICE_HOST* est définie sur l’adresse IP locale du service *MyApp1* avec le `/api/v1` chemin d’accès (autrement dit, `127.1.1.4/api/v1` ). Le service *MyApp1* est accessible à l’aide de la variable d’environnement, *MyApp1*ou *MyApp1. svc. cluster. local*.

> [!NOTE]
> Le fait de rendre un service disponible sur votre ordinateur de développement rend le service complet disponible quel que soit le chemin d’accès que vous définissez. Le chemin d’accès est utilisé uniquement pour définir la variable d’environnement à utiliser sur l’ordinateur de développement.
Vous pouvez également rendre un service à partir d’un espace de noms Kubernetes spécifique disponible à l’aide de *$ (services : service_name. NAMESPACE_NAME)*. Par exemple :

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

L’exemple ci-dessus rend le *myapp2* de l’espace de noms *MyNamespace* disponible sur votre ordinateur de développement et définit la variable d’environnement *MYAPP2_SERVICE_HOST* sur l’adresse IP locale du *myapp2* à partir de l’espace de noms *MyNamespace* .

## <a name="create-an-environment-variable-with-a-constant-value"></a>Créer une variable d’environnement avec une valeur constante

Sous *env*, spécifiez un *nom* et une *valeur* pour chaque variable d’environnement que vous souhaitez créer sur votre ordinateur de développement. Le *nom* est la variable d’environnement qui sera utilisée sur votre ordinateur de développement et la *valeur* est la valeur. Par exemple :

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

L’exemple ci-dessus crée une variable d’environnement nommée *debug_mode* avec la valeur *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Exemple KubernetesLocalProcessConfig. YAML

Voici un exemple de `KubernetesLocalProcessConfig.yaml` fichier complet :

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à utiliser Bridge to Kubernetes pour vous connecter à votre ordinateur de développement local à votre cluster, consultez [utiliser Bridge to Kubernetes avec Visual Studio code][bridge-to-kubernetes-vs-code] et [utiliser Bridge to Kubernetes avec Visual Studio][bridge-to-kubernetes-vs].

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
