---
title: Présentation des configurations de build
description: Cet article décrit les différentes configurations de build dans Visual Studio pour Mac
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 7f130f5dec77e0a1965c68cf71e642fdb636832f
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568871"
---
# <a name="understanding-build-configurations"></a>Présentation des configurations de build

## <a name="project-build-configurations"></a>Configurations de build d’un projet

Les projets peuvent avoir plusieurs configurations, et passer de l’une à l’autre permet différentes sorties au moment de la génération. Par exemple, la sortie d’une configuration Debug comprend des symboles de débogage, ce qui permet au débogueur de résoudre les noms de fonction, les paramètres ou les variables à partir de la trace de la pile d’une application qui s’est bloquée. Bien que ces informations supplémentaires soient utiles lors du développement, elles entraînent l’augmentation de la taille d’un fichier, ce qui n’est pas idéal pour la distribution.

Chaque plateforme a des configurations spécifiques pour sa génération.

## <a name="solution-configurations"></a>Configurations de solution

Comme pour les configurations de projet, les configurations de solution sont utilisées pour créer des configurations personnalisées pour un projet entier. Sous l’onglet **Mappages de configuration** , sous l’élément **Build > Configurations** , vous pouvez affecter une configuration cible pour chaque élément de la solution, comme illustré dans l’image suivante :

![Options de mappage de configuration](media/projects-and-solutions-image3.png)

Pour plus d’informations sur les configurations, reportez-vous à la vidéo [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) de James Montemagno.

## <a name="run-configuration"></a>Configuration d’exécution

Dans les versions précédentes de Xamarin Studio, vous pouviez sélectionner une option pour définir un projet en tant que **Projet de démarrage**, qui est le projet exécuté/débogué quand vous utilisez la commande générale exécuter/déboguer. Le nom du projet était indiqué en gras dans le panneau des projets.

Dans Visual Studio pour Mac, au lieu de définir un projet de démarrage, vous pouvez définir une _configuration d’exécution_. Les configurations d’exécution sont présentées dans une liste déroulante dans la barre d’outils, en regard du sélecteur de configuration de build, comme illustré ci-dessous :

![Listé déroulante Configuration d’exécution](media/projects-and-solutions-image8.png)

Une configuration d’exécution est un ensemble d’options d’exécution avec un nom et plusieurs configurations qui sont définies dans un projet à des fins différentes. Les configurations d’exécution sont définies au niveau du projet, et une configuration par défaut est créée automatiquement pour chaque projet exécutable, même s’il est possible d’en ajouter autant que nécessaire. Certains types de projets génèrent automatiquement des configurations d’exécution supplémentaires. Par exemple, les projets watchOS peuvent générer des  _configurations Coup d’œil et Notification_.

Vous pouvez partager les configurations avec d’autres développeurs (auquel cas, elles sont stockées dans le fichier .csproj) ou les conserver localement (auquel cas, elles sont stockées dans un fichier .user).

### <a name="android-run-configurations"></a>Configurations d’exécution Android

Les configurations d’exécution pour les projets Android vous permettent de spécifier l’activité, le service ou le récepteur de diffusion qui doit être lancé lors de l’exécution ou du débogage du projet. Vous pouvez passer des données supplémentaires intentionnelles et définir des indicateurs intentionnels pour pouvoir tester vos composants dans différentes conditions de lancement.

Pour le débogage sur un appareil physique, vous devez ajouter `Exported=true` à l’attribut Activity pour les activités autres que `MainLauncher` ou définir des filtres intentionnels.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Exemples de données pouvant être incluses dans les configurations d’exécution

La liste ci-dessous fournit quelques exemples de données qui peuvent être incluses dans les configurations d’exécution :

* Projet .NET normal
    * Application de démarrage alternative
    * Arguments du démarrage
    * Répertoire de travail
    * Variables d’environnement
    * Options de runtime Mono (à utiliser uniquement lors de l’exécution sur Mono)
* Projet Android
    * Point d’entrée (activité, service, récepteur)
    * Arguments et données intentionnels
* Projet iOS
    * Mode (Normal, Récupération en arrière-plan)
* Projet d’extension iOS
    * Application de démarrage : par défaut ou personnalisée
* Projet WatchKit
    * Mode (Coup d’œil, Notification)
    * Charge utile de la notification

## <a name="see-also"></a>Voir aussi

- [Présentation des configurations de build (Visual Studio sur Windows)](/visualstudio/ide/understanding-build-configurations)