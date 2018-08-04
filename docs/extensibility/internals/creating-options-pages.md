---
title: Création de Pages d’Options | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 834edb926142637a250cf4a695d5d1d54e103977
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499476"
---
# <a name="create-options-pages"></a>Créer des pages d’options
Dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] infrastructure de package gérée, les classes dérivées de <xref:Microsoft.VisualStudio.Shell.DialogPage> étendre le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE en ajoutant **Options** pages sous le **outils** menu.  
  
 Objet qui implémente une donnée **Option outils** page est associée à des VSPackages spécifiques par le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objet.  
  
 Étant donné que l’environnement instancie l’objet qui implémente un particulier **Outils/Options** page lorsque cette page est affichée par l’IDE :  
  
-   Un **Option outils** page doit être implémentée sur son propre objet et non sur l’objet qui implémente un VSPackage.  
  
-   Un objet ne peut pas implémenter plusieurs **Outils/Options** pages.  
  
## <a name="register-as-a-tools-options-page-provider"></a>Enregistrer en tant qu’un fournisseur de la page Outils/Options  
 Une configuration utilisateur prise en charge de VSPackage via **Outils/Options** pages indique les objets fournissant ces **Outils/Options** pages en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> appliquée à la <xref:Microsoft.VisualStudio.Shell.Package>implémentation.  
  
 Il doit y avoir une seule instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour chaque <xref:Microsoft.VisualStudio.Shell.DialogPage>-dérivés du type qui implémente un **Outils/Options** page.  
  
 Chaque instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilise le type qui implémente le **Outils/Options** page, les chaînes qui contiennent la catégorie et sous-catégorie utilisé pour identifier un **Outils/Options** page et des ressources informations pour inscrire le type comme fournissant un **Outils/Options** page.  
  
## <a name="persist-tools-options-page-state"></a>Conserver l’état de la page Outils/Options  
 Si un **Outils/Options** implémentation de la page est enregistrée avec prise en charge de l’automation est activée, l’IDE persiste l’état de la page, ainsi que tous les autres **Outils/Options** pages.  
  
 Un VSPackage peut gérer sa propre persistance à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Seulement un ou l’autre méthode de persistance doit être utilisé.  
  
## <a name="implement-dialogpage-class"></a>Implémenter une classe de DialogPage  
 Objet qui fournit l’implémentation d’un VSPackage d’un <xref:Microsoft.VisualStudio.Shell.DialogPage>-type dérivé peut tirer parti des fonctionnalités héritées suivantes :  
  
-   Une fenêtre d’interface utilisateur par défaut.  
  
-   Valeur par défaut un mécanisme de persistance disponible soit if <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> est appliqué à la classe, ou si le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propriété est définie sur `true` pour le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> qui est appliqué à la classe.  
  
-   Prise en charge d’Automation.  
  
 La configuration minimale requise pour un objet qui implémente un **Outils/Options** à l’aide de la page <xref:Microsoft.VisualStudio.Shell.DialogPage> est l’ajout de propriétés publiques.  
  
 Si la classe est correctement inscrite comme un **Outils/Options** page fournisseur, puis ses propriétés publiques sont disponibles sur le **Options** section de la **outils** menu sous la forme d’un grille des propriétés.  
  
 Toutes ces fonctionnalités par défaut peuvent être substituées. Par exemple, pour créer un utilisateur plus sophistiqué interface nécessite uniquement de remplacer l’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Exemple  
 Ce qui suit est une implémentation simple « Hello world » d’une page d’options. Ajouter le code suivant à un projet par défaut créé par le modèle de package Visual Studio avec le **commande de Menu** option sélectionnée va montrer correctement de fonctionnalité de page d’option.  
  
### <a name="description"></a>Description  
 La classe suivante définit une page d’options minimal « Hello world ». Lors de l’ouverture, l’utilisateur peut définir le public `HelloWorld` propriété dans une grille de propriétés.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Description  
 Appliquer l’attribut suivant à la classe de package rend les options de page disponible lorsque le package de charge. Les nombres sont arbitraire ID de ressources pour la catégorie et la page, et la valeur booléenne à la fin spécifie si la page prend en charge automation.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Description  
 Le Gestionnaire d’événements suivant affiche un résultat en fonction de la valeur de la propriété définie dans la page d’options. Il utilise le <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> méthode avec le résultat est explicitement converti dans le type de page d’option personnalisée pour accéder aux propriétés exposées par la page.  
  
 Dans le cas d’un projet généré par le modèle de package, appelez cette fonction à partir de la `MenuItemCallback` fonction à attacher à la commande par défaut ajoutée à la **outils** menu.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre les options et paramètres utilisateur](../../extensibility/extending-user-settings-and-options.md)   
 [Automation prend en charge pour les pages options](../../extensibility/internals/automation-support-for-options-pages.md)