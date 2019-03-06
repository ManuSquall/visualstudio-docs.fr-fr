---
title: Choix entre les VSPackages partagés et avec contrôle de version | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 705fe42cf158992bb041ac9b75348f7b25945631
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697505"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Choisissez entre les VSPackages partagés et avec contrôle de version
Différentes versions de Visual Studio peuvent coexister sur le même ordinateur. Packages VS peuvent prendre en charge toute combinaison de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versions.

 Vous pouvez activer des installations côte à côte de VSPackages via une des deux stratégies, la stratégie partagée ou la stratégie avec contrôle de version. Les deux prendre en charge la présence de plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et associées de versions de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

 Dans la stratégie partagée, un VSPackage est inscrit pour une utilisation dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans la stratégie de version, plusieurs DLL de VSPackage sont installés, une pour chaque version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge.

## <a name="shared-vspackages"></a>VSPackages partagés
 L’utilisation d’un VSPackage partagé est appropriée lorsque vous utilisez le VSPackage même dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour implémenter un VSPackage partagé, vous devez effectuer les étapes suivantes :

- Rendre votre VSPackage compatible avec plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Par conséquent, les deux méthodes d’exécution sont disponibles :

  - Limiter votre VSPackage à l’utilisation uniquement les fonctionnalités de la version la plus ancienne de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge.

  - Programmer un VSPackage pour s’adapter à la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans lequel elle s’exécute. Ensuite, si les requêtes de services plus récentes échouer, votre VSPackage peut offrir d’autres services qui sont pris en charge dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Inscrivez votre VSPackage en conséquence. Pour plus d’informations, consultez [l’inscription de VSPackage](../extensibility/internals/vspackage-registration.md) et [l’inscription de VSPackage géré](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Inscrire des extensions de fichier en conséquence. Pour plus d’informations, consultez [l’inscription des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Créer un programme d’installation qui déploie votre VSPackage pour les versions appropriées des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [l’installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [gestion des composants](../extensibility/internals/component-management.md).

- Résoudre le problème des conflits de l’inscription. Pour plus d’informations, consultez [l’inscription de VSPackage](../extensibility/internals/vspackage-registration.md).

- Ce que les fichiers partagés et avec contrôle de version respectent le décompte de références pour autoriser la sécurité de l’installation et suppression de plusieurs versions. Pour plus d’informations, consultez [gestion des composants](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VSPackages avec contrôle de version
 Sous la stratégie de VSPackage avec contrôle de version, vous créez un VSPackage pour chaque version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pris en charge. Cette opération est appropriée si vous prévoyez d’en tirer parti des services fournis par les versions ultérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], car chaque VSPackage peut évoluer sans affecter les autres. Néanmoins, la stratégie avec contrôle de version de création de plusieurs fichiers binaires, à partir d’une seule base de code ou à partir de plusieurs bases de code indépendantes, susceptible d’entraîner plus développement initial à la stratégie partagée. En outre, le programme d’installation supplémentaires travail est peut-être nécessaire, car vous devez créer un programme d’installation distinct pour chaque version ou une installation unique qui détecte les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui sont installés et qui prend en charge de votre VSPackage.

## <a name="binary-compatibility"></a>Compatibilité binaire
 En règle générale, la compatibilité binaire permet aux VSPackages de code natif développés avec les versions antérieures de Visual Studio pour exécuter dans les versions ultérieures de Visual Studio. Toutefois, il existe trois exceptions importantes :

- Si votre VSPackage s’appuie sur une version particulière du common language runtime, elle doit déterminer quelle version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il est en cours d’exécution.

- Un VSPackage peut avoir une dépendance sur une fonctionnalité spécifique d’un autre package Visual Studio ou un autre produit. Par conséquent, le VSPackage peut s’exécuter uniquement lorsque la dépendance est satisfaite.

- Un VSPackage peut être affecté par un correctif de sécurité dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack ou une version ultérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans ce cas, un VSPackage développées avec une version antérieure de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ne peut pas s’exécuter dans les versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] une fois le correctif de sécurité a été appliqué. Toutefois, vous pouvez reconstruire votre package avec la version plus récente et l’exécuter également dans les versions antérieures.

  VSPackages gérés doivent être générés à l’aide d’une version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] qui correspond à la version cible du [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

  En plus de la planification de la compatibilité binaire pour vos fichiers binaires VSPackage, vous également devez prendre en compte la solution et projet des formats de fichier. Si votre package Visual Studio crée un nouveau type de projet, vous devez décider si elle peut s’exécuter dans une version unique ou dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [la mise à niveau des projets personnalisés](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Voir aussi
- [Installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gestion des composants](../extensibility/internals/component-management.md)