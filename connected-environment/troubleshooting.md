---
title: Résolution des problèmes | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: troubleshooting
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: b41d228bcced6149c95b09b2445dd656ed9772d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-guide"></a>Guide de dépannage

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Erreur « upstream connect error or disconnect/reset before headers »
Cette erreur peut s’afficher au moment où vous tentez d’accéder à votre service. Par exemple, quand vous accédez à l’URL du service dans un navigateur. 

**Raison :** Le port du conteneur n’est pas disponible. Voici les raisons les plus courantes : 
* Le conteneur est toujours en cours de génération et de déploiement. Cela peut être le cas si vous exécutez `vsce up` ou démarrez le débogueur et que vous tentez d’accéder au conteneur avant que celui-ci ait été déployé avec succès.
* La configuration des ports n’est pas cohérente entre le fichier Dockerfile, le graphique Helm et l’éventuel code serveur qui ouvre un port.

**Solution(s) possible(s) :**
1. Si le conteneur est en cours de génération/déploiement, attendez 2 à 3 secondes et essayer d’accéder à nouveau au service. 
1. Vérifiez la configuration des ports. Les numéros des ports spécifiés doivent être **identiques** dans toutes les ressources suivantes :
    * **Fichier Dockerfile :** spécifié par l’instruction `EXPOSE`.
    * **[Graphique Helm](https://docs.helm.sh) :** spécifié par les valeurs `externalPort` et `internalPort` pour un service (souvent situées dans un fichier `values.yml`),
    * Les ports ouvert dans le code d’application, par exemple dans Node.js : `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>Fichier de configuration introuvable
Vous exécutez `vsce up` et obtenez l’erreur suivante : `Config file not found: .../vsce.yaml`

**Raison :** `vsce up` doit s’exécuter à partir du répertoire racine du code que vous voulez exécuter, et le dossier du code doit avoir été initialisé pour s’exécuter avec Connected Environment.

**Solution(s) possible(s) :**
1. Remplacez votre répertoire actif par le dossier racine contenant le code de votre service. 
1. Si le dossier de code ne contient pas de fichier vsce.yaml, exécutez `vsce init` pour générer des ressources Docker, Kubernetes et VSCE.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Erreur : « The pipe program 'vsce' exited unexpectedly with code 126. »
Le démarrage du débogueur VS Code peut parfois provoquer cette erreur. Il s’agit d’un bogue.

**Solution(s) possible(s) :**
1. Fermez et rouvrez VS Code.
2. Appuyez à nouveau sur F5.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Erreur de débogage « Configured debug type 'coreclr' is not supported »
Au moment de son exécution, le débogueur VS Code signale l’erreur suivante : `Configured debug type 'coreclr' is not supported.`

**Raison :** L’extension VS Code pour Connected Environment n’est pas installée sur votre ordinateur de développement.

**Solution(s) possible(s) :** Installez l’[extension VS Code pour Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Le portail Azure n’affiche pas d’instances Connected Environment

**Raison :** Aucune expérience de portail Azure pour Connected Environment n’est encore disponible en préversion.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>Le type ou le nom d’espace de noms « MyLibrary » est introuvable

**Raison :** Par défaut, le contexte de build se trouve au niveau du projet/service. Si vous utilisez un projet de bibliothèque, celui-ci est introuvable.

**Solution(s) possible(s) :** Procédez comme suit :
1. Modifiez le fichier vsce.yaml de façon à définir le contexte de build au niveau de la solution.
2. Modifiez les fichiers Dockerfile et Dockerfile.develop de sorte qu’ils fassent référence aux fichiers csproj par rapport au nouveau contexte de build.
3. Placez un fichier .dockerignore à côté du fichier .sln et modifiez-le si nécessaire.

Vous trouverez un exemple dans https://github.com/sgreenmsft/buildcontextsample

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Erreur d’autorisation « Microsoft.ConnectedEnvironment/register/action » au moment de créer un environnement
L’erreur suivante peut s’afficher quand vous gérez un environnement et que vous travaillez dans un abonnement Azure pour lequel vous ne disposez pas d’un accès Propriétaire ou Contributeur.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Raison :** L’espace de noms Microsoft.ConnectedEnvironment n’est pas inscrit dans l’abonnement Azure sélectionné.

**Solution(s) possible(s) :** Une personne disposant d’un accès Propriétaire ou Contributeur à l’abonnement Azure peut exécuter la commande Azure CLI ci-dessous pour inscrire manuellement l’espace de noms Microsoft.ConnectedEnvironment :

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE ne semble pas utiliser mon fichier Dockerfile existant pour générer un conteneur 

**Raison :** VSCE peut être configuré pour pointer vers un fichier Dockerfile spécifique de votre projet. S’il s’avère que VSCE n’utilise pas le fichier Dockerfile prévu pour générer vos conteneurs, vous devrez peut-être indiquer explicitement son emplacement à VSCE. 

**Solution(s) possible(s) :** Ouvrez le fichier `vsce.yaml` qui a été généré par VSCE dans votre projet. Utilisez la directive `configurations->develop->build->dockerfile` pour pointer vers le fichier Dockerfile que vous voulez utiliser :

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```