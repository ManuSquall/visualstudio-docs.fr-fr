---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 6 - En savoir plus sur le développement en équipe | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Bien démarrer avec Connected Environment et .NET Core

Étape précédente : [Appeler un autre conteneur](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Voyons cela en action :
1. Accédez à la fenêtre VS Code pour `mywebapi` et modifiez le code de la méthode `string Get(int id)`, par exemple :

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Next](get-started-netcore-07.md)
