---
title: Options et pages Options | Microsoft Docs
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
ms.openlocfilehash: 1e30be26c40834d3122d491f8d150f02b6f3b776
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300698"
---
# <a name="options-and-options-pages"></a>Options et pages Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cliquez sur **options** dans le menu **Outils** pour ouvrir la boîte de dialogue **options** . Les options de cette boîte de dialogue sont collectivement appelées pages d’options. Le contrôle d’arborescence dans le volet de navigation inclut des catégories d’options, et chaque catégorie possède des pages d’options. Lorsque vous sélectionnez une page, ses options s’affichent dans le volet droit. Ces pages vous permettent de modifier les valeurs des options qui déterminent l’état d’un VSPackage.  
  
## <a name="support-for-options-pages"></a>Prise en charge des pages d’options  
 La classe <xref:Microsoft.VisualStudio.Shell.Package> fournit la prise en charge de la création de pages d’options et de catégories d’options. La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implémente une page d’options.  
  
 L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> offre ses propriétés publiques à un utilisateur dans une grille générique de propriétés. Vous pouvez personnaliser ce comportement en remplaçant différentes méthodes sur la page pour créer une page d’options personnalisée qui possède sa propre interface utilisateur. Pour plus d’informations, consultez [création d’une page d’options](../../extensibility/creating-an-options-page.md).  
  
 La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager>, qui fournit la persistance pour les pages Options et également pour les paramètres utilisateur. Les implémentations par défaut des méthodes <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> et <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> persistent les modifications de propriété dans une section utilisateur du Registre si la propriété peut être convertie vers et à partir d’une chaîne.  
  
## <a name="options-page-registry-path"></a>Page d’options chemin du Registre  
 Par défaut, le chemin d’accès au registre des propriétés gérées par une page Options est déterminé en combinant <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, le mot DialogPage et le nom de type de la classe de la page Options. Par exemple, une classe de page Options peut être définie comme suit.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Si le <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> est HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, les paires nom de la propriété et valeur sont des sous-clés de HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.  
  
 Le chemin d’accès au registre de la page Options elle-même est déterminé en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, ToolsOptionsPages et la catégorie et le nom de la page Options. Par exemple, si la page Options personnalisées contient la catégorie, mes pages d’options et que la <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> est HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, la page Options contient la clé de Registre HKEY_LOCAL_MACHINE option \SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Mise en page et attributs des pages outils/options  
 L’attribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> détermine le regroupement des pages d’options personnalisées en catégories dans l’arborescence de navigation de la boîte de dialogue **options** . L’attribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associe une page d’options au VSPackage qui fournit l’interface. Prenons le fragment de code suivant :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Cela déclare que MyPackage fournit deux pages d’options, OptionsPageGeneral et OptionsPageCustom. Dans la boîte de dialogue **options** , les deux pages options s’affichent dans la catégorie **mes pages** d’options comme **général** et **personnalisé**, respectivement.  
  
## <a name="option-attributes-and-layout"></a>Attributs et disposition des options  
 L’interface utilisateur (IU) fournie par la page détermine l’apparence des options dans une page d’options personnalisée. La disposition, l’étiquetage et la description des options d’une page d’options générique sont déterminés par les attributs suivants :  
  
- <xref:System.ComponentModel.CategoryAttribute> détermine la catégorie de l’option.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> détermine le nom complet de l’option.  
  
- <xref:System.ComponentModel.DescriptionAttribute> détermine la description de l’option.  
  
  > [!NOTE]
  > Les attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisent des ressources de type chaîne pour la localisation et sont définis dans l' [exemple de projet managé](https://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Prenons le fragment de code suivant :  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  L’option OptionInteger s’affiche sur la page options sous forme d' **entier** dans la catégorie **mes options** . Si l’option est sélectionnée, l’option Description, **mon entier**, s’affiche dans la zone Description.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Accès aux pages d’options à partir d’un autre VSPackage  
 Un VSPackage qui héberge et gère une page d’options peut être accessible par programmation à partir d’un autre VSPackage à l’aide du modèle Automation. Par exemple, dans le code suivant, un VSPackage est inscrit comme hébergeant une page d’options.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Le fragment de code suivant obtient la valeur de OptionInteger à partir de MyOptionPage :  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Lorsque l’attribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> inscrit une page d’options, la page est inscrite sous la clé AutomationProperties si l’argument `SupportsAutomation` de l’attribut est `true`. Automation examine cette entrée du Registre pour trouver le VSPackage associé et l’automatisation accède ensuite à la propriété via la page Options hébergées, dans le cas présent, ma page de grille.  
  
 Le chemin d’accès au registre de la propriété Automation est déterminé en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, AutomationProperties et la catégorie et le nom de la page Options. Par exemple, si la page Options contient la catégorie ma catégorie, le nom de la page mon grille et le <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, alors la propriété Automation a la clé de Registre, HKEY_LOCAL_MACHINE page de grille Category\My \SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
> Le nom canonique, ma page de grille Category.My, est la valeur de la sous-clé Name de cette clé.
