---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 5 - Appeler un autre conteneur | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 6ef3a79d0b79feae64adcaebe31daa48ba75ab75
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Bien démarrer avec Connected Environment et .NET Core

Étape précédente : [Déboguer un conteneur dans Kubernetes](get-started-netcore-04.md)

Dans cette section, nous allons créer un deuxième service, `mywebapi`, et le nommer `webfrontend`. Chaque service s’exécutera dans des conteneurs distincts. Nous procèderons ensuite à un débogage dans les deux conteneurs.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Télécharger l’exemple de code pour *mywebapi*
Pour gagner du temps, téléchargeons un exemple de code à partir d’un dépôt GitHub. Accédez à https://github.com/Azure/vsce et sélectionnez **Clone or download** pour télécharger le dépôt GitHub. Le code correspondant à cette section se trouve dans `vsce/samples/dotnetcore/getting-started/mywebapi`.


## <a name="run-mywebapi"></a>Exécuter *mywebapi*
1. Ouvrez le dossier `mywebapi` dans une *fenêtre VS Code distincte*.
1. Appuyez sur F5 et attendez que le service soit généré et déployé. Il est prêt dès que la barre de débogage VS Code s’affiche.
1. Notez l’URL du point de terminaison, qui se présente comme suit : http://localhost:\<numéro_port\>. **Conseil : La barre d’état VS Code affiche une URL interactive.** Vous pouvez penser que le conteneur s’exécute localement, mais en réalité, il s’exécute dans notre environnement de développement dans Azure. La présence de l’adresse localhost s’explique par le fait qu’aucun point de terminaison public n’est défini dans `mywebapi` et qu’elle accessible uniquement à partir de l’instance Kubernetes. Pour des raisons pratiques et pour faciliter l’interaction avec le service privé à partir de votre ordinateur local, Connected Environment crée un tunnel SSH temporaire vers le conteneur s’exécutant dans Azure.
1. Dès que `mywebapi` est prêt, ouvrez votre navigateur en indiquant l’adresse localhost. Ajoutez `/api/values` à l’URL pour appeler l’API GET par défaut pour `ValuesController`. 
1. Si toutes les étapes ont abouti, une réponse du service `mywebapi` s’affiche.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Formuler une demande de *webfrontend* vers *mywebapi*
Écrivons maintenant du code dans `webfrontend` qui adresse une demande à `mywebapi`.
1. Basculez vers la fenêtre VS Code pour `webfrontend`.
1. *Remplacez* le code pour la méthode About :

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

L’exemple de code ci-dessus utilise aussi une classe `HeaderPropagatingHttpClient`. Cette classe d’assistance a été ajoutée au dossier de votre code au moment où vous avez exécuté `vsce init`. La classe `HeaderPropagatingHttpClient`, qui est dérivée de la classe bien connue `HttpClient`, ajoute une fonctionnalité qui permet de propager des en-têtes spécifiques d’un objet HttpRequest ASP .NET existant vers un objet HttpRequestMessage sortant. Nous verrons par la suite en quoi cela permet d’améliorer la productivité dans les scénarios d’équipe.


## <a name="debug-across-multiple-services"></a>Déboguer dans plusieurs services
1. À ce stade, `mywebapi` doit toujours s’exécuter avec le débogueur attaché. Si ce n’est pas le cas, appuyez sur F5 dans le projet `mywebapi`.
1. Définissez un point d’arrêt dans la méthode `Get(int id)` qui gère les demandes GET `api/values/{id}`.
1. Dans le projet `webfrontend`, définissez un point d’arrêt juste avant qu’il envoie une demande GET à `mywebapi/api/values`.
1. Appuyez sur F5 dans le projet `webfrontend`.
1. Appelez l’application web et parcourez le code pas à pas dans les deux services.
1. Dans l’application web, la page À propos affiche un message concaténé par les deux services : « Hello from webfrontend and Hello from mywebapi ».


Félicitations ! Vous disposez maintenant d’une application à plusieurs conteneurs qui peuvent être développés et déployés séparément.

> [!div class="nextstepaction"]
> [En savoir plus sur le développement en équipe](get-started-netcore-06.md)

