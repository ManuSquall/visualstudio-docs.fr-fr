---
title: Utilisation de MSBuild | Microsoft Docs
description: MSBuild fournit un format XML extensible pour créer des fichiers projet qui décrivent entièrement les éléments de projet à générer, les tâches de génération et les configurations de Build.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8891d9674a952f0272855c8b9203109ad2e22468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090692"
---
# <a name="using-msbuild"></a>Utilisation de MSBuild
MSBuild fournit un format XML bien défini et extensible pour créer des fichiers projet qui décrivent entièrement les éléments de projet à générer, les tâches de génération et les configurations de Build.

## <a name="general-msbuild-considerations"></a>Considérations générales relatives à MSBuild
 Les fichiers de projet MSBuild, par exemple, les [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] fichiers. csproj et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . vbproj, contiennent des données qui sont utilisées au moment de la génération, mais peuvent également contenir des données qui sont utilisées au moment de la conception. Les données au moment de la génération sont stockées à l’aide de primitives MSBuild, y compris élément élément [(MSBuild)](../../msbuild/item-element-msbuild.md) et [élément de propriété (MSBuild)](../../msbuild/property-element-msbuild.md). Les données au moment du design, qui sont des données spécifiques au type de projet et aux sous-types de projet associés, sont stockées dans un fichier XML de forme libre réservé.

 MSBuild n’a pas de prise en charge native pour les objets de configuration, mais fournit des attributs conditionnels pour spécifier des données spécifiques à la configuration. Par exemple :

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Pour plus d’informations sur les attributs conditionnels, consultez [constructions conditionnelles](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Extension de MSBuild pour votre type de projet
 Les interfaces et API MSBuild sont susceptibles d’être modifiées dans les futures versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Par conséquent, il est prudent d’utiliser les classes MPF (Managed package Framework), car elles fournissent une protection contre les modifications.

 Managed package Framework for Projects (MPFProj) fournit des classes d’assistance pour la création et la gestion d’un nouveau système de projet. Vous pouvez trouver le code source et les instructions de compilation dans [MPF pour les projets-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Les classes MPF spécifiques au projet sont les suivantes :

|Classe|Implémentation|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` la classe est un wrapper pour les éléments MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Générateurs de fichier unique et tâches MSBuild
 Les générateurs de fichiers uniques sont accessibles uniquement au moment de la conception, mais les tâches MSBuild peuvent être utilisées au moment de la conception et au moment de la génération. Pour une flexibilité maximale, par conséquent, utilisez des tâches MSBuild pour transformer et générer du code. Pour plus d’informations, consultez [outils personnalisés](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Voir aussi
- [Référence MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Outils personnalisés](../../extensibility/internals/custom-tools.md)
