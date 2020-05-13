---
title: Utilisation d’un cadre de forfait géré pour un type de projet (C) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704122"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Utilisation de l’infrastructure de package gérée pour implémenter un type de projet (C#)
Le Cadre de paquet géré (MPF) offre des classes CMD que vous pouvez utiliser ou hériter pour mettre en œuvre vos propres types de projets. Le MPF implémente de nombreuses interfaces que Visual Studio s’attend à ce qu’un type de projet fournisse, vous laissant libre de vous concentrer sur la mise en œuvre des détails de votre type de projet.

## <a name="using-the-mpf-project-source-code"></a>Utilisation du code source du projet MPF
 Le Cadre de paquet géré pour les projets (MPFProj) offre des cours d’aide pour la création et la gestion de nouveaux systèmes de projet. Contrairement à d’autres classes du MPF, les classes de projet ne sont pas incluses dans les assemblages expédiés avec Visual Studio. Au lieu de cela, les classes de projet sont fournies comme code source au [MPF pour les projets 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Pour ajouter ce projet à votre solution VSPackage, faites ce qui suit :

1. Téléchargez les fichiers MPFProj sur *MPFProjectDir*.

2. Dans le *fichier MPFProjectDir*'Dev10'Src’CSharp’ProjectBase.file, modifiez le bloc suivant :

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Créez un projet VSPackage.

2. Déchargez le projet VSPackage.

3. Modifier le fichier VSPackage .csproj en ajoutant `<Import>` le bloc suivant avant les autres blocs:

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

3. Rouvrir le projet VSPackage. Vous devriez voir un nouvel annuaire nommé ProjectBase.

4. Ajoutez la référence suivante au projet VSPackage :

     Microsoft.Build.Tasks.4.0

5. Créez le projet.

## <a name="hierarchy-classes"></a>Classes de hiérarchie
 Le tableau suivant résume les classes du MPFProj qui soutiennent les hiérarchies de projets. Pour plus d’informations, voir [Hiérarchies et Sélection](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Classes de traitement des documents
 Le tableau suivant répertorie les classes du MPF qui prennent en charge le traitement des documents. Pour plus d’informations, voir [Les éléments du projet d’ouverture et d’économie](../../extensibility/internals/opening-and-saving-project-items.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Classes de configuration et de sortie
 Le tableau suivant répertorie les classes du MPF qui permettent aux types de projets de prendre en charge plusieurs configurations, telles que le débbug et la libération, ainsi que les collections de production de projets. Pour plus d’informations, voir [Options de configuration de gestion](../../extensibility/internals/managing-configuration-options.md).

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Cours d’automatisation-soutien
 Le tableau suivant répertorie les classes du MPF qui prennent en charge l’automatisation afin que les utilisateurs de votre type de projet puissent écrire des add-ins.

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classes de propriétés
 Le tableau suivant répertorie les classes du MPF qui permettent aux types de projets d’ajouter des propriétés que les utilisateurs peuvent parcourir et modifier dans un navigateur de propriété.

|Nom de classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
