---
title: Créer un environnement de développement Node.js constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 3 - Créer une application web ASP.NET | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 34e1f07e173ccba6aab561fb4795abbe938e0127
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31890152"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Bien démarrer avec Connected Environment et Node.js

Étape précédente : [Créer un environnement de développement Kubernetes dans Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Créer une application web Node.js
Téléchargez le code depuis GitHub en accédant à https://github.com/Azure/vsce et en sélectionnant **Clone or download** pour télécharger le dépôt GitHub dans votre environnement local. Le code correspondant à ce guide se trouve dans `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Mettre à jour un fichier de contenu
Non seulement Connected Environment vous permet d’exécuter du code dans Kubernetes, mais aussi de voir de façon rapide et itérative les effets des changements que vous apportez au code dans un environnement Kubernetes situé dans le cloud.

1. Localisez le fichier `./public/index.html` et apportez une modification au code HTML. Par exemple, modifiez la couleur d’arrière-plan de la page en choisissant un ton bleu :

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Enregistrez le fichier. Quelques instants plus tard, dans la fenêtre de terminal, un message s’affiche indiquant qu’un fichier situé dans le conteneur en cours d’exécution a été mis à jour.
1. Accédez à votre navigateur et actualisez la page. Vous pouvez constater que la couleur a été mise à jour.

Que s'est-il passé ? Les modifications apportées aux fichiers de contenu, notamment de format HTML et CSS, ne nécessitent pas le redémarrage du processus Node.js. De ce fait, une commande `vsce up` active synchronise automatiquement les fichiers de contenu modifiés directement dans le conteneur en cours d’exécution dans Azure, ce qui vous permet de voir rapidement vos modifications de contenu.

### <a name="test-from-a-mobile-device"></a>Tester à partir d’un appareil mobile
Si vous ouvrez l’application web sur un appareil mobile, vous constaterez que l’interface utilisateur ne s’affiche pas correctement sur un appareil de petite taille.

Pour résoudre ce problème, nous allons ajouter une balise META `viewport` :
1. Ouvrez le fichier `./public/index.html`.
1. Ajoutez une balise META `viewport` dans l’élément `head` existant :

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Enregistrez le fichier.
1. Actualisez le navigateur de votre appareil. À présent, l’application web s’affiche correctement. 

Cet exemple montre bien que certains problèmes ne peuvent pas être identifiés tant que vous ne testez pas l’application sur un appareil qui est susceptible d’être utilisé. Avec VS Connected Environment, vous pouvez rapidement itérer au sein de votre code et valider les modifications sur les appareils cibles.

## <a name="update-a-code-file"></a>Mettre à jour un fichier de code
Une mise à jour de fichiers de code côté serveur demande un peu plus de travail, car une application Node.js doit redémarrer.

1. Dans la fenêtre de terminal, appuyez sur `Ctrl+C` (pour arrêter `vsce up`).
1. Ouvrez le fichier de code nommé `server.js` et modifiez le message d’accueil du service : 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Enregistrez le fichier.
1. Exécutez `vsce up` dans la fenêtre de terminal. 

L’image de conteneur est alors regénérée et le graphique Helm redéployé. Rechargez la page du navigateur pour voir vos modifications de code prendre effet.


Mais il existe une *méthode encore plus rapide* pour développer du code, que nous explorerons dans la section suivante. 
> [!div class="nextstepaction"]
> [Déboguer un conteneur dans Kubernetes](get-started-nodejs-04.md)
