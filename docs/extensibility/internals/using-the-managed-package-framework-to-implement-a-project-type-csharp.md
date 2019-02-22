---
title: À l’aide de Managed Package Framework pour un Type de projet (c#) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdefaf3dfbce124ecfee9ab6f5c0479fe12930f8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627764"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Utilisation de l’infrastructure de package gérée pour implémenter un type de projet (C#)
Managed Package Framework (MPF) fournit les classes c# vous pouvez utiliser ou hériter pour implémenter vos propres types de projet. MPF implémente la plupart des interfaces de que Visual Studio attend un type de projet pour fournir, en vous laissant permettant de vous concentrer sur l’implémentation de l’exactitude de votre type de projet.

## <a name="using-the-mpf-project-source-code"></a>En utilisant le Code Source du projet MPF
 Managed Package Framework pour les projets (MPFProj) fournit des classes d’assistance pour créer et gérer le nouveau système de projet. Contrairement aux autres classes dans le MPF, les classes du projet ne sont pas inclus dans les assemblys fournis avec Visual Studio. Au lieu de cela, les classes du projet sont fournis en tant que code source à [MPF de projets 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Pour ajouter ce projet à votre solution VSPackage, procédez comme suit :

1.  Télécharger les fichiers MPFProj à *MPFProjectDir*.

2.  Dans le *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, modifiez le bloc suivant :

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1.  Créez un projet VSPackage.

2.  Décharger le projet VSPackage.

3.  Modifier le fichier .csproj VSPackage en ajoutant le bloc suivant avant les autres `<Import>` blocs :

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1.  Enregistrez le projet.

2.  Fermez et rouvrez la solution VSPackage.

3.  Rouvrez le projet VSPackage. Vous devriez voir un répertoire nommé ProjectBase.

4.  Ajoutez la référence suivante au projet VSPackage :

     Microsoft.Build.Tasks.4.0

5.  Générez le projet.

## <a name="hierarchy-classes"></a>Hiérarchie des Classes
 Le tableau suivant récapitule les classes dans le MPFProj qui prennent en charge des hiérarchies de projet. Pour plus d’informations, consultez [hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.HierarchyNode`|
|`Microsoft.VisualStudio.Package.ProjectNode`|
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|
|`Microsoft.VisualStudio.Package.FileNode`|
|`Microsoft.VisualStudio.Package.FolderNode`|
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|
|`Microsoft.VisualStudio.Package.ReferenceNode`|
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|
|`Microsoft.VisualStudio.Package.ComReferenceNode`|
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|
|`Microsoft.VisualStudio.Package.BuildDependency`|

## <a name="document-handling-classes"></a>Classes de gestion des documents
 Le tableau suivant répertorie les classes dans le MPF qui prennent en charge la gestion des documents. Pour plus d’informations, consultez [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Configuration et les Classes de sortie
 Le tableau suivant répertorie les classes dans le MPF qui permettent les types de projets prend en charge plusieurs configurations, telles que les versions debug et release et collections de sortie du projet. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Classes de prise en charge Automation
 Le tableau suivant répertorie les classes dans le MPF qui prennent en charge d’automation afin que les utilisateurs de votre type de projet peuvent écrire des compléments.

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classes de propriétés
 Le tableau suivant répertorie les classes dans le MPF qui permettent les types de projets ajouter des propriétés que les utilisateurs peuvent parcourir et modifier dans un Explorateur de propriétés.

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|