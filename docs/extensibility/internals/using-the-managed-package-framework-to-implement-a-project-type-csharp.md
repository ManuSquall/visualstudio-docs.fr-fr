---
title: "À l’aide d’infrastructure du Package managé pour un Type de projet (c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>À l’aide de l’infrastructure du Package managé pour implémenter un Type de projet (c#)
Managed Package Framework (MPF) fournit des classes c# vous pouvez utiliser ou hériter pour implémenter vos propres types de projet. Le MPF implémente de nombreuses interfaces que Visual Studio attend un type de projet pour fournir, en laissant vous concentrer sur l’implémentation de l’exactitude de votre type de projet.  
  
## <a name="using-the-mpf-project-source-code"></a>En utilisant le Code Source du projet MPF  
 Managed Package Framework pour les projets (MPFProj) fournit des classes d’assistance pour créer et gérer le nouveau système de projet. Contrairement à d’autres classes dans le chargeur multifonctions, les classes du projet ne sont pas inclus dans les assemblys fournis avec Visual Studio. Au lieu de cela, les classes du projet sont fournis sous forme de code source à [MPF de projets 2013](http://mpfproj12.codeplex.com).  
  
 Pour ajouter ce projet à votre solution VSPackage, procédez comme suit :  
  
1.  Téléchargez les fichiers MPFProj *MPFProjectDir*.  
  
2.  Dans le *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, modifiez le bloc suivant :  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Créez un projet VSPackage.  
  
2.  Décharger le projet VSPackage.  
  
3.  Modifier le fichier .csproj VSPackage en ajoutant le bloc suivant avant l’autre `<Import>` blocs :  
  
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
  
3.  Rouvrez le projet VSPackage. Vous devez voir un répertoire nommé ProjectBase.  
  
4.  Ajoutez la référence au projet VSPackage suivante :  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Générez le projet.  
  
## <a name="hierarchy-classes"></a>Hiérarchie des Classes  
 Le tableau suivant récapitule les classes qui prennent en charge les hiérarchies de projet dans le MPFProj. Pour plus d’informations, consultez [hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nom de la classe|  
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
 Le tableau suivant répertorie les classes dans le chargeur multifonctions qui prennent en charge la gestion des documents. Pour plus d’informations, consultez [d’ouverture et l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nom de la classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Configuration et les Classes de sortie  
 Le tableau suivant répertorie les classes dans le chargeur multifonctions qui vous permettent de types de projet prend en charge plusieurs configurations, telles que les versions debug et release et collections de sortie du projet. Pour plus d’informations, consultez [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
|Nom de la classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Classes de prise en charge Automation  
 Le tableau suivant répertorie les classes qui prennent en charge d’automation afin que les utilisateurs de votre type de projet peuvent écrire des compléments dans le chargeur multifonctions.  
  
|Nom de la classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Classes de propriétés  
 Le tableau suivant répertorie les classes dans le chargeur multifonctions qui vous permettent de types de projet Ajouter des propriétés que les utilisateurs peuvent parcourir et modifier dans la fenêtre Propriétés.  
  
|Nom de la classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
