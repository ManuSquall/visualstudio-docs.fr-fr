---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 5 - Appeler un autre conteneur | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: ab3934e6f7f013dd21309dc8c98461983bdfe30a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898425"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Bien démarrer avec Connected Environment et .NET Core et Visual Studio

Étape précédente : [Déboguer un conteneur dans Kubernetes](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Appeler un autre conteneur
Dans cette section, nous allons créer un deuxième service, `mywebapi`, et le nommer `webfrontend`. Chaque service s’exécutera dans des conteneurs distincts. Nous procèderons ensuite à un débogage dans les deux conteneurs.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Télécharger l’exemple de code pour *mywebapi*
Pour gagner du temps, téléchargeons un exemple de code à partir d’un dépôt GitHub. Accédez à https://github.com/Azure/vsce et sélectionnez **Clone or download** pour télécharger le dépôt GitHub. Le code correspondant à cette section se trouve dans `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Exécuter *mywebapi*
1. Ouvrez le projet `mywebapi` dans une *fenêtre Visual Studio distincte*.
1. Sélectionnez **Connected Environment for AKS** dans la liste déroulante des paramètres de lancement comme vous l’avez fait précédemment pour le projet `webfrontend`. Cette fois, au lieu de créer un nouvel environnement de développement, sélectionnez celui que vous avez déjà créé. Comme précédemment, conservez la valeur par défaut de Space (Espace) (`mainline`) et cliquez sur **OK**. Dans la fenêtre de sortie, vous remarquez peut-être que Visual Studio démarre pour « préparer » ce nouveau service dans votre environnement de développement de façon à accélérer le processus au moment où vous démarrez le débogage.
1. Appuyez sur F5 et attendez que le service soit généré et déployé. Vous saurez qu’il est prêt dès que la barre d’état Visual Studio pendra la couleur orange.
1. Notez l’URL du point de terminaison qui figure dans le volet **Connected Environment for AKS** de la fenêtre **Sortie**. Elle se présente sous la forme suivante : http://localhost:\<numéro_port\>. Vous pouvez penser que le conteneur s’exécute localement, mais en réalité, il s’exécute dans notre environnement de développement dans Azure.
1. Dès que `mywebapi` est prêt, ouvrez votre navigateur à l’adresse localhost et ajoutez `/api/values` à l’URL pour appeler l’API GET par défaut pour `ValuesController`. 
1. Si toutes les étapes ont abouti, le service `mywebapi` affiche une réponse sous la forme suivante.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Formuler une demande de *webfrontend* à *mywebapi*
Écrivons maintenant du code dans `webfrontend` qui adresse une demande à `mywebapi`. Basculez vers la fenêtre Visual Studio contenant le projet `webfrontend`. Dans le fichier `HomeController.cs`, *remplacez* le code de la méthode About par ceci :

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

Observez la façon dont la fonctionnalité de détection du service DNS de Kubernetes est employée pour faire référence au service avec `http://mywebapi`. **Le code s’exécute dans notre environnement de développement de la même façon qu’il s’exécutera en production**.

L’exemple de code ci-dessus utilise aussi une classe `HeaderPropagatingHttpClient`. Cette classe d’assistance est le fichier `HeaderPropagation.cs` qui a été ajouté à votre projet au moment où vous l’avez configuré pour utiliser Connected Environment. La classe `HeaderPropagatingHttpClient`, qui est dérivée de la classe bien connue `HttpClient`, ajoute une fonctionnalité qui permet de propager des en-têtes spécifiques d’un objet HttpRequest ASP .NET existant vers un objet HttpRequestMessage sortant. Nous verrons par la suite en quoi cela permet d’améliorer la productivité dans les scénarios d’équipe.

## <a name="debug-across-multiple-services"></a>Déboguer dans plusieurs services
1. À ce stade, `mywebapi` doit toujours s’exécuter avec le débogueur attaché. Si ce n’est pas le cas, appuyez sur F5 dans le projet `mywebapi`.
1. Définissez un point d’arrêt dans la méthode `Get(int id)` du fichier `ValuesController.cs` qui gère les demandes GET `api/values/{id}`.
1. Dans le projet `webfrontend` où vous avez collé le code ci-dessus, définissez un point d’arrêt juste avant qu’il envoie une demande GET à `mywebapi/api/values`.
1. Appuyez sur F5 dans le projet `webfrontend`. Visual Studio ouvre à nouveau un navigateur sur le port localhost approprié et l’application web s’affiche.
1. Cliquez sur le lien « **About** » en haut de la page pour déclencher le point d’arrêt dans le projet `webfrontend`. 
1. Appuyez sur F10 pour continuer. Dès lors, le point d’arrêt du projet `mywebapi` est déclenché.
1. Appuyez sur F5 pour continuer et revenir au code du projet `webfrontend`.
1. Si vous appuyez à nouveau sur F5, la demande aboutit et retourne une page dans le navigateur. Dans l’application web, la page À propos affiche un message concaténé par les deux services : « Hello from webfrontend and Hello from mywebapi ».

Félicitations ! Vous disposez maintenant d’une application à plusieurs conteneurs qui peuvent être développés et déployés séparément.

> [!div class="nextstepaction"]
> [En savoir plus sur le développement en équipe](get-started-netcore-visualstudio-06.md)

