---
title: Créer un environnement de développement Node.js constitué de conteneurs en utilisant Kubernetes dans le cloud - Étape 5 - Appeler un autre conteneur | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: 5b7065714475ee700fb1a04502a50a4fce0b0e8d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Bien démarrer avec Connected Environment et Node.js

Étape précédente : [Déboguer un conteneur dans Kubernetes](get-started-nodejs-04.md)

Dans cette section, nous allons créer un deuxième service, `mywebapi`, et le nommer `webfrontend`. Chaque service s’exécutera dans des conteneurs distincts. Nous procèderons ensuite à un débogage dans les deux conteneurs.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Ouvrir l’exemple de code pour *mywebapi*
Vous devez déjà disposer de l’exemple de code `mywebapi` pour ce guide sous un dossier nommé `vsce/samples` (dans le cas contraire, accédez à https://github.com/Azure/vsce et sélectionnez **Clone or download** pour télécharger le dépôt GitHub.) Le code correspondant à cette section se trouve dans `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Exécuter *mywebapi*
1. Ouvrez le dossier `mywebapi` dans une *fenêtre VS Code distincte*.
1. Appuyez sur F5 et attendez que le service soit généré et déployé. Il est prêt dès que la barre de débogage VS Code s’affiche.
1. Notez l’URL du point de terminaison, qui se présente comme suit : http://localhost :\<numéro_port\>. **Conseil : La barre d’état VS Code affiche une URL interactive.** Vous pouvez penser que le conteneur s’exécute localement, mais en réalité, il s’exécute dans notre environnement de développement dans Azure. La présence de l’adresse localhost s’explique par le fait qu’aucun point de terminaison public n’est défini dans `mywebapi` et qu’elle accessible uniquement à partir de l’instance Kubernetes. Pour des raisons pratiques et pour faciliter l’interaction avec le service privé à partir de votre ordinateur local, Connected Environment crée un tunnel SSH temporaire vers le conteneur s’exécutant dans Azure.
1. Dès que `mywebapi` est prêt, ouvrez votre navigateur en indiquant l’adresse localhost. Une réponse du service `mywebapi` (« Hello from mywebapi ») doit s’afficher.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Formuler une demande de *webfrontend* à *mywebapi*
Écrivons maintenant du code dans `webfrontend` qui adresse une demande à `mywebapi`.
1. Basculez vers la fenêtre VS Code pour `webfrontend`.
1. Ajoutez ces lignes de code au-dessus de `server.js` :
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Remplacez* le code pour le gestionnaire GET `/api`. Au moment de traiter une demande, il adresse à son tour un appel à `mywebapi`, puis retourne les résultats des deux services.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Observez la façon dont la fonctionnalité de détection du service DNS de Kubernetes est employée pour faire référence au service avec `http://mywebapi`. **Le code s’exécute dans notre environnement de développement de la même façon qu’il s’exécutera en production**.

L’exemple de code ci-dessus utilise un module d’assistance nommé `propagateHeaders`. Celui-ci a été ajouté au dossier de votre code au moment où vous avez exécuté `vsce init`. La fonction `propagateHeaders.from()` propage des en-têtes spécifiques d’un objet http.IncomingMessage existant vers un objet d’en-têtes pour une demande sortante. Nous verrons par la suite en quoi ceci permet d’améliorer la productivité dans les scénarios d’équipe.


## <a name="debug-across-multiple-services"></a>Déboguer dans plusieurs services
1. À ce stade, `mywebapi` doit toujours s’exécuter avec le débogueur attaché. Si ce n’est pas le cas, appuyez sur F5 dans le projet `mywebapi`.
1. Définissez un point d’arrêt dans le gestionnaire `/` GET par défaut.
1. Dans le projet `webfrontend`, définissez un point d’arrêt juste avant qu’il envoie une demande GET à `http://mywebapi`.
1. Appuyez sur F5 dans le projet `webfrontend`.
1. Ouvrez l’application web et parcourez le code pas à pas dans les deux services. L’application web doit afficher un message concaténé par les deux services : « Hello from webfrontend and Hello from mywebapi ».


Félicitations ! Vous disposez maintenant d’une application à plusieurs conteneurs qui peuvent être développés et déployés séparément.

> [!div class="nextstepaction"]
> [En savoir plus sur le développement en équipe](get-started-nodejs-06.md)
