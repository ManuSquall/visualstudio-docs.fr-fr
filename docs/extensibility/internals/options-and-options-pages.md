---
title: "Options et les Pages d’Options | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1177a9a4df1f07c93540fa039117c5fa81289e17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="options-and-options-pages"></a>Options et les Pages d’Options
En cliquant sur **Options** sur la **outils** menu s’ouvre le **Options** boîte de dialogue. Les options de cette boîte de dialogue sont collectivement appelées pages d’options. Le contrôle d’arborescence dans le volet de navigation inclut les catégories d’options, et chaque catégorie comporte des pages d’options. Lorsque vous sélectionnez une page, ses options s’affichent dans le volet droit. Ces pages vous permettent de modifier les valeurs des options qui déterminent l’état d’un VSPackage.  
  
## <a name="support-for-options-pages"></a>Prise en charge des Pages d’Options  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fournit la prise en charge pour la création de pages d’options et les catégories d’options. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implémente une page d’options.  
  
 L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> offre ses propriétés publiques à un utilisateur dans une grille générique de propriétés. Vous pouvez personnaliser ce comportement en substituant les différentes méthodes de la page pour créer une page d’options personnalisées qui possède sa propre interface utilisateur (IU). Pour plus d’informations, consultez [création d’une Page d’Options](../../extensibility/creating-an-options-page.md).  
  
 Le <xref:Microsoft.VisualStudio.Shell.DialogPage> la classe implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager>, qui fournit la persistance pour les pages d’options et paramètres utilisateur. Les implémentations par défaut de la <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> et <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> méthodes rendre persistantes les modifications de propriété dans une section de l’utilisateur du Registre si la propriété peut être convertie vers et à partir d’une chaîne.  
  
## <a name="options-page-registry-path"></a>Chemin d’accès du Registre Options Page  
 Par défaut, le chemin d’accès du Registre des propriétés gérée par une page d’options est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, le mot DialogPage et le nom de type de la classe de la page options. Par exemple, une classe de page d’options peut être définie comme suit.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Si la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> est HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, puis les paires nom / valeur de propriété sont des sous-clés de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Le chemin d’accès du Registre de la page d’options lui-même est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, ToolsOptionsPages et les options de la page catégorie et le nom. Par exemple, si la page d’options personnalisées a la catégorie, mon Option de Pages et le <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> est HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la page d’options a la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Attributs de Page Outils/Options et la disposition  
 Le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut détermine le regroupement de pages d’options personnalisées dans les catégories dans l’arborescence de navigation de la **Options** boîte de dialogue. Le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associe une page d’options le VSPackage qui fournit l’interface. Prenons le fragment de code suivant :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Cela déclare que MyPackage fournit deux pages d’options, OptionsPageGeneral et OptionsPageCustom. Dans le **Options** boîte de dialogue, les deux pages d’options s’affichent dans le **mes Pages Option** catégorie comme **général** et **personnalisé**, respectivement.  
  
## <a name="option-attributes-and-layout"></a>Attributs d’option et la disposition  
 L’interface utilisateur (IU) qui fournit de la page détermine l’apparence des options dans une page d’options personnalisées. La mise en page, l’étiquetage et la description des options d’une page générique d’options sont déterminées par les attributs suivants :  
  
-   <xref:System.ComponentModel.CategoryAttribute>Détermine la catégorie de l’option.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>Détermine le nom complet de l’option.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>Détermine la description de l’option.  
  
    > [!NOTE]
    >  Attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisez les ressources de chaîne pour la localisation et sont définies dans le [exemple de projet managé](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Prenons le fragment de code suivant :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 L’option OptionInteger s’affiche dans la page d’options en tant que **entier Option** dans les **mes Options de** catégorie. Si l’option est sélectionnée, la description, **mon option entier**, apparaît dans la zone de description.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>L’accès aux Pages d’Options à partir d’un autre package VS  
 Un VSPackage qui héberge et gère une page d’options par programmation accessibles à partir d’un autre VSPackage à l’aide du modèle automation. Par exemple, dans le code suivant, un VSPackage est enregistré comme une page d’options d’hébergement.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Le fragment de code suivant obtient la valeur de OptionInteger de MyOptionPage :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Lorsque le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut enregistre une page d’options, la page est enregistrée sous la touche AutomationProperties, si le `SupportsAutomation` l’argument de l’attribut est `true`. Automation examine cette entrée de Registre pour trouver le VSPackage associé et l’automatisation, puis accède à la propriété via la page d’options hébergé, dans ce cas, Page de grille.  
  
 Le chemin d’accès du Registre de la propriété automation est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, AutomationProperties et les options de la page catégorie et le nom. Par exemple, si la page d’options a la catégorie Mes, le nom de ma Page de grille et le <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la propriété automation a la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\ Page de grille Microsoft\VisualStudio\8.0Exp\AutomationProperties\My catégorie\Ma.  
  
> [!NOTE]
>  Le nom canonique, Page de grille Category.My, est la valeur de la sous-clé du nom de cette clé.