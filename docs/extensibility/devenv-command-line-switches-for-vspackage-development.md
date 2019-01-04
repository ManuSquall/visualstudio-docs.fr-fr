---
title: Commutateurs de ligne de commande devenv pour le développement VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4333f7e0c892771ffb9b4643f4814cf3352a8f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820291"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Commutateurs de ligne de commande devenv pour le développement VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet aux développeurs d’automatiser les tâches à partir de la ligne de commande lors de l’exécution *devenv.exe*, le fichier qui démarre l’environnement de développement intégré (IDE) Visual Studio.  

 Tâches :  

-   Déploiement d’applications dans des configurations prédéfinies d’en dehors de l’IDE.  

-   Automatiquement la génération de projets à l’aide de la présélection paramètres de build ou des configurations de débogage.  

-   Chargement de l’IDE dans des configurations spécifiques, à partir d’en dehors de l’IDE. En outre, vous pouvez personnaliser l’IDE lors de son lancement.  

## <a name="guidelines-for-switches"></a>Instructions pour les commutateurs  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documentation décrit les commutateurs de ligne de commande devenv de niveau de l’utilisateur. Pour plus d’informations, consultez [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md). Devenv prend également en charge les commutateurs de ligne de commande supplémentaires qui sont utiles au développement VSPackage, déploiement et débogage.  


| Commutateur de ligne de commande | Description |
|---------------------| - |
| /SafeMode | Lance [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en mode sans échec, chargeant uniquement l’IDE par défaut et les services. Le commutateur /safemode empêche le chargement de tous les packages VS tiers [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] démarre, garantissant ainsi l’exécution stable.<br /><br /> Ce commutateur ne prend aucun argument. |
| /resetskippkgs | Efface tous les ignorer les options de chargement qui ont été ajoutées par les utilisateurs qui souhaitent éviter de charger les VSPackages problématiques, puis démarre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La présence d’une balise SkipLoading désactive le chargement d’un VSPackage. Effacement de la balise réactive le chargement du VSPackage.<br /><br /> Ce commutateur ne prend aucun argument. |
| /rootsuffix | Démarre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l’aide d’un autre emplacement. La commande suivante est exécutée par le raccourci créé par le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] programme d’installation :<br /><br /> devenv /RootSuffix exp<br /><br /> Dans ce cas, exp identifie un emplacement avec un suffixe donné, par exemple 10.0Exp plutôt que 10.0. L’instance expérimentale vous permet de déboguer un VSPackage séparément à partir de l’instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous utilisez pour écrire du code.<br /><br /> Ce commutateur peut prendre n’importe quelle chaîne qui identifie un emplacement que vous avez créé à l’aide de VSRegEx.exe. Pour plus d’informations, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md). |
| /Splash | Affiche la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] écran de démarrage comme d’habitude, puis affiche une boîte de message avant d’afficher l’IDE principal. La boîte de message vous permet d’étudier l’écran de démarrage, pour rechercher une icône de produit VSPackage, par exemple.<br /><br /> Ce commutateur ne prend aucun argument. |

## <a name="see-also"></a>Voir aussi  
 [Ajouter des commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md)   
 [Commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md)