---
title: "Options et Pages d’Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Options pages (Visual Studio SDK), managées package framework prise en charge des outils"
  - "infrastructure du package managé, la prise en charge des pages Outils/Options"
  - "prise en charge, les pages d’Options Outils"
  - "Pages d’Options (Visual Studio SDK), des dispositions des outils"
  - "Pages d’Options Outils (Visual Studio SDK), attributs"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Options et Pages d’Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En cliquant sur **Options** sur la **outils** menu ouvre le **Options** boîte de dialogue. Les options de cette boîte de dialogue sont collectivement appelées pages d’options. Le contrôle d’arborescence dans le volet de navigation inclut les catégories d’options, et chaque catégorie comporte des pages d’options. Lorsque vous sélectionnez une page, ses options apparaissent dans le volet droit. Ces pages vous permettent de modifier les valeurs des options qui déterminent l’état d’un VSPackage.  
  
## Prise en charge des Pages d’Options  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe prend en charge la création de pages d’options et les catégories d’options. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implémente une page options.  
  
 L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> propose ses propriétés publiques à un utilisateur dans une grille de propriétés générique. Vous pouvez personnaliser ce comportement en substituant les méthodes sur la page pour créer une page options personnalisée qui possède sa propre interface utilisateur \(IU\). Pour plus d'informations, consultez [Création d’une Page d’Options](../../extensibility/creating-an-options-page.md).  
  
 La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager>, qui fournit la persistance pour les pages d’options et paramètres utilisateur. Les implémentations par défaut de la <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> et <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> méthodes rendre persistantes les modifications de propriété dans une section du Registre de l’utilisateur si la propriété peut être convertie vers et à partir d’une chaîne.  
  
## Chemin d’accès du Registre Options Page  
 Par défaut, le chemin d’accès de Registre des propriétés gérées par une page d’options est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, le mot DialogPage et le nom de type de la classe de la page options. Par exemple, une classe de page d’options peut être définie comme suit.  
  
 [!CODE [VSSDKSupportForOptionsPages#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#1)]  
  
 Si la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> est HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, les paires nom \/ valeur de propriété sont des sous\-clés de HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral.  
  
 Le chemin d’accès de Registre de la page options lui\-même est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, ToolsOptionsPages et les options de la page catégorie et le nom. Par exemple, si la page d’options personnalisées possède la catégorie, mon Option Pages et le <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> est HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, la page d’options a la clé de Registre HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My Option Pages\\Custom.  
  
## Attributs de Page Outils\/Options et la disposition  
 Le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut détermine le regroupement des pages d’options personnalisées en catégories dans l’arborescence de navigation de la **Options** boîte de dialogue. Le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associe une page options VSPackage qui fournit l’interface. Prenons le fragment de code suivant :  
  
 [!CODE [VSSDKSupportForOptionsPages#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#2)]  
  
 Cette instruction déclare que MyPackage fournit deux pages d’options, OptionsPageGeneral et OptionsPageCustom. Dans le **Options** boîte de dialogue, les deux pages d’options s’affichent dans le **Mes Pages Option** catégorie **Général** et **personnalisé**, respectivement.  
  
## Attributs d’option et la disposition  
 L’interface utilisateur \(IU\) qui fournit la page détermine l’apparence des options dans une page d’options personnalisées. La mise en page, étiquetage et description des options dans une page d’options génériques sont déterminés par les attributs suivants :  
  
-   <xref:System.ComponentModel.CategoryAttribute> Détermine la catégorie de l’option.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Détermine le nom complet de l’option.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Détermine la description de l’option.  
  
    > [!NOTE]
    >  Attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisez les ressources de chaîne pour la localisation et sont définies dans le [exemple de projet managé](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Prenons le fragment de code suivant :  
  
 [!CODE [VSSDKSupportForOptionsPages#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#3)]  
  
 L’option OptionInteger s’affiche sur la page d’options en tant que **entier Option** dans les **Mes Options de** catégorie. Si l’option est sélectionnée, la description, **mon option entier**, apparaît dans la zone description.  
  
## L’accès aux Pages d’Options à partir d’un autre package VS  
 Un VSPackage qui héberge et gère une page options accessible par programmation à partir d’un autre package VS à l’aide du modèle automation. Par exemple, dans le code suivant un VSPackage est enregistré comme une page d’options d’hébergement.  
  
 [!CODE [VSSDKSupportForOptionsPages#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#4)]  
  
 Le fragment de code suivant obtient la valeur de OptionInteger de MyOptionPage :  
  
 [!CODE [VSSDKSupportForOptionsPages#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#5)]  
  
 Lorsque le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attribut enregistre une page options, la page est enregistrée sous la touche AutomationProperties, si le `SupportsAutomation` l’argument de l’attribut est `true`. Automation examine cette entrée de Registre pour rechercher le VSPackage associé et l’automatisation, puis accède à la propriété via la page d’options hébergé, dans ce cas, ma Page de grille.  
  
 Le chemin d’accès de Registre de la propriété automation est déterminée en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, AutomationProperties et les options de la page catégorie et le nom. Par exemple, si la page d’options a la catégorie Mes, le nom de ma Page de grille et la <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, la propriété automation a la clé de Registre, Page de grille HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My catégorie\\Ma.  
  
> [!NOTE]
>  Le nom canonique, ma Page de grille Category.My, est la valeur de la sous\-clé du nom de cette clé.