---
title: Prise en charge des propriétés de projet et Configuration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c36ee7332f896ed3228166b2c729a4bc2a4df03c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46496036"
---
# <a name="support-for-project-and-configuration-properties"></a>Prise en charge des propriétés de configuration et de projet
Le **propriétés** fenêtre dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) peut afficher les propriétés de configuration et de projet. Vous pouvez fournir une page de propriétés pour votre propre type de projet afin que l’utilisateur peut définir des propriétés pour votre application.  
  
 En sélectionnant un nœud de projet dans **l’Explorateur de solutions** , puis en cliquant sur **propriétés** sur le **projet** menu, vous pouvez ouvrir une boîte de dialogue qui inclut le projet et la configuration Propriétés. Dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]et le projet de types dérivés de ces langues, cette boîte de dialogue s’affiche comme une page à onglets dans le [général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md). Pour plus d’informations, consultez [pas dans la Build : procédure pas à pas : exposition de propriétés de projet et Configuration (c#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Managed Package Framework pour les projets (MPFProj) fournit des classes d’assistance pour créer et gérer le nouveau système de projet. Vous trouverez la source des instructions de code et la compilation à [MPF pour les projets - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistance de projet et des propriétés de Configuration  
 Propriétés de configuration et de projet sont conservées dans un fichier projet qui a toute extension de nom de fichier associé avec le type de projet, par exemple, .csproj, .vbproj et .myproj. Les projets de langage utilisent généralement un fichier de modèle pour générer le fichier de projet. Toutefois, il existe en fait plusieurs façons d’associer des modèles et des types de projets. Pour plus d’informations, consultez [Description du modèle de répertoire (. Fichiers VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Propriétés de configuration et de projet sont créées en ajoutant des éléments dans le fichier de modèle. Ces propriétés sont ensuite disponibles pour tout projet créé en utilisant le type de projet qui utilise ce modèle. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projets et le MPFProj utilisent tous deux le [pas dans la Build : vue d’ensemble de MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) schéma pour les fichiers de modèle. Ces fichiers ont une section PropertyGroup pour chaque configuration. Propriétés des projets sont généralement conservées dans la première section PropertyGroup, ce qui a un argument de la Configuration de la valeur est une chaîne null.  
  
 Le code suivant montre le début d’un fichier de projet MSBuild base.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 Dans ce fichier de projet, `<Name>` et `<SchemaVersion>` sont des propriétés du projet, et `<Optimize>` est une propriété de configuration.  
  
 Il est la responsabilité du projet pour rendre persistantes les propriétés de projet et la configuration du fichier projet.  
  
> [!NOTE]
>  Un projet peut optimiser la persistance par des valeurs de propriété uniquement persistantes qui diffèrent de leurs valeurs par défaut.  
  
## <a name="support-for-project-and-configuration-properties"></a>Prise en charge des propriétés de configuration et de projet  
 Le `Microsoft.VisualStudio.Package.SettingsPage` classe implémente des pages de propriétés de projet et de configuration. L’implémentation par défaut de `SettingsPage` propose des propriétés publiques à un utilisateur dans une grille de propriétés génériques. Le `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` méthode sélectionne des classes dérivées de `SettingsPage` pour les grilles de propriétés de projet. Le `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` méthode sélectionne des classes dérivées de `SettingsPage` pour les grilles de propriétés de configuration. Votre type de projet doit substituer ces méthodes pour sélectionner les pages de propriétés appropriée.  
  
 Le `SettingsPage` classe et la `Microsoft.VisualStudio.Package.ProjectNode` classe offrent ces méthodes pour rendre persistantes les propriétés de configuration et de projet :  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` et `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` conserver les propriétés du projet.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` et `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` conserver les propriétés de configuration.  
  
    > [!NOTE]
    >  Les implémentations de la `Microsoft.VisualStudio.Package.SettingsPage` et `Microsoft.VisualStudio.Package.ProjectNode` classes utilisent la `Microsoft.Build.BuildEngine` (MSBuild) des méthodes pour obtenir et définir les propriétés de configuration et de projet à partir du fichier projet.  
  
 La classe que vous dérivez de `SettingsPage` doit implémenter `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` et `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` pour conserver les propriétés de configuration du projet ou du fichier projet.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute et chemin d’accès du Registre  
 Les classes dérivées de `SettingsPage` sont conçus pour être partagés entre les VSPackages. Pour permettre à un VSPackage créer une classe dérivée de `SettingsPage`, ajoutez un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` à une classe dérivée de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Le VSPackage à laquelle l’attribut est attaché est sans important. Quand un VSPackage est enregistré avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l’id de classe (CLSID) de n’importe quel objet qui peut être créé est enregistré afin qu’un appel à <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> pouvez la créer.  
  
 Le chemin d’accès de Registre d’un objet qui peut être créé est déterminé en combinant <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, le mot, CLSID et le guid du type d’objet. Si `MyProjectPropertyPage` classe possède un guid de {3c693da2-5bca-49b3-bd95-ffe0a39dd723} et le UserRegistryRoot est HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, alors le chemin d’accès de Registre serait HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projet et les attributs de propriété de Configuration et la disposition  
 Le <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, et <xref:System.ComponentModel.DescriptionAttribute> attributs déterminent la disposition, l’étiquetage et la description des propriétés de projet et de configuration dans une page de propriétés génériques. Ces attributs déterminent la catégorie, le nom complet et description de l’option, respectivement.  
  
> [!NOTE]
>  Attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisez les ressources de type chaîne pour la localisation et sont définies dans [MPF pour les projets - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Prenons le fragment de code suivant :  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 Le `MyConfigProp` propriété configuration apparaît dans la page de propriété de configuration en tant que **mes propriété Config** dans la catégorie, **ma catégorie**. Si l’option est sélectionnée, la description, **ma Description**, apparaît dans le panneau de description.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout et suppression de Pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)   
 [Projets](../../extensibility/internals/projects.md)   
 [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
