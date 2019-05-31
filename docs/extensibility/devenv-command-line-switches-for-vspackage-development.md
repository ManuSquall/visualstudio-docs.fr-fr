---
title: Commutateurs de ligne de commande devenv pour le développement VSPackage | Microsoft Docs
ms.date: 12/10/2018
ms.topic: conceptual
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289f31c503143dc2b992717483f4d8701414e09d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348050"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Commutateurs de ligne de commande devenv pour le développement VSPackage

Visual Studio permet aux développeurs d’automatiser les tâches à partir de la ligne de commande lors de l’exécution `devenv.exe`, le fichier qui démarre l’IDE Visual Studio.

 Tâches :

- Déploiement d’applications dans des configurations prédéfinies d’en dehors de l’IDE.

- Automatiquement la génération de projets à l’aide de la présélection paramètres de build ou des configurations de débogage.

- Chargement de l’IDE dans des configurations spécifiques, à partir d’en dehors de l’IDE. Vous pouvez également personnaliser l’IDE lors de son lancement.

## <a name="guidelines-for-switches"></a>Instructions pour les commutateurs

Documentation de Visual Studio décrit le niveau de l’utilisateur `devenv` commutateurs de ligne de commande. Pour plus d’informations, consultez [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md). Le `devenv` prend également en charge les commutateurs de ligne de commande supplémentaires qui sont utiles au développement VSPackage, déploiement et débogage.

| Commutateur de ligne de commande | Description |
|---------------------| - |
| `/ResetSkipPkgs` | Efface toutes les options de chargement de skip qui ont été ajoutées par les utilisateurs qui vous voulez éviter de charger les VSPackages problématiques, puis démarre Visual Studio. La présence d’une balise SkipLoading désactive le chargement d’un VSPackage. Effacement de la balise réactive le chargement du VSPackage.<br /><br /> Ce commutateur ne prend aucun argument. |
| `/RootSuffix` | Démarre Visual Studio à l’aide d’un autre emplacement. La commande suivante est exécutée par le raccourci créé par le programme d’installation du Kit de développement logiciel Visual Studio :<br /><br /> `devenv /RootSuffix exp`<br /><br /> Dans ce cas, `exp` identifie un emplacement avec un suffixe particulier (par exemple, `10.0Exp` au lieu de `10.0`). L’instance expérimentale vous permet de déboguer un VSPackage séparément à partir de l’instance de Visual Studio que vous utilisez pour écrire du code.<br /><br /> Ce commutateur peut prendre n’importe quelle chaîne qui identifie un emplacement que vous avez créé à l’aide de VSRegEx.exe. Pour plus d’informations, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Démarre Visual Studio en mode sans échec, chargeant uniquement l’IDE par défaut et les services. Le `/SafeMode` commutateur empêche le chargement au démarrage de Visual Studio, garantir la stabilité de l’exécution de tous les packages VS tiers.<br /><br /> Ce commutateur ne prend aucun argument. |
| `/Setup` | Force Visual Studio à fusionner les métadonnées des ressources qui décrivent les menus, barres d’outils et des groupes de commandes de tous les packages disponibles. Vous pouvez uniquement exécuter cette commande en tant qu’administrateur. <br /><br /> Ce commutateur ne prend aucun argument. La commande `devenv /Setup` est généralement utilisée comme dernière étape du processus d’installation. Utilisation de la `/Setup` commutateur ne démarre l’IDE.|
| `/Splash` | Indique le démarrage de Visual Studio de l’écran, comme d’habitude, et puis affiche un message indiquant zone avant d’afficher l’IDE principal. La boîte de message vous permet d’étudier l’écran de démarrage (par exemple, pour vérifier une icône de produit VSPackage).<br /><br /> Ce commutateur ne prend aucun argument. |

## <a name="see-also"></a>Voir aussi

- [Ajouter des commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md)
- [Commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md)