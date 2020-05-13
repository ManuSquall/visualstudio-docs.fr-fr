---
title: Prise en charge des propriétés de projet et de configuration (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704902"
---
# <a name="support-for-project-and-configuration-properties"></a>Prise en charge des propriétés de configuration et de projet
La fenêtre **Propriétés** dans l’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) peut afficher les propriétés du projet et de la configuration. Vous pouvez fournir une page de propriété pour votre propre type de projet afin que l’utilisateur puisse définir des propriétés pour votre application.

 En sélectionnant un nœud de projet dans **Solution Explorer,** puis en cliquant sur **Properties** sur le menu **du projet,** vous pouvez ouvrir une boîte de dialogue qui comprend des propriétés de projet et de configuration. Dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]et , et les types de projet dérivés de ces langues, cette boîte de dialogue apparaît comme une page tabbed dans le [général, l’environnement, les options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md). Pour plus d’informations, voir [Not in Build: Walkthrough: Exposing Project and Configuration Properties (C)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Le Cadre de paquet géré pour les projets (MPFProj) offre des cours d’aide pour la création et la gestion de nouveaux systèmes de projet. Vous pouvez trouver le code source et les instructions de compilation à [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistance des propriétés de projet et de configuration
 Les propriétés de projet et de configuration sont persistées dans un fichier de projet qui a n’importe quelle extension de nom de fichier associée au type de projet, par exemple, .csproj, .vbproj, et .myproj. Les projets linguistiques utilisent généralement un fichier de modèle pour générer le fichier de projet. Cependant, il existe en fait plusieurs façons d’associer les types de projets et les modèles. Pour plus d’informations, voir [Description de l’annuaire Template (. Vsdir) Fichiers](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Les propriétés de projet et de configuration sont créées en ajoutant des éléments au fichier de modèle. Ces propriétés sont ensuite disponibles pour tout projet créé en utilisant le type de projet qui utilise ce modèle. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projets et le MPFProj utilisent tous deux le [schéma Not in Build: MSBuild Overview](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) pour les fichiers modèles. Ces fichiers ont une section PropertyGroup pour chaque configuration. Les propriétés des projets sont généralement persistées dans la première section PropertyGroup, qui a un argument de configuration réglé à une corde nulle.

 Le code suivant montre le début d’un fichier de projet MSBuild de base.

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

 Dans ce fichier `<Name>` `<SchemaVersion>` de projet, `<Optimize>` et sont des propriétés de projet, et est une propriété de configuration.

 Il incombe au projet de poursuivre les propriétés du projet et de la configuration du dossier du projet.

> [!NOTE]
> Un projet peut optimiser la persistance en persistant uniquement les valeurs de propriété qui diffèrent de leurs valeurs par défaut.

## <a name="support-for-project-and-configuration-properties"></a>Prise en charge des propriétés de configuration et de projet
 La `Microsoft.VisualStudio.Package.SettingsPage` classe implémente les pages de propriété de projet et de configuration. La mise `SettingsPage` en œuvre par défaut des propriétés publiques offre des propriétés publiques à un utilisateur dans une grille de propriété générique. La `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` méthode sélectionne les `SettingsPage` classes dérivées des réseaux de propriété du projet. La `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` méthode sélectionne les `SettingsPage` classes dérivées des grilles de propriété de configuration. Votre type de projet devrait passer outre à ces méthodes pour sélectionner les pages de propriété appropriées.

 La `SettingsPage` classe `Microsoft.VisualStudio.Package.ProjectNode` et la classe offrent ces méthodes pour maintenir les propriétés de projet et de configuration :

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`et `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` persistent propriétés du projet.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`et `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` les propriétés de configuration persistantes.

  > [!NOTE]
  > Les implémentations `Microsoft.VisualStudio.Package.SettingsPage` et `Microsoft.Build.BuildEngine` `Microsoft.VisualStudio.Package.ProjectNode` les classes utilisent les méthodes (MSBuild) pour obtenir et définir les propriétés du projet et de la configuration à partir du dossier du projet.

  La classe que `SettingsPage` vous `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` dérivez doit implémenter et pour maintenir les propriétés de projet ou de configuration du fichier de projet.

## <a name="provideobjectattribute-and-registry-path"></a>FournirObjectAttribute et Le chemin du registre
 Les classes `SettingsPage` dérivées sont conçues pour être partagées sur VSPackages. Pour permettre à un VSPackage de créer `SettingsPage`une `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` classe dérivée, `Microsoft.VisualStudio.Shell.Package`ajouter un à une classe dérivée de .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Le VSPackage auquel l’attribut est attaché n’est pas important. Lorsqu’un VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]est enregistré auprès de , l’id de classe (CLSID) <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> de tout objet qui peut être créé est enregistré afin qu’un appel pour pouvoir le créer.

 Le chemin de registre d’un objet <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>qui peut être créé est déterminé en combinant, le mot, CLSID, et le guid du type d’objet. Si `MyProjectPropertyPage` la classe a un guid de 3c693da2-5bca-49b3-bd95-ffe0a39dd723 et l’utilisateurRegistryRoot est HKEY_CURRENT_USER-Logiciel-Microsoft-VisualStudio-8.0Exp, alors la voie de registre serait HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0Exp-CLSID\\'3c693da2-5bca-49b3-bd95-ffe0a39dd723'.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Attributs et aménagement de propriétés de projet et de configuration
 Le <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute> , et les attributs déterminent la disposition, l’étiquetage et la description des propriétés de projet et de configuration dans une page de propriété générique. Ces attributs déterminent la catégorie, le nom d’affichage et la description de l’option, respectivement.

> [!NOTE]
> Attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisent les ressources de chaîne pour la localisation et sont définis dans [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Prenons le fragment de code suivant :

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 La `MyConfigProp` propriété de configuration apparaît sur la page de propriété de configuration comme **Ma propriété Config** dans la catégorie, **Ma catégorie**. Si l’option est sélectionnée, la description, **Ma description**, apparaît dans le panneau de description.

## <a name="see-also"></a>Voir aussi
- [Ajout et suppression de pages de propriétés](../../extensibility/adding-and-removing-property-pages.md)
- [Projets](../../extensibility/internals/projects.md)
- [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
