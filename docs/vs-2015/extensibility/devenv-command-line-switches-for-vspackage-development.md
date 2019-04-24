---
title: Commutateurs de ligne de commande devenv pour le développement VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118043"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Commutateurs de ligne de commande Devenv pour le développement VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permet aux développeurs d’automatiser les tâches à partir de la ligne de commande lors de l’exécution de devenv.exe, le fichier qui démarre l’environnement de développement intégré (IDE) Visual Studio.  
  
 Tâches :  
  
- Déploiement d’applications dans des configurations prédéfinies d’en dehors de l’IDE.  
  
- Automatiquement la génération de projets à l’aide de la présélection paramètres de build ou des configurations de débogage.  
  
- Chargement de l’IDE dans des configurations spécifiques, à partir d’en dehors de l’IDE. En outre, vous pouvez personnaliser l’IDE lors de son lancement.  
  
## <a name="guidelines-for-switches"></a>Instructions pour les commutateurs  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] documentation décrit les commutateurs de ligne de commande devenv de niveau de l’utilisateur. Pour plus d’informations, consultez [commutateurs de ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md). Devenv prend également en charge les commutateurs de ligne de commande supplémentaires qui sont utiles au développement VSPackage, déploiement et débogage.  
  
|Commutateur de ligne de commande|Description|  
|--------------------------|-----------------|  
|/safemode|Lance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en mode sans échec, chargeant uniquement l’IDE par défaut et les services. Le commutateur /safemode empêche le chargement de tous les packages VS tiers [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre, garantissant ainsi l’exécution stable.<br /><br /> Ce commutateur ne prend aucun argument.|  
|/resetskippkgs|Efface tous les ignorer les options de chargement qui ont été ajoutées par les utilisateurs qui souhaitent éviter de charger les VSPackages problématiques, puis démarre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. La présence d’une balise SkipLoading désactive le chargement d’un VSPackage. Effacement de la balise réactive le chargement du VSPackage.<br /><br /> Ce commutateur ne prend aucun argument.|  
|/rootsuffix|Démarre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l’aide d’un autre emplacement. La commande suivante est exécutée par le raccourci créé par le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] programme d’installation :<br /><br /> devenv /RootSuffix exp<br /><br /> Dans ce cas, exp identifie un emplacement avec un suffixe donné, par exemple 10.0Exp plutôt que 10.0. L’instance expérimentale vous permet de déboguer un VSPackage séparément à partir de l’instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous utilisez pour écrire du code.<br /><br /> Ce commutateur peut prendre n’importe quelle chaîne qui identifie un emplacement que vous avez créé à l’aide de VSRegEx.exe. Pour plus d’informations, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).|  
|/splash|Affiche la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] écran de démarrage comme d’habitude, puis affiche une boîte de message avant d’afficher l’IDE principal. La boîte de message vous permet d’étudier l’écran de démarrage, pour rechercher une icône de produit VSPackage, par exemple.<br /><br /> Ce commutateur ne prend aucun argument.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md)   
 [Commutateurs de la ligne de commande Devenv](../ide/reference/devenv-command-line-switches.md)
