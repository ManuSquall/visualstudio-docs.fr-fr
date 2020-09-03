---
title: Choix entre les VSPackages partagés et les packages avec version | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821974"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Choix entre les VSPackages partagés et à versions gérées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Différentes versions de Visual Studio peuvent coexister sur le même ordinateur. Les VSPackages peuvent prendre en charge n’importe quelle combinaison de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versions.  
  
 Vous pouvez activer des installations côte à côte de VSPackages à l’aide de l’une des deux stratégies suivantes : la stratégie partagée ou la stratégie avec version. Les deux prennent en charge la présence de plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et des versions associées du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 Dans la stratégie partagée, un VSPackage est inscrit pour une utilisation dans plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dans la stratégie avec version, plusieurs dll VSPackage sont installées, une pour chaque version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous prenez en charge.  
  
## <a name="shared-vspackages"></a>VSPackages partagés  
 L’utilisation d’un VSPackage partagé est appropriée lorsque vous utilisez le même VSPackage dans plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pour implémenter un VSPackage partagé, vous devez effectuer les étapes suivantes :  
  
- Rendez votre VSPackage compatible avec plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Deux méthodes sont disponibles :  
  
  - Limitez votre VSPackage à l’utilisation des fonctionnalités de la version la plus ancienne de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous prenez en charge.  

  - Programmez votre VSPackage pour l’adapter à la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dans laquelle il s’exécute. Ensuite, si les requêtes pour les services plus récents échouent, votre VSPackage peut proposer d’autres services pris en charge dans les versions antérieures de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Inscrivez votre VSPackage de manière appropriée. Pour plus d’informations, consultez [inscription du VSPackage](../extensibility/internals/vspackage-registration.md) et inscription du [VSPackage géré](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Inscrire correctement les extensions de fichier. Pour plus d’informations, consultez [inscription d’extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Créez un programme d’installation qui déploie votre VSPackage pour les versions appropriées de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pour plus d’informations, consultez [installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [gestion des composants](../extensibility/internals/component-management.md).  
  
- Résolvez le problème des collisions d’inscription. Pour plus d’informations, consultez [inscription du VSPackage](../extensibility/internals/vspackage-registration.md).  
  
- Assurez-vous que les fichiers partagés et les fichiers avec version respectent le décompte de références pour permettre une installation et une suppression sécurisées de plusieurs versions. Pour plus d’informations, consultez [gestion des composants](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages avec version  
 Dans la stratégie VSPackage avec version, vous créez un VSPackage pour chaque version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que vous prenez en charge. Cela est approprié lorsque vous vous attendez à tirer parti des services fournis par les versions ultérieures de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , car chaque VSPackage peut évoluer sans affecter les autres. Néanmoins, la stratégie avec version de création de plusieurs binaires, qu’il s’agisse d’une base de code unique ou de plusieurs bases de code indépendantes, peut impliquer un développement initial plus initial que la stratégie partagée. En outre, un travail d’installation supplémentaire peut être nécessaire, car vous devez créer une installation distincte pour chaque version ou une installation unique qui détecte les versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installées et prises en charge par votre VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilité binaire  
 En général, la compatibilité binaire permet aux VSPackages de code natif développés avec des versions antérieures de Visual Studio de s’exécuter dans les versions ultérieures de Visual Studio. Toutefois, il existe trois exceptions importantes :  
  
- Si votre VSPackage s’appuie sur une version particulière du common language runtime, il doit déterminer la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qu’il exécute.  
  
- Un VSPackage peut avoir une dépendance sur une fonctionnalité spécifique d’un autre VSPackage ou d’un autre produit. Par conséquent, le VSPackage peut s’exécuter uniquement lorsque la dépendance est satisfaite.  
  
- Un VSPackage peut être affecté par un correctif de sécurité dans une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Service Pack ou une version ultérieure de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dans ce cas, un VSPackage développé avec une version antérieure du [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] peut ne pas s’exécuter dans les versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] après l’application du correctif de sécurité. Toutefois, vous pouvez régénérer votre package avec la version ultérieure et l’exécuter également dans des versions antérieures.  
  
  Les VSPackages managés doivent être générés à l’aide d’une version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et de [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] qui correspondent à la version cible de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Outre la planification de la compatibilité binaire pour vos fichiers binaires VSPackage, vous devez également tenir compte des formats de fichier de projet et de solution. Si votre VSPackage crée un nouveau type de projet, vous devez décider s’il peut s’exécuter dans une seule version ou dans plusieurs versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pour plus d’informations, consultez [mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestion des composants](../extensibility/internals/component-management.md)
