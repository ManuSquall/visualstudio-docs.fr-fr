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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185279"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Commutateurs de ligne de commande Devenv pour le développement VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permet aux développeurs d’automatiser les tâches à partir de la ligne de commande lors de l’exécution de devenv.exe, le fichier qui démarre l’environnement de développement intégré (IDE) de Visual Studio.  
  
 Les tâches sont les suivantes :  
  
- Déploiement d’applications dans des configurations prédéfinies à partir de l’extérieur de l’IDE.  
  
- Génération automatique de projets à l’aide de paramètres de génération prédéfinis ou de configurations de débogage.  
  
- Chargement de l’IDE dans des configurations spécifiques, tout en dehors de l’IDE. En outre, vous pouvez personnaliser l’IDE lors du lancement.  
  
## <a name="guidelines-for-switches"></a>Instructions pour les commutateurs  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la documentation décrit les commutateurs de ligne de commande devenv au niveau de l’utilisateur. Pour plus d’informations, consultez [commutateurs de ligne de commande devenv](../ide/reference/devenv-command-line-switches.md). Devenv prend également en charge des commutateurs de ligne de commande supplémentaires qui sont utiles pour le développement, le déploiement et le débogage VSPackage.  
  
|Commutateur de ligne de commande|Description|  
|--------------------------|-----------------|  
|charger|Démarre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en mode sans échec, en chargeant uniquement les services et l’IDE par défaut. Le commutateur/SafeMode empêche le chargement de tous les VSPackages tiers au [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarrage, garantissant ainsi une exécution stable.<br /><br /> Ce commutateur ne prend aucun argument.|  
|/resetskippkgs|Efface toutes les options de chargement par omission qui ont été ajoutées par les utilisateurs qui souhaitent éviter de charger les VSPackages problématiques, puis démarre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . La présence d’une balise SkipLoading désactive le chargement d’un VSPackage. La désactivation de la balise réactive le chargement du VSPackage.<br /><br /> Ce commutateur ne prend aucun argument.|  
|/rootsuffix|Démarre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l’aide d’un autre emplacement. La commande suivante est exécutée par le raccourci créé par le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] programme d’installation :<br /><br /> /RootSuffix exp de devenv<br /><br /> Dans ce cas, exp identifie un emplacement avec un suffixe particulier, par exemple 10.0 exp au lieu de 10,0. L’instance expérimentale vous permet de déboguer un VSPackage séparément de l’instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous utilisez pour écrire du code.<br /><br /> Ce commutateur peut prendre n’importe quelle chaîne qui identifie un emplacement que vous avez créé à l’aide de VSRegEx.exe. Pour plus d’informations, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).|  
|/splash|Affiche l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] écran de démarrage comme d’habitude, puis affiche une boîte de message avant d’afficher l’IDE principal. La boîte de message vous permet d’étudier l’écran de démarrage pour rechercher une icône de produit VSPackage, par exemple.<br /><br /> Ce commutateur ne prend aucun argument.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de commutateurs de ligne de commande](../extensibility/adding-command-line-switches.md)   
 [Commutateurs de ligne de commande devenv](../ide/reference/devenv-command-line-switches.md)
