---
title: "Choix entre les VSPackages partagées et la version | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 20613722410bbe57231177eefafec79184d7741f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Choix entre les VSPackages partagés et version
Différentes versions de Visual Studio peuvent coexister sur le même ordinateur. Les VSPackages peut prendre en charge toute combinaison de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versions.  
  
 Vous pouvez activer des installations côte à côte des VSPackages par le biais de deux stratégies, la stratégie partagée ou la stratégie de contrôle de version du. Les deux prendre en charge la présence de plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et associé les versions de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Dans la stratégie partagée, un VSPackage est enregistré pour une utilisation dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans la stratégie de contrôle de version du, plusieurs DLL VSPackage sont installés, une pour chaque version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge.  
  
## <a name="shared-vspackages"></a>Packages VS partagés  
 À l’aide d’un VSPackage partagé est appropriée lorsque vous utilisez le VSPackage même dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour implémenter un VSPackage partagé, vous devez effectuer les étapes suivantes :  
  
-   Rendre votre VSPackage compatibles avec plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Par conséquent, les deux méthodes d’exécution sont disponibles :  
  
    -   Limiter votre VSPackage à l’aide uniquement les fonctionnalités de la version la plus ancienne de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge.  
  
    -   Programmer un VSPackage pour s’adapter à la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans lequel elle s’exécute. Ensuite, si l’échec des requêtes de services plus récents, votre VSPackage peut offrir autres services qui sont pris en charge dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Inscrire votre VSPackage en conséquence. Pour plus d’informations, consultez [VSPackage inscription](../extensibility/internals/vspackage-registration.md) et [gérés de l’inscription du VSPackage](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Inscrire des extensions de fichier en conséquence. Pour plus d’informations, consultez [l’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Créer un programme d’installation qui déploie votre VSPackage pour les versions appropriées des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [l’installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [gestion des composants](../extensibility/internals/component-management.md).  
  
-   Résoudre le problème de collisions de l’inscription. Pour plus d’informations, consultez [VSPackage inscription](../extensibility/internals/vspackage-registration.md).  
  
-   Ce que les fichiers partagés et de contrôle de version du respectent le décompte de références pour autoriser la sécurité de l’installation et la suppression de plusieurs versions. Pour plus d’informations, consultez [gestion des composants](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages avec version  
 Sous la stratégie de contrôle de version du VSPackage, vous créez un VSPackage pour chaque version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge. Cela est approprié lorsque vous prévoyez tirer parti des services fournis par les versions ultérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], car chaque VSPackage peut évoluer sans affecter les autres. Toutefois, la stratégie de version de la création de plusieurs fichiers binaires à partir d’une base de code unique ou à partir de plusieurs bases de code indépendant, susceptible d’entraîner plus développement initial à la stratégie partagée. En outre, les tâches de configuration supplémentaires peut être requis, car vous devez créer un programme d’installation distinct pour chaque version ou un programme d’installation unique qui détecte les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui sont installés et qui prend en charge de votre VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilité binaire  
 En règle générale, la compatibilité binaire permet VSPackages en code natif développés avec les versions antérieures de Visual Studio pour s’exécuter dans les versions ultérieures de Visual Studio. Toutefois, il existe trois exceptions importantes :  
  
-   Si votre VSPackage s’appuie sur une version particulière du common language runtime, elle doit déterminer quelle version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qu’il est en cours d’exécution.  
  
-   Un VSPackage peut avoir une dépendance sur une fonctionnalité spécifique d’un autre VSPackage ou un autre produit. Par conséquent, le VSPackage peut s’exécuter uniquement lorsque la dépendance est satisfaite.  
  
-   Un VSPackage peut être affecté par un correctif de sécurité dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack ou une version ultérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans ce cas, un VSPackage développées avec une version antérieure de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ne peut pas s’exécuter dans les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] après le correctif de sécurité a été appliqué. Toutefois, vous pouvez reconstruire votre package avec la version plus récente et exécuter également dans les versions antérieures.  
  
 VSPackages gérés doivent être générés à l’aide d’une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] qui correspond à la version cible du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 En plus de la planification de la compatibilité binaire pour vos fichiers binaires VSPackage, vous également devez prendre en compte la solution et projet des formats de fichier. Si votre VSPackage crée un nouveau type de projet, vous devez décider si elle peut s’exécuter dans une version unique ou dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [la mise à niveau des projets personnalisés](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Voir aussi  
 [L’installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestion des composants](../extensibility/internals/component-management.md)