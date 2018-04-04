---
title: Créer un environnement de développement Node.js constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 4 - Déboguer un conteneur dans Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 8dca016f3a3feb2d1fb10a80695b82e531e48a74
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Bien démarrer avec Connected Environment et Node.js

Étape précédente : [Créer un conteneur Node.js dans Kubernetes](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Sélectionner la configuration de débogage VSCE
1. Pour ouvrir la vue de débogage, cliquez sur l’icône Déboguer dans la **barre d’activités** latérale de VS Code.
1. Sélectionnez **Launch Program (VSCE)** (Lancer le programme (VSCE)) comme configuration de débogage active.

![](media/debug-configuration-nodejs.png)

> [!Note]
> Si aucune commande Connected Environment ne figure dans la palette de commandes, vérifiez que vous avez bien [installé l’extension VS Code pour Connected Environment](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code).

## <a name="debug-the-container-in-kubernetes"></a>Déboguer le conteneur dans Kubernetes
Appuyez sur **F5** pour déboguer votre code dans Kubernetes.

Comme pour la commande `up`, le code est synchronisé dans l’environnement de développement au moment où vous lancez le débogage et un conteneur est généré et déployé dans Kubernetes. Cette fois, bien entendu, le débogueur est attaché au conteneur distant.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Définissez un point d’arrêt dans un fichier de code côté serveur, par exemple au sein de `app.get('/api'...` dans `server.js`. Actualisez la page du navigateur ou appuyez sur le bouton « Say It Again » (Répéter). Vous devez alors atteindre le point d’arrêt et être en mesure de parcourir le code pas à pas.

Vous disposez d’un accès complet aux informations de débogage (pile des appels, variables locales, informations sur les exceptions, etc.) comme si le code s’exécutait localement.

## <a name="edit-code-and-refresh-the-debug-session"></a>Modifier le code et actualiser la session de débogage
Apportez une modification au code en veillant à ce que le débogueur soit actif. Par exemple, modifiez à nouveau le message d’accueil :

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

Enregistrez le fichier puis, dans le **volet d’actions de débogage**, cliquez sur le bouton **Actualiser**. 

![](media/debug-action-refresh-nodejs.png)

Au lieu de regénérer et de redéployer une nouvelle image de conteneur à chaque modification du code, ce qui prend souvent beaucoup de temps, Connected Environment redémarre le processus Node.js entre les sessions de débogage pour accélérer la boucle édition/débogage.

Actualisez l’application web dans le navigateur ou appuyez sur le bouton *Say It Again* (Répéter). Votre message personnalisé s’affiche dans l’interface utilisateur.


## <a name="use-nodemon-to-develop-even-faster"></a>Utiliser NodeMon pour développer encore plus vite
*Nodemon* est un outil très prisé dont se servent les développeurs Node.js pour développer rapidement. Au lieu de redémarrer manuellement le processus Node à chaque modification de code côté serveur, il est fréquent que les développeurs configurent leur projet Node de sorte que *nodemon* surveille les modifications de fichiers et redémarre automatiquement le processus serveur. Avec cette méthodologie, le développeur actualise simplement son navigateur après avoir modifié le code.

L’objectif de Connected Environment est de vous permettre d’utiliser les mêmes flux de travail de développement productifs que ceux que vous employez quand vous développez localement. Pour illustrer cela, l’exemple de projet `webfrontend` a été configuré pour utiliser *nodemon* (il est configuré comme dépendance de développement dans `package.json`).

Essayez la procédure suivante :
1. Arrêtez le débogueur VS Code.
1. Cliquez sur l’icône Déboguer dans la **barre d’activités** latérale de VS Code. 
1. Sélectionnez **Attach (VSCE)** comme configuration de débogage active.
1. Appuyez sur F5.

Dans cette configuration, le conteneur est configuré pour démarrer *nodemon*. Dès lors que des modifications sont apportées au code serveur, *nodemon* redémarre automatiquement le processus Node, exactement de la même façon que lorsque vous développez en local. 
1. Modifiez à nouveau le message d’accueil dans `server.js`, puis enregistrez le fichier.
1. Actualisez le navigateur ou cliquez sur le bouton *Say It Again* (Répéter) pour voir vos modifications prendre effet.

**Vous connaissez maintenant une méthode permettant d’itérer rapidement au sein du code et de déboguer directement dans Kubernetes.** Par la suite, nous verrons comment créer et appeler un deuxième conteneur.

> [!div class="nextstepaction"]
> [Appeler un service s’exécutant dans un conteneur distinct](get-started-nodejs-05.md)

