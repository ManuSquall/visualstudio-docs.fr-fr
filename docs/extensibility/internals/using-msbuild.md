---
title: Utilisation de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704288"
---
# <a name="using-msbuild"></a>Utilisation de MSBuild
MSBuild fournit un format XML bien défini et extensible pour créer des fichiers de projet qui décrivent entièrement les éléments du projet à construire, construisent des tâches et construisent des configurations.

## <a name="general-msbuild-considerations"></a>Considérations générales MSBuild
 Les fichiers de projet MSBuild, par exemple les [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] fichiers .csproj et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj, contiennent des données qui sont utilisées au moment de la construction, mais peuvent également contenir des données qui sont utilisées au moment de la conception. Les données de build-time sont stockées à l’aide de primitifs MSBuild, y compris [l’élément d’élément (MSBuild)](../../msbuild/item-element-msbuild.md) et [l’élément de propriété (MSBuild).](../../msbuild/property-element-msbuild.md) Les données de temps de conception, qui sont des données spécifiques au type de projet et à tous les sous-types de projets connexes, sont stockées dans des XML gratuits qui lui sont réservés.

 MSBuild n’a pas de support natif pour les objets de configuration, mais fournit des attributs conditionnels pour spécifier des données spécifiques à la configuration. Par exemple :

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Pour plus d’informations sur les attributs conditionnels, voir [Constructions conditionnelles](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Étendre la msBuild pour votre type de projet
 Les interfaces MSBuild et les API peuvent [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]être modifiées dans les futures versions de . Par conséquent, il est prudent d’utiliser les classes de cadre de paquets gérés (MPF) parce qu’elles protègent contre les changements.

 Le Cadre de paquet géré pour les projets (MPFProj) offre des cours d’aide pour la création et la gestion de nouveaux systèmes de projet. Vous pouvez trouver le code source et les instructions de compilation à [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Les classes MPF spécifiques au projet sont les suivantes :

|Classe|Implémentation|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`classe est un emballage pour les articles MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Générateurs de fichiers uniques vs tâches MSBuild
 Les générateurs de fichiers simples sont accessibles uniquement au moment de la conception, mais les tâches MSBuild peuvent être utilisées à l’heure de conception et à l’heure de construction. Pour une flexibilité maximale, utilisez donc les tâches MSBuild pour transformer et générer du code. Pour plus d’informations, voir [Custom Tools](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Outils personnalisés](../../extensibility/internals/custom-tools.md)
