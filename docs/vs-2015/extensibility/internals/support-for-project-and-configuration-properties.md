---
title: Prise en charge des propriétés de projet et de configuration | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301066"
---
# <a name="support-for-project-and-configuration-properties"></a>Prise en charge des propriétés de configuration et de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La fenêtre **Propriétés** dans l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] peut afficher les propriétés de projet et de configuration. Vous pouvez fournir une page de propriétés pour votre propre type de projet afin que l’utilisateur puisse définir des propriétés pour votre application.  
  
 En sélectionnant un nœud de projet dans **Explorateur de solutions** puis en cliquant sur **Propriétés** dans le menu **projet** , vous pouvez ouvrir une boîte de dialogue qui comprend les propriétés du projet et de la configuration. Dans [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], et les types de projets dérivés de ces langages, cette boîte de dialogue apparaît sous la forme d’une page à onglets dans la [boîte de dialogue général, environnement, options](../../ide/reference/general-environment-options-dialog-box.md). Pour plus d’informations, consultez [not in Build : procédure pas à pas : exposition des propriétésC#de projet et de configuration ()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Managed package Framework for Projects (MPFProj) fournit des classes d’assistance pour la création et la gestion d’un nouveau système de projet. Vous pouvez trouver le code source et les instructions de compilation dans [MPF pour les projets-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistance des propriétés de projet et de configuration  
 Les propriétés de projet et de configuration sont rendues persistantes dans un fichier projet qui a une extension de nom de fichier associée au type de projet, par exemple,. csproj,. vbproj et. MyProj. Les projets de langage utilisent généralement un fichier de modèle pour générer le fichier projet. Toutefois, il existe plusieurs façons d’associer des types de projet et des modèles. Pour plus d’informations, consultez [plume : modèles Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) et [Description du répertoire de modèles (. Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Les propriétés de projet et de configuration sont créées en ajoutant des éléments au fichier de modèle. Ces propriétés sont ensuite disponibles pour tous les projets créés à l’aide du type de projet qui utilise ce modèle. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projets et les MPFProj utilisent tous deux le schéma [not in Build : MSBuild Overview](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) pour les fichiers modèles. Ces fichiers ont une section PropertyGroup pour chaque configuration. Les propriétés des projets sont généralement conservées dans la première section PropertyGroup, dont l’argument de configuration a pour valeur une chaîne NULL.  
  
 Le code suivant illustre le début d’un fichier projet de base MSBuild.  
  
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
  
 Dans ce fichier projet, `<Name>` et `<SchemaVersion>` sont des propriétés de projet, et `<Optimize>` est une propriété de configuration.  
  
 Il incombe au projet de conserver le projet et les propriétés de configuration du fichier projet.  
  
> [!NOTE]
> Un projet peut optimiser la persistance en persistant uniquement les valeurs de propriété qui diffèrent de leurs valeurs par défaut.  
  
## <a name="support-for-project-and-configuration-properties"></a>Prise en charge des propriétés de configuration et de projet  
 La classe `Microsoft.VisualStudio.Package.SettingsPage` implémente les pages de propriétés de projet et de configuration. L’implémentation par défaut de `SettingsPage` offre des propriétés publiques à un utilisateur dans une grille de propriétés génériques. La méthode `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` sélectionne les classes dérivées de `SettingsPage` pour les grilles des propriétés du projet. La méthode `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` sélectionne les classes dérivées de `SettingsPage` pour les grilles des propriétés de configuration. Votre type de projet doit substituer ces méthodes pour sélectionner les pages de propriétés appropriées.  
  
 La classe `SettingsPage` et la classe `Microsoft.VisualStudio.Package.ProjectNode` offrent ces méthodes pour conserver les propriétés de projet et de configuration :  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` et `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` de conserver les propriétés du projet.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` et `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` des propriétés de configuration persistantes.  
  
  > [!NOTE]
  > Les implémentations des classes `Microsoft.VisualStudio.Package.SettingsPage` et `Microsoft.VisualStudio.Package.ProjectNode` utilisent les méthodes `Microsoft.Build.BuildEngine` (MSBuild) pour récupérer et définir des propriétés de projet et de configuration à partir du fichier projet.  
  
  La classe que vous dérivez de `SettingsPage` doit implémenter `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` et `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` pour conserver les propriétés de projet ou de configuration du fichier projet.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute et chemin du Registre  
 Les classes dérivées de `SettingsPage` sont conçues pour être partagées entre les VSPackages. Pour permettre à un VSPackage de créer une classe dérivée de `SettingsPage`, ajoutez un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` à une classe dérivée de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Le VSPackage auquel est attaché l’attribut n’a pas d’importance. Lorsqu’un VSPackage est inscrit auprès d' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l’ID de classe (CLSID) de tout objet pouvant être créé est inscrit pour qu’un appel à <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> puisse le créer.  
  
 Le chemin d’accès au registre d’un objet qui peut être créé est déterminé par la combinaison <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, du mot, du CLSID et du GUID du type d’objet. Si `MyProjectPropertyPage` classe a un GUID de {3c693da2-5bca-49B3-bd95-ffe0a39dd723} et que le UserRegistryRoot est HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, le chemin d’accès du Registre serait HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49B3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Attributs et disposition des propriétés de projet et de configuration  
 Les attributs <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>et <xref:System.ComponentModel.DescriptionAttribute> déterminent la disposition, l’étiquetage et la description des propriétés de projet et de configuration dans une page de propriétés générique. Ces attributs déterminent respectivement la catégorie, le nom complet et la description de l’option.  
  
> [!NOTE]
> Les attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisent des ressources de type chaîne pour la localisation et sont définis dans [MPF pour les projets-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Prenons le fragment de code suivant :  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 La propriété de configuration `MyConfigProp` apparaît sur la page de propriétés de configuration comme **ma propriété config** dans la catégorie, **ma catégorie**. Si l’option est sélectionnée, la description, **ma description**, s’affiche dans le volet Description.  
  
## <a name="see-also"></a>Voir aussi  
 [Not in Build : procédure pas à pas : exposition des propriétés deC#projet et de configuration ()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Ajout et suppression de pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)   
   d' [État VSPackage](../../misc/vspackage-state.md)  
 [Projets](../../extensibility/internals/projects.md)   
 [Plume : modèles Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
