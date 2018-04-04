---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 3 - Créer une application web ASP.NET Core | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: f858a013e4b0c2ce1c30b8f26f2dc33eebf19c27
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Bien démarrer avec Connected Environment et .NET Core

Étape précédente : [Créer un environnement de développement Kubernetes dans Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Créer une application web ASP.NET Core
Si vous avez installé [.NET Core](https://www.microsoft.com/net), vous pouvez rapidement créer une application web ASP.NET Core dans un dossier nommé `webfrontend`.
```cmd
dotnet new mvc --name webfrontend
```

Vous pouvez aussi **télécharger un exemple de code depuis GitHub** en accédant à https://github.com/Azure/vsce et en sélectionnant **Clone or download** pour télécharger le dépôt GitHub dans votre environnement local. Le code correspondant à ce guide se trouve dans `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Mettre à jour un fichier de contenu
Non seulement Connected Environment vous permet d’exécuter du code dans Kubernetes, mais aussi de voir de façon rapide et itérative les effets des changements que vous apportez au code dans un environnement Kubernetes situé dans le cloud.

1. Localisez le fichier `./Views/Home/Index.cshtml` et apportez une modification au code HTML. Par exemple, remplacez la ligne 70 qui contient `<h2>Application uses</h2>` par quelque chose comme : `<h2>Hello k8s in Azure!</h2>`
1. Enregistrez le fichier. Quelques instants plus tard, dans la fenêtre de terminal, un message s’affiche indiquant qu’un fichier situé dans le conteneur en cours d’exécution a été mis à jour.
1. Accédez à votre navigateur et actualisez la page. La page web affiche le code HTML mis à jour.

Que s'est-il passé ? Les modifications apportées aux fichiers de contenu, notamment de format HTML et CSS, ne nécessitent pas de recompilation dans une application web .NET Core. De ce fait, une commande `vsce up` active synchronise automatiquement les fichiers de contenu modifiés dans le conteneur s’exécutant dans Azure, ce qui vous permet de voir rapidement les modifications que vous avez apportées au contenu.

## <a name="update-a-code-file"></a>Mettre à jour un fichier de code
Une mise à jour de fichiers de code demande un peu plus de travail dans la mesure où une application .NET Core a besoin d’être regénérée et de produire les fichiers binaires applicatifs mis à jour.

1. Dans la fenêtre de terminal, appuyez sur `Ctrl+C` (pour arrêter `vsce up`).
1. Ouvrez le fichier de code nommé `Controllers/HomeController.cs` et modifiez le message qui s’affiche dans la page À propos : `ViewData["Message"] = "Your application description page.";`
1. Enregistrez le fichier.
1. Exécutez `vsce up` dans la fenêtre de terminal. 

L’image de conteneur est alors regénérée et le graphique Helm redéployé. Pour voir vos changements de code prendre effet dans l’application en cours d’exécution, accédez au menu À propos de l’application web.


Mais il existe une *méthode encore plus rapide* pour développer du code, que nous explorerons dans la section suivante. 
> [!div class="nextstepaction"]
> [Déboguer un conteneur dans Kubernetes](get-started-netcore-04.md)

