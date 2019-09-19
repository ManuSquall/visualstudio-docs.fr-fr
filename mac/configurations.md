---
title: Présentation des configurations de build
description: Cet article décrit les différentes configurations de build dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128397"
---
# <a name="understanding-build-configurations"></a>Présentation des configurations de build

Vous pouvez stocker différentes configurations de propriétés de solution et de projet à utiliser dans différents genres de builds pendant le processus de développement. Les projets créés par Visual Studio pour Mac à l’aide d’un modèle incluent généralement des configurations Debug et Release qui prennent en charge le débogage d’une application et le déploiement d’une application, respectivement. 

Si vous souhaitez créer des configurations personnalisées, consultez [création et modification des configurations de build](/visualstudio/mac/create-and-edit-configurations).

>[!NOTE]
>Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [Présentation des configurations de build](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Configurations de solution

Les configurations de solution sont utilisées pour spécifier des configurations pour tous les projets d’une solution. À l’aide de l’onglet **mappages de configuration** sous l’élément de **Configuration > de builds** , vous pouvez affecter une configuration cible pour chaque élément de la solution ouverte. Cela est illustré dans l’image suivante :

![Options de mappage de configuration](media/projects-and-solutions-image3.png)

Pour plus d’informations sur les configurations, reportez-vous à la vidéo [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) de James Montemagno.

## <a name="project-build-configurations"></a>Configurations de build d’un projet

Les projets ont tendance à avoir plusieurs configurations. La configuration et la plateforme ciblées par un projet sont utilisées ensemble pour spécifier les propriétés à utiliser lors de sa génération. Le basculement entre les configurations permet des sorties différentes au moment de la génération. Par exemple, la sortie d’une configuration Debug comprend des symboles de débogage, ce qui permet au débogueur de résoudre les noms de fonction, les paramètres ou les variables à partir de la trace de la pile d’une application qui s’est bloquée. Bien que ces informations supplémentaires soient utiles lors du développement, elles entraînent l’augmentation de la taille d’un fichier, ce qui n’est pas idéal pour la distribution.

Chaque plateforme a des configurations spécifiques pour sa génération. Les pages de configuration de build pour les projets sont accessibles en accédant à la section **générer** de la boîte de dialogue **Options du projet** . Pour ouvrir cette boîte de dialogue, cliquez avec le bouton droit sur le projet et sélectionnez **options** ou double-cliquez sur le projet dans l’Explorateur de solutions.

## <a name="run-configuration"></a>Configuration d’exécution

Visual Studio pour Mac vous permet de définir une _configuration de série de tests_. Les configurations d’exécution sont présentées dans une liste déroulante dans la barre d’outils, en regard du sélecteur de configuration de build, comme illustré ci-dessous :

![Listé déroulante Configuration d’exécution](media/projects-and-solutions-image8.png)

Une configuration d’exécution est un ensemble d’options d’exécution avec un nom et plusieurs configurations qui sont définies dans un projet à des fins différentes. Les configurations d’exécution sont définies au niveau du projet, et une valeur par défaut est créée automatiquement pour chaque projet exécutable, bien qu’il soit possible d’en ajouter autant que nécessaire. Certains types de projets génèrent automatiquement des configurations d’exécution supplémentaires. Par exemple, les projets watchOS peuvent générer des _configurations Coup d’œil et Notification_.

Les configurations peuvent être partagées avec d’autres développeurs (dans ce cas, les configurations sont stockées dans le fichier. csproj) ou conservées localement (dans ce cas, elles sont stockées dans un fichier. User).

### <a name="android-run-configurations"></a>Configurations d’exécution Android

Les configurations d’exécution pour les projets Android autorisent la spécification d’une activité, d’un service ou d’un récepteur de diffusion particulier à lancer lors de l’exécution ou du débogage du projet. Vous pouvez transmettre des données Intent supplémentaires et définir des indicateurs d’intention pour tester vos composants dans différentes conditions de lancement.

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
