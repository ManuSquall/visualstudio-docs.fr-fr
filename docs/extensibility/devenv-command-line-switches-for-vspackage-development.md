---
title: Devenv Command-Line Switches for VSPackage Development (fr) Microsoft Docs
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712194"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Commutateurs de ligne de commande devenv pour le développement VSPackage

Visual Studio permet aux développeurs d’automatiser `devenv.exe`les tâches à partir de la ligne de commande lors de l’exécution, le fichier qui démarre l’IDE Visual Studio.

 Les tâches comprennent :

- Déploiement d’applications dans des configurations préconsignées à partir de l’extérieur de l’IDE.

- Construire automatiquement des projets à l’aide de paramètres de construction prédéfinis ou de déboiffages.

- Chargement de l’IDE dans des configurations spécifiques, le tout de l’extérieur de l’IDE. Vous pouvez également personnaliser l’IDE lors du lancement.

## <a name="guidelines-for-switches"></a>Lignes directrices pour les commutateurs

La documentation Visual Studio décrit `devenv` les commutateurs de ligne de commande au niveau de l’utilisateur. Pour plus d’informations, voir [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md). L’outil `devenv` prend également en charge d’autres commutateurs de ligne de commande qui sont utiles avec le développement, le déploiement et le débogage VSPackage.

| Commutateur de ligne de commande | Description |
|---------------------| - |
| `/ResetSkipPkgs` | Efface toutes les options de chargement sauter qui ont été ajoutés par les utilisateurs qui veulent éviter de charger VSPackages problématiques, puis démarre Visual Studio. La présence d’une balise SkipLoading désactive le chargement d’un VSPackage. Le dégagement de l’étiquette permet le chargement du VSPackage.<br /><br /> Ce commutateur ne prend aucun argument. |
| `/RootSuffix` | Démarre Visual Studio en utilisant un autre emplacement. La commande suivante est gérée par le raccourci créé par l’installateur Visual Studio SDK :<br /><br /> `devenv /RootSuffix exp`<br /><br /> Dans ce `exp` cas, identifie un emplacement avec un `10.0Exp` suffixe `10.0`particulier (par exemple, au lieu de ). L’instance expérimentale vous permet de déboiffer un VSPackage séparément de l’instance de Visual Studio que vous utilisez pour écrire du code.<br /><br /> Ce commutateur peut prendre n’importe quelle chaîne qui identifie un emplacement que vous avez créé en utilisant VSRegEx.exe. Pour plus d’informations, voir [The Experimental Instance](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Lance Visual Studio en mode sans échec, ne chargeant que l’IDE par défaut et les services. L’interrupteur `/SafeMode` empêche tous les VSPackages tiers de se charger lorsque Visual Studio démarre, assurant une exécution stable.<br /><br /> Ce commutateur ne prend aucun argument. |
| `/Setup` | Forces Visual Studio pour fusionner les métadonnées de ressources qui décrivent les menus, les barres d’outils et les groupes de commandement de tous les VSPackages disponibles. Vous ne pouvez exécuter cette commande qu’en tant qu’administrateur. <br /><br /> Ce commutateur ne prend aucun argument. La commande `devenv /Setup` est généralement utilisée comme dernière étape du processus d’installation. L’utilisation `/Setup` de l’interrupteur ne démarre pas l’IDE.|
| `/Splash` | Affiche l’écran d’éclaboussure Visual Studio, comme d’habitude, puis affiche une boîte de message avant de montrer l’IDE principal. La boîte de message vous permet d’étudier l’écran d’éclaboussure (par exemple, pour vérifier une icône de produit VSPackage).<br /><br /> Ce commutateur ne prend aucun argument. |

## <a name="see-also"></a>Voir aussi

- [Ajouter des commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md)
- [Commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md)
