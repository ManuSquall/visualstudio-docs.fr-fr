---
title: Présentation des configurations de build
description: Cet article décrit les différentes configurations de build dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128397"
---
# <a name="understanding-build-configurations"></a>Présentation des configurations de build

Vous pouvez stocker différentes configurations de propriétés de solution et de projet à utiliser dans différents types de builds pendant le processus de développement. Les projets créés par Visual Studio pour Mac à l’aide d’un modèle comprennent généralement des configurations Debug et Release qui prennent en charge le débogage d’une application et le déploiement d’une application, respectivement. 

Si vous souhaitez créer des configurations personnalisées, voir [Créer et modifier les configurations de construction](/visualstudio/mac/create-and-edit-configurations).

>[!NOTE]
>Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, voir [Comprendre construire des configurations](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Configurations de solution

Les configurations de solutions sont utilisées pour spécifier les configurations de tous les projets dans une solution. En utilisant l’onglet **Configuration Mappings** sous l’élément **Configuration > Configurations,** vous pouvez attribuer une configuration cible pour chaque élément de la solution ouverte. Ceci est démontré dans l’image suivante :

![Options de mappage de configuration](media/projects-and-solutions-image3.png)

Pour plus d’informations sur les configurations, reportez-vous à la vidéo [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) de James Montemagno.

## <a name="project-build-configurations"></a>Configurations de build d’un projet

Les projets ont tendance à avoir plusieurs configurations. La configuration et la plate-forme d’un projet cibles sont utilisés ensemble pour spécifier les propriétés à utiliser quand il est construit. Le passage d’une configuration à l’autre permet des sorties différentes au moment de la construction. Par exemple, la sortie d’une configuration Debug comprend des symboles de débogage, ce qui permet au débogueur de résoudre les noms de fonction, les paramètres ou les variables à partir de la trace de la pile d’une application qui s’est bloquée. Bien que ces informations supplémentaires soient utiles lors du développement, elles entraînent l’augmentation de la taille d’un fichier, ce qui n’est pas idéal pour la distribution.

Chaque plateforme a des configurations spécifiques pour sa génération. Les pages de configuration de construction pour les projets peuvent être consultées en naviguant vers la section **Build** dans le dialogue **Options de projet.** Ouvrez ce dialogue en cliquant à droite sur le projet et en sélectionnant **options** ou en faisant deux clics sur le projet dans l’explorateur de solution.

## <a name="run-configuration"></a>Configuration de série de tests

Visual Studio pour Mac vous permet de définir une _configuration de course_. Les configurations d’exécution sont présentées dans une liste déroulante dans la barre d’outils, en regard du sélecteur de configuration de build, comme illustré ci-dessous :

![Listé déroulante Configuration d’exécution](media/projects-and-solutions-image8.png)

Une configuration d’exécution est un ensemble d’options d’exécution avec un nom et plusieurs configurations qui sont définies dans un projet à des fins différentes. Les configurations d’exécution sont définies au niveau du projet, et un défaut sera créé automatiquement pour chaque projet exécutable, bien qu’il soit possible d’en ajouter autant que nécessaire. Certains types de projets génèrent automatiquement des configurations d’exécution supplémentaires. Par exemple, les projets watchOS peuvent générer des _configurations Glance et Notification._

Les configurations peuvent être partagées avec d’autres développeurs (auquel cas les configurations seront stockées dans le fichier .csproj) ou conservées localement (dans ce cas, elles seront stockées dans un fichier .user).

### <a name="android-run-configurations"></a>Configurations d’exécution Android

Les configurations d’exécution pour les projets Android permettent la spécification d’une activité, d’un service ou d’un récepteur de diffusion particulier pour lancer lors de l’exécution ou de la débogage du projet. Vous pouvez passer des données supplémentaires et définir des drapeaux d’intention pour tester vos composants dans différentes conditions de lancement.

Pour le débogage sur un appareil physique, vous devez ajouter `Exported=true` à l’attribut Activity pour les activités autres que `MainLauncher` ou définir des filtres intentionnels.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Exemples de données pouvant être incluses dans les configurations d’exécution

La liste ci-dessous fournit quelques exemples de données qui peuvent être incluses dans les configurations d’exécution :

* Projet .NET normal
  * Application de démarrage alternative
  * Arguments du démarrage
  * Répertoire de travail
  * Variables d'environnement
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
