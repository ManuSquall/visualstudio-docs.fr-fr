---
title: Utilisation d’une infrastructure de package managée pour un type de projet (C#) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704122"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Utilisation de l’infrastructure de package gérée pour implémenter un type de projet (C#)
Managed package Framework (MPF) fournit des classes C# que vous pouvez utiliser ou hériter de pour implémenter vos propres types de projets. Le MPF implémente un grand nombre des interfaces que Visual Studio attend pour fournir un type de projet, ce qui vous permet de vous concentrer sur l’implémentation des détails de votre type de projet.

## <a name="using-the-mpf-project-source-code"></a>Utilisation du code source du projet MPF
 Managed package Framework for Projects (MPFProj) fournit des classes d’assistance pour la création et la gestion d’un nouveau système de projet. Contrairement aux autres classes du MPF, les classes de projet ne sont pas incluses dans les assemblys fournis avec Visual Studio. Au lieu de cela, les classes de projet sont fournies en tant que code source sur [MPF pour les projets 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Pour ajouter ce projet à votre solution VSPackage, procédez comme suit :

1. Téléchargez les fichiers MPFProj sur *MPFProjectDir*.

2. Dans le \Dev10\Src\CSharp\ProjectBase.file *MPFProjectDir*, modifiez le bloc suivant :

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Créez un projet VSPackage.

2. Déchargez le projet VSPackage.

3. Modifiez le fichier VSPackage. csproj en ajoutant le bloc suivant avant les autres `<Import>` blocs :

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Enregistrez le projet.

2. Fermez et rouvrez la solution VSPackage.

3. Rouvrez le projet VSPackage. Vous devez voir un nouveau répertoire nommé ProjectBase.

4. Ajoutez la référence suivante au projet VSPackage :

     Microsoft. Build. Tasks. 4.0

5. Créez le projet.

## <a name="hierarchy-classes"></a>Classes de hiérarchie
 Le tableau suivant récapitule les classes du MPFProj qui prennent en charge les hiérarchies de projet. Pour plus d’informations, consultez [hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Classes de gestion de documents
 Le tableau suivant répertorie les classes du MPF qui prennent en charge la gestion des documents. Pour plus d’informations, consultez [ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Classes de sortie et de configuration
 Le tableau suivant répertorie les classes du MPF qui permettent aux types de projet de prendre en charge plusieurs configurations, telles que Debug et Release, ainsi que des collections de sortie de projet. Pour plus d’informations, consultez [gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automation-classes de prise en charge
 Le tableau suivant répertorie les classes du MPF qui prennent en charge l’automatisation afin que les utilisateurs de votre type de projet puissent écrire des compléments.

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classes de propriétés
 Le tableau suivant répertorie les classes du chargeur multifonctions qui permettent aux types de projets d’ajouter des propriétés que les utilisateurs peuvent parcourir et modifier dans un Explorateur de propriétés.

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
