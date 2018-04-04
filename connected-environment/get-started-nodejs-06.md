---
title: Créer un environnement de développement Node.js constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 6 - Découvrir le développement en équipe | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Bien démarrer avec Connected Environment et Node.js

Étape précédente : [Appeler un service s’exécutant dans un conteneur distinct](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Voyons cela en action :
1. Accédez à la fenêtre VS Code pour `mywebapi` et modifiez le code du gestionnaire `/` par défaut, par exemple :

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Next](get-started-nodejs-07.md)

