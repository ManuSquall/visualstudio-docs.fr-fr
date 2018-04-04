---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 6 - En savoir plus sur le développement en équipe | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
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
