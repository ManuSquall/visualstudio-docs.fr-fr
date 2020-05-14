---
title: Pages d’options et d’options Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706838"
---
# <a name="options-and-options-pages"></a>Options et pages Options
Cliquer sur **options** sur le menu **Tools** ouvre la boîte de dialogue **Options.** Les options dans cette boîte de dialogue sont collectivement appelées pages d’options. Le contrôle des arbres dans le volet de navigation comprend des catégories d’options, et chaque catégorie a des pages d’options. Lorsque vous sélectionnez une page, ses options apparaissent dans le bon volet. Ces pages vous permettent de modifier les valeurs des options qui déterminent l’état d’un VSPackage.

## <a name="support-for-options-pages"></a>Prise en charge des pages Options
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fournit un soutien pour la création de pages d’options et de catégories d’options. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implémente une page d’options.

 La mise <xref:Microsoft.VisualStudio.Shell.DialogPage> en œuvre par défaut des offres de ses propriétés publiques à un utilisateur dans une grille générique de propriétés. Vous pouvez personnaliser ce comportement en prépondant diverses méthodes sur la page pour créer une page d’options personnalisées qui a sa propre interface utilisateur (interface utilisateur). Pour plus d’informations, voir [Créer une page d’options](../../extensibility/creating-an-options-page.md).

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe <xref:Microsoft.VisualStudio.Shell.IProfileManager>implémente , ce qui fournit la persistance pour les pages d’options et aussi pour les paramètres de l’utilisateur. Les implémentations <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> par défaut de la propriété et les <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> méthodes persistent changements de propriété dans une section utilisateur du registre si la propriété peut être convertie à et à partir d’une chaîne.

## <a name="options-page-registry-path"></a>Options Page Registry Path
 Par défaut, la trajectoire de registre des propriétés <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>gérées par une page d’options est déterminée en combinant, le mot DialogPage, et le nom type de la classe de page d’options. Par exemple, un cours de page d’options peut être défini comme suit.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Si <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> le nom de propriété et les paires de valeur sont HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0Exp, alors les paires de noms et de valeurs de la propriété sont des sous-clés de HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0Exp-DialogPage-Company.OptionsPage.OptionsPageGeneral.

 Le parcours de registre de la <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>page d’options elle-même est déterminé en combinant, le mot, ToolsOptionsPages, et la catégorie de page d’options et le nom. Par exemple, si la page d’options personnalisées <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> a la catégorie, Mes pages d’option, et l’est HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp, alors la page d’options a la clé de registre, HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio -8.0Exp-ToolsOptionsPagesPages-My Options-Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Attributs et mise en page Outils/Options
 L’attribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> détermine le regroupement des pages d’options personnalisées en catégories dans l’arbre de navigation de la boîte de dialogue **Options.** L’attribut <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> associe une page d’options à l’emballage VS qui fournit l’interface. Prenons le fragment de code suivant :

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Cela déclare que MyPackage fournit deux pages d’options, OptionsPageGeneral et OptionsPageCustom. Dans la boîte de dialogue **Options,** les deux pages d’options apparaissent dans la catégorie **Pages Mes options** en tant que **générale** et **personnalisée,** respectivement.

## <a name="option-attributes-and-layout"></a>Attributs et mise en page d’options
 L’interface utilisateur (interface utilisateur) que la page fournit détermine l’apparence des options dans une page d’options personnalisées. La mise en page, l’étiquetage et la description des options dans une page d’options génériques sont déterminés par les attributs suivants :

- <xref:System.ComponentModel.CategoryAttribute>détermine la catégorie de l’option.

- <xref:System.ComponentModel.DisplayNameAttribute>détermine le nom d’affichage de l’option.

- <xref:System.ComponentModel.DescriptionAttribute>détermine la description de l’option.

  > [!NOTE]
  > Attributs équivalents, SRCategory, LocDisplayName et SRDescription, utilisent les ressources de chaîne pour la localisation et sont définis dans [l’échantillon de projet géré.](/azure/devops/integrate/index)

  Prenons le fragment de code suivant :

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  L’option OptionInteger apparaît sur la page d’options sous le titre **Integer Option** dans la catégorie **Mes options.** Si l’option est sélectionnée, la description, **Mon option d’intégration**, apparaît dans la boîte de description.

## <a name="accessing-options-pages-from-another-vspackage"></a>Accès aux pages Options d’un autre VSPackage
 Un VSPackage qui héberge et gère une page d’options peut être programmée à partir d’un autre VSPackage en utilisant le modèle d’automatisation. Par exemple, dans le code suivant, un VSPackage est enregistré comme hébergeant une page d’option.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Le fragment de code suivant obtient la valeur d’OptionInteger de MyOptionPage :

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> l’attribut enregistre une page d’options, la page est `SupportsAutomation` enregistrée sous `true`la clé AutomationProperties si l’argument de l’attribut est . Automation examine cette entrée de registre pour trouver le VSPackage associé, et l’automatisation accède ensuite à la propriété via la page d’options hébergée, dans ce cas, My Grid Page.

 Le chemin de registre de la <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>propriété d’automatisation est déterminé en combinant, le mot, AutomationProperties, et la catégorie de page d’options et le nom. Par exemple, si la page d’options a la catégorie <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>Ma catégorie, le nom My Grid Page, et le , HKEY_LOCAL_MACHINE-MICROSOFT-Microsoft-VisualStudio-8.0Exp, alors la propriété d’automatisation a la clé de registre, HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp-AutomationProperties-My Category-My Grid Page.

> [!NOTE]
> Le nom canonique, My Category.My Grid Page, est la valeur de la sous-clé nom de cette clé.
