---
title: Création de Pages d’Options | Microsoft Docs
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
ms.openlocfilehash: 319d889d2763662cda92d815ce45a3becfcab8cf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938611"
---
# <a name="creating-options-pages"></a>Création de pages Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] infrastructure de package gérée, les classes dérivées de <xref:Microsoft.VisualStudio.Shell.DialogPage> étendre le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE en ajoutant **Options** pages sous le **outils** menu.  
  
 Objet qui implémente une donnée **Option outils** page est associée à des VSPackages spécifiques par le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objet.  
  
 Étant donné que l’environnement instancie l’objet qui implémente un particulier **Outils/Options** page lorsque cette page est affichée par l’IDE :  
  
-   Un **Option outils** page doit être implémentée sur son propre objet et non sur l’objet qui implémente un VSPackage.  
  
-   Un objet ne peut pas implémenter plusieurs **Outils/Options** pages.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>L’inscription d’un fournisseur de Page d’Options Outils  
 Une configuration utilisateur prise en charge de VSPackage via **Outils/Options** pages indique les objets fournissant ces **Outils/Options** pages en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> appliquée à la <xref:Microsoft.VisualStudio.Shell.Package>implémentation.  
  
 Il doit y avoir une seule instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour chaque <xref:Microsoft.VisualStudio.Shell.DialogPage>-dérivés du type qui implémente un **Outils/Options** page.  
  
 Chaque instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilise le type qui implémente le **Outils/Options** page, les chaînes qui contiennent la catégorie et sous-catégorie utilisé pour identifier un **Outils/Options** page et des ressources informations pour inscrire le type comme fournissant un **Outils/Options** page.  
  
## <a name="persisting-tools-options-page-state"></a>État persistant de la Page d’outils Options  
 Si un **Outils/Options** implémentation de la page est enregistrée avec prise en charge de l’automation est activée, l’IDE persiste l’état de la page, ainsi que tous les autres **Outils/Options** pages.  
  
 Un VSPackage peut gérer sa propre persistance à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Seulement un ou l’autre méthode de persistance doit être utilisé.  
  
## <a name="implementing-dialogpage-class"></a>Classe d’implémentation DialogPage  
 Objet qui fournit l’implémentation d’un VSPackage d’un <xref:Microsoft.VisualStudio.Shell.DialogPage>-type dérivé peut tirer parti des fonctionnalités héritées suivantes :  
  
- Une fenêtre d’interface utilisateur par défaut.  
  
- Valeur par défaut un mécanisme de persistance disponible soit if <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> est appliqué à la classe, ou si le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propriété est définie sur `true` pour le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> qui est appliqué à la classe.  
  
- Prise en charge d’Automation.  
  
  La configuration minimale requise pour un objet qui implémente un **Outils/Options** à l’aide de la page <xref:Microsoft.VisualStudio.Shell.DialogPage> est l’ajout de propriétés publiques.  
  
  Si la classe est correctement inscrite comme un **Outils/Options** page fournisseur, puis ses propriétés publiques sont disponibles sur le **Options** section de la **outils** menu sous la forme d’un grille des propriétés.  
  
  Toutes ces fonctionnalités par défaut peuvent être substituées. Par exemple, pour créer un utilisateur plus sophistiqué interface nécessite uniquement de remplacer l’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Exemple  
 Ce qui suit est une implémentation simple « hello world » d’une page d’options. Ajouter le code suivant à un projet par défaut créé par le modèle de Package Visual Studio avec le **commande de Menu** option sélectionnée va montrer correctement de fonctionnalité de page d’option.  
  
### <a name="description"></a>Description  
 La classe suivante définit une page d’options minimal « hello world ». Lors de l’ouverture, l’utilisateur peut définir le public `HelloWorld` propriété dans une grille de propriétés.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Description  
 Appliquer l’attribut suivant à la classe de package rend les options de page disponible lorsque le package de charge. Les nombres sont arbitraire ID de ressources pour la catégorie et la page, et la valeur booléenne à la fin spécifie si la page prend en charge automation.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Description  
 Le Gestionnaire d’événements suivant affiche un résultat en fonction de la valeur de la propriété définie dans la page d’options. Il utilise le <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> méthode avec le résultat est explicitement converti dans le type de page d’option personnalisée pour accéder aux propriétés exposées par la page.  
  
 Dans le cas d’un projet généré par le modèle de package, appelez cette fonction à partir de la `MenuItemCallback` fonction à attacher à la commande par défaut ajoutée à la **outils** menu.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options et paramètres d’extension utilisateur](../../extensibility/extending-user-settings-and-options.md)   
 [Prise en charge de l’automatisation pour les pages Options](../../extensibility/internals/automation-support-for-options-pages.md)
