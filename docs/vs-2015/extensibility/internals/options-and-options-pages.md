---
title: Options et Pages d’Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 350f0c873a0b6692d16dcbc987db32b63f68be72
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952230"
---
# <a name="options-and-options-pages"></a>Options et pages Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cliquant sur **Options** sur le **outils** menu ouvre le **Options** boîte de dialogue. Les options de cette boîte de dialogue sont collectivement appelées pages d’options. Le contrôle d’arborescence dans le volet de navigation inclut les catégories d’options, et chaque catégorie comporte des pages d’options. Lorsque vous sélectionnez une page, ses options apparaissent dans le volet droit. Ces pages vous permettent de modifier les valeurs des options qui déterminent l’état d’un VSPackage.  
  
## <a name="support-for-options-pages"></a>Prise en charge des Pages d’Options  
 Le <xref:Microsoft.VisualStudio.Shell.Package> classe fournit la prise en charge pour la création de pages d’options et les catégories d’options. Le <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implémente une page d’options.  
  
 L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> propose ses propriétés publiques à un utilisateur dans une grille générique de propriétés. Vous pouvez personnaliser ce comportement en substituant les différentes méthodes de la page pour créer une page d’options personnalisées qui possède sa propre interface utilisateur (IU). Pour plus d’informations, consultez [création d’une Page d’Options](../../extensibility/creating-an-options-page.md).  
  
 Le <xref:Microsoft.VisualStudio.Shell.DialogPage> la classe implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager>, qui fournit la persistance pour les pages d’options et paramètres utilisateur. Les implémentations par défaut de la <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> et <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> méthodes rendre persistantes les modifications de propriété dans une section de l’utilisateur du Registre si la propriété peut être convertie vers et à partir d’une chaîne.  
  
## <a name="options-page-registry-path"></a>Chemin d’accès de Registre Options Page  
 Par défaut, le chemin d’accès de Registre des propriétés gérée par une page d’options est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, le mot DialogPage et le nom de type de la classe de page d’options. Par exemple, une classe de page d’options peut être définie comme suit.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Si le <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> est HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, puis les paires nom / valeur de propriété sont des sous-clés de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Le chemin d’accès de Registre de la page d’options lui-même est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, ToolsOptionsPages et les options page catégorie et le nom. Par exemple, si la page d’options personnalisées possède la catégorie, mon Option Pages et le <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> est HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la page d’options a la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Attributs de Page Outils/Options et la disposition  
 Le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut détermine le regroupement des pages d’options personnalisées en catégories dans l’arborescence de navigation de la **Options** boîte de dialogue. Le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut associe une page d’options VSPackage qui fournit l’interface. Prenons le fragment de code suivant :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Cela déclare que MyPackage fournit deux pages d’options, OptionsPageGeneral et OptionsPageCustom. Dans le **Options** boîte de dialogue, les deux pages d’options s’affichent dans le **mes Pages Option** catégorie comme **général** et **personnalisé**, respectivement.  
  
## <a name="option-attributes-and-layout"></a>Attributs d’option et disposition  
 L’interface utilisateur (IU) qui fournit la page détermine l’apparence des options dans une page d’options personnalisées. La mise en page, l’étiquetage et la description des options d’une page options générique sont déterminées par les attributs suivants :  
  
- <xref:System.ComponentModel.CategoryAttribute> Détermine la catégorie de l’option.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Détermine le nom complet de l’option.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Détermine la description de l’option.  
  
  > [!NOTE]
  >  Attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisez les ressources de type chaîne pour la localisation et sont définies dans le [exemple de projet managé](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Prenons le fragment de code suivant :  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  L’option OptionInteger s’affiche dans la page d’options en tant que **entier Option** dans le **mes Options** catégorie. Si l’option est sélectionnée, la description, **mon option entier**, apparaît dans la zone de description.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>L’accès aux Pages d’Options à partir d’un autre package Visual Studio  
 Un VSPackage qui héberge et gère une page d’options par programmation accessibles à partir d’un autre package Visual Studio à l’aide du modèle automation. Par exemple, dans le code suivant, un VSPackage est inscrit comme une page d’options d’hébergement.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Le fragment de code suivant obtient la valeur de OptionInteger à partir de MyOptionPage :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Lorsque le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut inscrit une page d’options, la page est enregistrée sous la clé de AutomationProperties si le `SupportsAutomation` argument de l’attribut est `true`. Automation examine cette entrée de Registre pour rechercher le VSPackage associé et l’automatisation, puis accède à la propriété via la page options hébergé, dans ce cas, ma Page de grille.  
  
 Le chemin d’accès de Registre de la propriété d’automation est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, AutomationProperties et les options page catégorie et le nom. Par exemple, si la page d’options possède la catégorie de ma catégorie, le nom de ma Page de grille et le <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la propriété d’automation a la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\ Page de grille Microsoft\VisualStudio\8.0Exp\AutomationProperties\My catégorie\Ma.  
  
> [!NOTE]
>  Le nom canonique, ma Page de grille Category.My, est la valeur de la sous-clé de nom de cette clé.
