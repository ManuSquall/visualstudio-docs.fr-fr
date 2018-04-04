---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 4 - Déboguer un conteneur dans Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: f06489194f70a3e7e617f4022917cd1d4a96337f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Bien démarrer avec Connected Environment et .NET Core
 
Étape précédente : [Créer une application web ASP.NET Core](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Sélectionner la configuration de débogage VSCE
1. Pour ouvrir la vue de débogage, cliquez sur l’icône Déboguer dans la **barre d’activités** latérale de VS Code.
1. Sélectionnez **.NET Core Launch (VSCE)** comme configuration de débogage active.

![](media/debug-configuration.png)

> [!Note]
> Si aucune commande Connected Environment ne figure dans la palette de commandes, vérifiez que vous avez bien [installé l’extension VS Code pour Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="debug-the-container-in-kubernetes"></a>Déboguer le conteneur dans Kubernetes
Appuyez sur **F5** pour déboguer votre code dans Kubernetes.

Comme pour la commande `up`, le code est synchronisé dans l’environnement de développement et un conteneur est généré et déployé dans Kubernetes. Cette fois, bien entendu, le débogueur est attaché au conteneur distant.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Définissez un point d’arrêt dans un fichier de code côté serveur, par exemple dans la fonction `Index()` du fichier source `Controllers/HomeController.cs`. Le fait d’actualiser la page de navigateur permet d’atteindre le point d’arrêt.

Vous disposez d’un accès complet aux informations de débogage (pile des appels, variables locales, informations sur les exceptions, etc.) comme si le code s’exécutait localement.

## <a name="edit-code-and-refresh"></a>Modifier le code et actualiser
Apportez une modification au code en veillant à ce que le débogueur soit actif. Par exemple, modifiez le message de la page À propos dans `Controllers/HomeController.cs`. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Enregistrez le fichier puis, dans le **volet d’actions de débogage**, cliquez sur le bouton **Actualiser**. 

![](media/debug-action-refresh.png)

Au lieu de regénérer et de redéployer une nouvelle image de conteneur à chaque modification du code, ce qui prend souvent beaucoup de temps, Connected Environment recompile de façon incrémentielle le code dans le conteneur existant pour accélérer la boucle édition/débogage.

Actualisez l’application web dans le navigateur et accédez à la page À propos. Votre message personnalisé s’affiche dans l’interface utilisateur.

**Vous connaissez maintenant une méthode permettant d’itérer rapidement au sein du code et de déboguer directement dans Kubernetes.** Par la suite, nous verrons comment créer et appeler un deuxième conteneur.

> [!div class="nextstepaction"]
> [Appeler un service s’exécutant dans un conteneur distinct](get-started-netcore-05.md)
