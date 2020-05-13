---
title: Choisir entre vsPackages partagés et versionnés (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739886"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Choisissez entre VSPackages partagés et versions
Différentes versions de Visual Studio peuvent coexister sur le même ordinateur. VSPackages peut prendre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en charge n’importe quel mélange de versions.

 Vous pouvez activer des installations côte à côte de VSPackages à travers deux stratégies, la stratégie partagée ou la stratégie version. Tous deux s’adaptent [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à la présence de versions multiples et associées du cadre .NET.

 Dans la stratégie partagée, un VSPackage est enregistré [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pour une utilisation dans plusieurs versions de . Dans la stratégie versionnée, plusieurs DLS VSPackage sont [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installés, un pour chaque version que vous soutenez.

## <a name="shared-vspackages"></a>VsPackages partagés
 L’utilisation d’un VSPackage partagé est appropriée lorsque vous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]utilisez le même VSPackage dans plusieurs versions de . Pour implémenter un VSPackage partagé, vous devez prendre les mesures suivantes :

- Rendez votre VSPackage compatible avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]plusieurs versions de . Deux façons de le faire sont disponibles :

  - Limitez votre VSPackage à l’utilisation uniquement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] des fonctionnalités de la première version que vous soutenez.

  - Programmez votre VSPackage pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous adapter à la version dans laquelle il est en cours d’exécution. Ensuite, si les requêtes pour les services plus récents échouent, votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage peut offrir d’autres services qui sont pris en charge dans les anciennes versions de .

- Enregistrez votre VSPackage de manière appropriée. Pour plus d’informations, voir [l’enregistrement VSPackage](../extensibility/internals/vspackage-registration.md) et [l’enregistrement VSPackage géré](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Enregistrez les extensions de fichiers de manière appropriée. Pour plus d’informations, voir [Les extensions de noms de fichiers d’enregistrement pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Créez un installateur qui déploie votre VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pour les versions appropriées de . Pour plus d’informations, voir [Installer VSPackages avec Windows Install et](../extensibility/internals/installing-vspackages-with-windows-installer.md) Gestion des [composants](../extensibility/internals/component-management.md).

- Aborder la question des collisions d’enregistrement. Pour plus d’informations, voir [l’enregistrement VSPackage](../extensibility/internals/vspackage-registration.md).

- Assurez-vous que les fichiers partagés et versionnés respectent le comptage des références pour permettre l’installation et la suppression sécuritaires de plusieurs versions. Pour plus d’informations, voir [Gestion des composants](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VsPackages versionnés
 Dans le cadre de la stratégie VSPackage version, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous créez un VSPackage pour chaque version que vous soutenez. Cela est approprié lorsque vous vous attendez à profiter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]des services fournis par des versions ultérieures de , parce que chaque VSPackage peut évoluer sans affecter les autres. Néanmoins, la stratégie version de créer plusieurs binaires, soit à partir d’une base de code unique ou de plusieurs bases de code indépendantes, pourrait impliquer plus de développement initial que la stratégie partagée. En outre, un travail de configuration supplémentaire pourrait être nécessaire parce que vous devez créer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soit une configuration distincte pour chaque version ou une configuration unique qui détecte les versions de ce qui sont installés et que vos supports VSPackage.

## <a name="binary-compatibility"></a>Compatibilité binaire
 En général, la compatibilité binaire permet à des VSPackages à code natif développés avec des versions antérieures de Visual Studio de s’exécuter dans des versions ultérieures de Visual Studio. Cependant, il y a trois exceptions importantes :

- Si votre VSPackage s’appuie sur une version particulière de l’heure [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’exécution de la langue commune, alors il doit déterminer dans quelle version de celui-ci est en cours d’exécution.

- Un VSPackage peut avoir une dépendance à une caractéristique spécifique d’un autre VSPackage ou d’un autre produit. Par conséquent, le VSPackage ne peut fonctionner que lorsque la dépendance est satisfaite.

- Un VSPackage peut être affecté par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un correctif de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sécurité dans un pack de service ou une version ultérieure de . Dans ces cas, un VSPackage développé [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] avec une version antérieure [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de la pourrait ne pas s’exécuter dans les versions de après le correctif de sécurité a été appliqué. Cependant, vous pouvez reconstruire votre paquet avec la version ultérieure et l’avoir également exécuté dans les versions antérieures.

  Les VSPackages gérés doivent être [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] construits à l’aide d’une version et celle [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] qui correspondent à la version cible de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

  En plus de planifier la compatibilité binaire pour vos binaires VSPackage, vous devriez également envisager des formats de fichiers de solution et de projet. Si votre VSPackage crée un nouveau type de projet, vous devez décider s’il peut s’exécuter en une seule version ou dans plusieurs versions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, voir [Mise à niveau des projets personnalisés](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Voir aussi
- [Installation de VSPackages avec installateur Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gestion des composants](../extensibility/internals/component-management.md)
