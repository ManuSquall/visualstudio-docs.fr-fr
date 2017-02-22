---
title: "Choix entre les packages VS partag&#233;s et version | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Côte à côte"
  - "installation de côte à côte"
  - "installation (Visual Studio SDK), côte à côte"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Choix entre les packages VS partag&#233;s et version
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Différentes versions de Visual Studio peuvent coexister sur le même ordinateur. Packages VS peuvent prendre en charge toute combinaison de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versions.  
  
 Vous pouvez activer des installations côte à côte de packages VS via une des deux stratégies, la stratégie partagée ou la stratégie de version. Les deux prendre en charge la présence de plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et associé les versions de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Dans la stratégie partagée, un VSPackage est enregistré pour une utilisation dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans la stratégie de version, plusieurs DLL VSPackage sont installés, une pour chaque version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge.  
  
## Packages VS partagés  
 L'utilisation d'un VSPackage partagé est appropriée lorsque vous utilisez le même VSPackage dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour implémenter un VSPackage partagé, vous devez effectuer les opérations suivantes :  
  
-   Rendre votre VSPackage compatibles avec plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Par conséquent, les deux méthodes d'exécution sont disponibles :  
  
    -   Limiter votre VSPackage à utiliser uniquement les fonctionnalités de la version la plus ancienne de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge.  
  
    -   Programmer votre package VS pour s'adapter à la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sur lequel il s'exécute. Ensuite, si les requêtes pour les nouveaux services échouent, le VSPackage peut offrir d'autres services qui sont pris en charge dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Inscrire votre VSPackage en conséquence. Pour plus d’informations, consultez [Inscription du package VS](../extensibility/internals/vspackage-registration.md) et [Managed VSPackage Registration](http://msdn.microsoft.com/fr-fr/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Inscrire des extensions de fichier en conséquence. Pour plus d'informations, consultez [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Créer un programme d'installation qui déploie votre VSPackage pour les versions appropriées des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [Installation de packages VS avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [Gestion des composants](../extensibility/internals/component-management.md).  
  
-   Résoudre le problème des collisions d'inscription. Pour plus d'informations, consultez [Inscription du package VS](../extensibility/internals/vspackage-registration.md).  
  
-   Ce que les fichiers partagés et version respectent le décompte de références pour permettre la sécurité de l'installation et la suppression de plusieurs versions. Pour plus d'informations, consultez [Gestion des composants](../extensibility/internals/component-management.md).  
  
## Packages VS avec version  
 Sous la stratégie VSPackage avec version, vous créez un VSPackage pour chaque version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge. Cela est approprié lorsque vous souhaitez tirer parti des services fournis par les versions ultérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], car chaque VSPackage peut évoluer sans affecter les autres. Toutefois, la stratégie de version de création de plusieurs fichiers binaires à partir d'une base de code unique ou de plusieurs bases de code indépendant, susceptible d'entraîner plus développement initial à la stratégie partagée. En outre, un travail de paramétrage supplémentaires peut\-être être requis, car vous devez créer un programme d'installation distinct pour chaque version ou une installation unique qui détecte les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui sont installés et que votre VSPackage prend en charge.  
  
## Compatibilité binaire  
 En règle générale, la compatibilité binaire permet de packages VS code natif développés avec les versions antérieures de Visual Studio pour s'exécuter dans les versions ultérieures de Visual Studio. Toutefois, il existe trois exceptions importantes :  
  
-   Si votre package VS s'appuie sur une version particulière du common language runtime, il doit déterminer quelle version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qu'il est en cours d'exécution.  
  
-   Un VSPackage peut avoir une dépendance sur une fonctionnalité spécifique d'un autre package VS ou un autre produit. Par conséquent, le VSPackage peut s'exécuter uniquement lorsque la dépendance est satisfaite.  
  
-   Un VSPackage peut être affecté par un correctif de sécurité dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack ou une version ultérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans ce cas, un VSPackage développées avec une version antérieure de le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] peut ne pas fonctionner dans les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] une fois le correctif de sécurité a été appliqué. Toutefois, vous pouvez reconstruire votre package avec la version plus récente et exécuter également dans les versions antérieures.  
  
 Les VSPackages gérés doivent être générés à l'aide d'une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] qui correspondent à la version cible de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 En plus de la planification de la compatibilité binaire pour vos fichiers binaires VSPackage, également doivent envisager solution et projet des formats de fichier. Si votre VSPackage crée un nouveau type de projet, vous devez décider si elle peut s'exécuter dans une version unique ou dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations, consultez [Mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md).  
  
## Voir aussi  
 [Installation de packages VS avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestion des composants](../extensibility/internals/component-management.md)