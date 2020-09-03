---
title: Création de pages d’options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196948"
---
# <a name="creating-options-pages"></a>Création de pages Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] infrastructure de package managée, les classes dérivées de <xref:Microsoft.VisualStudio.Shell.DialogPage> étendent l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE en ajoutant des pages d' **options** dans le menu **Outils** .  
  
 Un objet qui implémente une page d' **options Outils** donnée est associé à des VSPackages spécifiques par l' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objet.  
  
 Étant donné que l’environnement instancie l’objet qui implémente une page d' **options Outils** particulière lorsque cette page spécifique est affichée par l’IDE :  
  
- Une page d' **options Outils** doit être implémentée sur son propre objet, et non sur l’objet qui implémente un VSPackage.  
  
- Un objet ne peut pas implémenter plusieurs pages d' **options d’outils** .  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Inscription en tant que fournisseur de la page Options des outils  
 Un VSPackage qui prend en charge la configuration de l’utilisateur via les pages d' **options Outils** indique les objets qui fournissent ces pages d' **options d’outils** en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> appliquées à l' <xref:Microsoft.VisualStudio.Shell.Package> implémentation.  
  
 Il doit y avoir une instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour chaque <xref:Microsoft.VisualStudio.Shell.DialogPage> type dérivé de qui implémente une page **Outils Options** .  
  
 Chaque instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilise le type qui implémente la page **Options des outils** , des chaînes qui contiennent la catégorie et la sous-catégorie utilisées pour identifier une page d' **options Outils** , ainsi que des informations sur les ressources pour inscrire le type comme fournissant une page **Outils Options** .  
  
## <a name="persisting-tools-options-page-state"></a>État de la page Options des outils persistants  
 Si une implémentation de page **Options des outils** est inscrite avec la prise en charge d’Automation activée, l’IDE conserve l’état de la page avec toutes les autres pages **Options des outils** .  
  
 Un VSPackage peut gérer sa propre persistance à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Une seule et unique méthode de persistance doit être utilisée.  
  
## <a name="implementing-dialogpage-class"></a>Implémentation de la classe DialogPage  
 Un objet qui fournit l’implémentation d’un VSPackage d’un <xref:Microsoft.VisualStudio.Shell.DialogPage> type dérivé de VSPackage peut tirer parti des fonctionnalités héritées suivantes :  
  
- Fenêtre d’interface utilisateur par défaut.  
  
- Mécanisme de persistance par défaut disponible si <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> est appliqué à la classe, ou si la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propriété a la valeur `true` pour le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> qui est appliqué à la classe.  
  
- Prise en charge d’Automation.  
  
  La configuration minimale requise pour un objet qui implémente une page **Outils Options** à l’aide <xref:Microsoft.VisualStudio.Shell.DialogPage> de est l’ajout de propriétés publiques.  
  
  Si la classe est correctement inscrite en tant que fournisseur de la page **Options des outils** , ses propriétés publiques sont disponibles dans la section **options** du menu **Outils** sous la forme d’une grille de propriétés.  
  
  Toutes ces fonctionnalités par défaut peuvent être remplacées. Par exemple, pour créer une interface utilisateur plus sophistiquée, vous devez uniquement substituer l’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .  
  
## <a name="example"></a>Exemple  
 Ce qui suit est une implémentation « Hello World » simple d’une page d’options. L’ajout du code suivant à un projet par défaut créé par le modèle de package Visual Studio avec l’option de **commande de menu** sélectionnée vous montrera correctement les fonctionnalités de page d’options.  
  
### <a name="description"></a>Description  
 La classe suivante définit une page d’options minimale « Hello World ». Lorsqu’il est ouvert, l’utilisateur peut définir la `HelloWorld` propriété publique dans une grille des propriétés.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Description  
 L’application de l’attribut suivant à la classe de package rend la page Options disponible lors du chargement du package. Les nombres sont des ID de ressource arbitraires pour la catégorie et la page, et la valeur booléenne à la fin spécifie si la page prend en charge l’Automation.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Description  
 Le gestionnaire d’événements suivant affiche un résultat en fonction de la valeur de la propriété définie dans la page Options. Elle utilise la <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> méthode avec le résultat explicitement converti en type de page d’options personnalisé pour accéder aux propriétés exposées par la page.  
  
 Dans le cas d’un projet généré par le modèle de package, appelez cette fonction à partir de la `MenuItemCallback` fonction pour l’attacher à la commande par défaut ajoutée au menu **Outils** .  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des paramètres et des options utilisateur](../../extensibility/extending-user-settings-and-options.md)   
 [Prise en charge de l’automatisation pour les pages Options](../../extensibility/internals/automation-support-for-options-pages.md)
