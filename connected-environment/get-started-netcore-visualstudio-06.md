---
title: Créer un environnement de développement .NET Core constitué de conteneurs en utilisant Kubernetes dans le cloud avec Visual Studio - Étape 6 - Découvrir le développement en équipe | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Développement rapide Kubernetes à l’aide de conteneurs et de microservices sur Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: ghogen
ms.openlocfilehash: fb05df7782c23c6caa973e0c1ad3e9433e8b2470
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Bien démarrer avec Connected Environment et .NET Core et Visual Studio

Étape précédente : [Appeler un autre conteneur](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>En savoir plus sur le développement en équipe

Jusqu’à présent, nous avons exécuté le code de notre application comme si nous étions le seul développeur à travailler sur l’application. Dans cette section, nous allons découvrir en quoi Connected Environment simplifie le développement en équipe :
* Permettre à une équipe de développeurs de travailler dans le même environnement de développement.
* Permettre à chaque développeur d’itérer au sein de son code de manière isolée sans craindre de perturber les autres.
* Tester du code de bout en bout, préalablement à sa validation, sans avoir à créer des objets fictifs ou à simuler des dépendances.

## <a name="challenges-with-developing-microservices"></a>Difficultés liées au développement de microservices
Notre exemple d’application n’est pas très complexe pour le moment. Mais dans le cadre d’un développement réel, les difficultés ne tardent pas se manifester à mesure que des services sont ajoutés et que l’équipe de développement s’étoffe.

Imaginez-vous travaillant sur un service qui interagit avec des dizaines d’autres services.

1. Au bout d’un certain temps, il peut devenir irréaliste de tout exécuter en local à des fins de développement. En effet, il n’est pas certain que votre ordinateur de développement ait suffisamment de ressources pour exécuter l’application entière. Ou bien, votre application dispose peut-être de points de terminaison qui doivent être accessible publiquement (par exemple, votre application répond à un webhook à partir d’une application SaaS).
1. Vous pouvez essayer d’exécuter uniquement les services dont vous dépendez, mais cela signifie que vous devez avoir connaissance de la clôture complète des dépendances (par exemple, des dépendances de dépendances). Ou bien, peut-être ne savez-vous pas bien comment générer et exécuter vos dépendances, car vous n’y avez pas travaillé dessus.
1. Certains développeurs se résolvent à simuler ou à feindre la plupart des dépendances de leurs services. Cela peut parfois être utile, mais la gestion de ces objets fictifs peut vite devenir une tâche de développement à part entière. De plus, votre environnement de développement peut devenir très différent de l’environnement de production, et de légers bogues peuvent s’insinuer.
1. Il s’ensuit qu’il devient difficile d’effectuer le moindre test de bout en bout. Un test d’intégration peut raisonnablement être réalisé après la validation, ce qui signifie que les problèmes sont identifiés à un stade plus avancé dans le cycle de développement.

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>Travailler dans un environnement de développement partagé
Avec Connected Environment, vous pouvez configurer un environnement de développement *partagé* dans Azure. Chaque développeur peut se concentrer simplement sur sa partie de l’application et développer de manière itérative du *code de pré-validation* dans un environnement qui contient déjà tous les autres services et ressources cloud dont dépendent leur scénarios. Les dépendances sont toujours à jour et les développeurs travaillent comme en production.

## <a name="work-in-your-own-space"></a>Travailler dans votre propre espace
Entre le moment où vous développez le code de votre service et le moment où vous êtes en mesure de l’archiver, le code est souvent dans un état incorrect. Vous continuez de le façonner, de le tester et de l’expérimenter de manière itérative avec des solutions. Le concept d’**espace** propre à Connected Environment vous permet de travailler de manière isolée sans craindre de perturber les membres de votre équipe.

Pour faire en sorte que les services `webfrontend` et `mywebapi` s’exécutent tous deux dans notre environnement de développement **et dans l’espace `mainline`**, procédez comme suit.
1. Fermez les sessions F5 et/ou de débogage éventuelles pour les deux services, mais laissez les projets ouverts dans leurs fenêtres Visual Studio.
2. Basculez vers la fenêtre Visual Studio contenant le projet `mywebapi` et appuyez sur Ctrl+F5 pour exécuter le service sans le débogueur attaché.
3. Basculez vers la fenêtre Visual Studio contenant le projet `webfrontend` et appuyez sur Ctrl+ F5pour l’exécuter également.

> [!Note]
Il est parfois nécessaire d’actualiser le navigateur de suite après l’affichage initial de la page web consécutif à un Ctrl+F5.

Quiconque ouvrant l’URL publique et accédant à l’application web appellera le chemin de code que nous avons écrit et qui parcourt les deux services en utilisant l’espace `mainline` par défaut. Maintenant supposons que nous voulons poursuivre le développement de `mywebapi` : comment faire sans interrompre les autres développeurs qui utilisent l’environnement de développement ? Pour cela, nous allons configurer notre propre espace.

### <a name="create-a-new-space"></a>Créer un nouvel espace
Dans Visual Studio, vous pouvez créer des espaces supplémentaires qui seront utilisés quand vous appuierez sur F5 ou Ctrl+F5 pour votre service. Vous avez toute latitude quant à la désignation d’un espace et au sens que vous voulez lui donner (p.ex.,  `sprint4` ou `demo`).

Pour créer un espace, procédez comme suit :
1. Basculez vers la fenêtre Visual Studio contenant le projet `mywebapi`.
2. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.
3. Sélectionnez l’onglet **Déboguer** à gauche pour afficher les paramètres Connected Environment.
4. De là, vous pouvez modifier ou créer l’environnement connecté et/ou l’espace qui seront utilisés quand vous appuierez sur F5 ou Ctrl+F5. *Veillez à ce que l’environnement connecté que vous avez créé précédemment est sélectionné*.
5. Dans la liste déroulante **Space** (Espace), sélectionnez **<Create New Space...>** (Créer un espace).

    ![](images/Settings.png)

6. Dans la boîte de dialogue **Add Space** (Ajouter un espace), tapez le nom de l’espace et cliquez sur **OK**. J’ai attribué mon nom (« scott ») au nouvel espace pour que mes homologues sachent qu’il s’agit de l’espace dans lequel je travaille.

    ![](images/AddSpace.png)

7. Votre environnement de développement est maintenant visible et le nouvel espace est sélectionné dans la page de propriétés du projet.

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>Mettre à jour le code de *mywebapi*

1. Dans le projet `mywebapi`, apportez une modification au code de la méthode `string Get(int id)` dans le fichier `ValuesController.cs` comme suit :
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. Définissez un point d’arrêt dans ce bloc de code mis à jour (vous en avez peut-être déjà défini un précédemment).
3. Appuyez sur F5 pour démarrer le service `mywebapi`. Le service démarre dans votre environnement de développement en utilisant l’espace sélectionné, en l’occurrence `scott`.

Voici un diagramme qui vous aidera à comprendre le fonctionnement des différents espaces. Le chemin de couleur bleue représente une demande via l’espace `mainline`, qui est le chemin utilisé par défaut si aucun espace n’est indiqué devant l’URL. Le chemin de couleur verte représente une demande via l’espace `scott`.

![](media/Space-Routing.png)

Cette fonctionnalité intégrée de Connected Environment vous permet de tester le code de bout en bout dans un environnement partagé sans contraindre chaque développeur à recréer la pile complète de services dans son espace. Notez que ce routage nécessite le transfert d’en-têtes de propagation dans le code de votre application, comme nous l’avons vu dans l’étape précédente de ce guide.

## <a name="test-code-running-in-the-scott-space"></a>Tester le code s’exécutant dans l’espace `scott`
Pour tester la nouvelle version de `mywebapi` avec `webfrontend`, ouvrez votre navigateur en indiquant l’URL du point d’accès public de `webfrontend` (p.ex.,  https://webfrontend-teamenv.vsce.io) et accédez à la page À propos. Vous devez y trouver le message d’origine « Hello from webfrontend and Hello from mywebapi ».

Maintenant, ajoutez la partie « scott- » à l’URL sous la forme https://scott-webfrontend-teamenv.vsce.io, puis actualisez le navigateur. Le point d’arrêt que vous définissez dans votre projet `mywebapi` doit être atteint. Appuyer sur F5 pour continuer ; le message « Hello webfrontend and mywebapi now says something new » doit maintenant être affiché dans votre navigateur. Cela est dû au fait que le chemin de votre code mis à jour dans `mywebapi` s’exécute dans l’espace `scott`.

> [!div class="nextstepaction"]
> [Récapitulatif](get-started-netcore-visualstudio-07.md)