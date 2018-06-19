---
title: Créer un environnement de développement Node.js constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 6 - Découvrir le développement en équipe | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883577"
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

