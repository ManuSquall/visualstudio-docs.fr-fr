---
title: Commutateurs de Command-Line devenv pour le développement VSPackage | Microsoft Docs
description: Découvrez comment les développeurs peuvent automatiser des tâches à partir de la ligne de commande lors de l’exécution de devenv.exe, le fichier qui démarre l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ea08b4714a79e09fce5933b67997a032532481f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904241"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Commutateurs de ligne de commande devenv pour le développement VSPackage

Visual Studio permet aux développeurs d’automatiser des tâches à partir de la ligne de commande lors de l’exécution de `devenv.exe` , le fichier qui démarre l’IDE de Visual Studio.

 Les tâches sont les suivantes :

- Déploiement d’applications dans des configurations prédéfinies à partir de l’extérieur de l’IDE.

- Génération automatique de projets à l’aide de paramètres de génération prédéfinis ou de configurations de débogage.

- Chargement de l’IDE dans des configurations spécifiques, tout en dehors de l’IDE. Vous pouvez également personnaliser l’IDE lors du lancement.

## <a name="guidelines-for-switches"></a>Instructions pour les commutateurs

La documentation de Visual Studio décrit les commutateurs de ligne de commande au niveau de l’utilisateur `devenv` . Pour plus d’informations, consultez [commutateurs de ligne de commande devenv](../ide/reference/devenv-command-line-switches.md). L' `devenv` outil prend également en charge des commutateurs de ligne de commande supplémentaires qui sont utiles pour le développement, le déploiement et le débogage VSPackage.

| Commutateur de ligne de commande | Description |
|---------------------| - |
| `/ResetSkipPkgs` | Efface toutes les options de chargement par omission qui ont été ajoutées par les utilisateurs qui souhaitent éviter de charger les VSPackages problématiques, puis démarre Visual Studio. La présence d’une balise SkipLoading désactive le chargement d’un VSPackage. La désactivation de la balise réactive le chargement du VSPackage.<br /><br /> Ce commutateur ne prend aucun argument. |
| `/RootSuffix` | Démarre Visual Studio à l’aide d’un autre emplacement. La commande suivante est exécutée par le raccourci créé par le programme d’installation du kit de développement logiciel (SDK) Visual Studio :<br /><br /> `devenv /RootSuffix exp`<br /><br /> Dans ce cas, `exp` identifie un emplacement avec un suffixe particulier (par exemple, `10.0Exp` au lieu de `10.0` ). L’instance expérimentale vous permet de déboguer un VSPackage séparément de l’instance de Visual Studio que vous utilisez pour écrire du code.<br /><br /> Ce commutateur peut prendre n’importe quelle chaîne qui identifie un emplacement que vous avez créé à l’aide de VSRegEx.exe. Pour plus d’informations, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Lance Visual Studio en mode sans échec, en chargeant uniquement les services et l’IDE par défaut. Le `/SafeMode` commutateur empêche le chargement de tous les VSPackages tiers au démarrage de Visual Studio, garantissant ainsi une exécution stable.<br /><br /> Ce commutateur ne prend aucun argument. |
| `/Setup` | Force Visual Studio à fusionner les métadonnées de ressource qui décrivent les menus, les barres d’outils et les groupes de commandes de tous les VSPackages disponibles. Vous ne pouvez exécuter cette commande qu’en tant qu’administrateur. <br /><br /> Ce commutateur ne prend aucun argument. La commande `devenv /Setup` est généralement utilisée comme dernière étape du processus d’installation. L’utilisation du `/Setup` commutateur ne démarre pas l’IDE.|
| `/Splash` | Affiche l’écran de démarrage de Visual Studio, comme d’habitude, puis affiche une boîte de message avant d’afficher l’IDE principal. La boîte de message vous permet d’étudier l’écran de démarrage (par exemple, pour rechercher une icône de produit VSPackage).<br /><br /> Ce commutateur ne prend aucun argument. |

## <a name="see-also"></a>Voir aussi

- [Ajouter des commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md)
- [Commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md)
