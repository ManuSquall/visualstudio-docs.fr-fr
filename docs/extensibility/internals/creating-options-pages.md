---
title: "Création de Pages d’Options | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ae8540a2f372abacd8eda6e63cd868edbb050392
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-options-pages"></a>Création de Pages d’Options
Dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] infrastructure de package gérée, les classes dérivées de <xref:Microsoft.VisualStudio.Shell.DialogPage> étendre le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE en ajoutant **Options** pages sous le **outils** menu.  
  
 Objet qui implémente une donnée **Option outils** page est associée à des VSPackages spécifiques par le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objet.  
  
 Étant donné que l’environnement instancie l’objet qui implémente un particulier **Outils Options** page lorsque cette page est affichée par l’IDE :  
  
-   A **Option outils** page doit être implémentée sur son propre objet et non sur l’objet qui implémente un VSPackage.  
  
-   Un objet ne peut pas implémenter plusieurs **Outils Options** pages.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>L’inscription d’un fournisseur de Page d’Options Outils  
 Une VSPackage prise en charge configuration de l’utilisateur via **Outils Options** pages indique les objets qui fournit ces **Outils Options** pages en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> appliquée à la <xref:Microsoft.VisualStudio.Shell.Package>mise en œuvre.  
  
 Il doit y avoir une seule instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour chaque <xref:Microsoft.VisualStudio.Shell.DialogPage>-dérivées du type qui implémente un **Outils Options** page.  
  
 Chaque instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilise le type qui implémente le **Outils Options** page, les chaînes qui contiennent la catégorie et sous-catégorie utilisé pour identifier un **Outils Options** page et des ressources informations pour enregistrer le type comme fournissant un **Outils Options** page.  
  
## <a name="persisting-tools-options-page-state"></a>Outils de rendre persistant l’état Page Options  
 Si un **Outils Options** mise en œuvre de la page est enregistré avec prise en charge automation activé, l’IDE état de la page persistant, ainsi que tous les autres **Outils Options** pages.  
  
 Un VSPackage peut gérer sa propre persistance à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Qu’une ou l’autre méthode de persistance doit être utilisé.  
  
## <a name="implementing-dialogpage-class"></a>Classe d’implémentation DialogPage  
 Objet qui fournit l’implémentation d’un VSPackage d’un <xref:Microsoft.VisualStudio.Shell.DialogPage>-type dérivé peut tirer parti des fonctionnalités héritées suivantes :  
  
-   Une fenêtre d’interface utilisateur par défaut.  
  
-   A par défaut mécanisme de persistance disponible soit if <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> est appliqué à la classe, ou si le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> est définie sur `true` pour la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> qui est appliqué à la classe.  
  
-   Prise en charge d’Automation.  
  
 La configuration minimale requise pour un objet qui implémente un **Outils Options** à l’aide de la page <xref:Microsoft.VisualStudio.Shell.DialogPage> est l’ajout de propriétés publiques.  
  
 Si la classe est correctement enregistré en tant qu’un **Outils Options** page fournisseur, puis ses propriétés publiques sont disponibles sur le **Options** section de la **outils** menu sous la forme d’un grille des propriétés.  
  
 Toutes ces fonctionnalités par défaut peuvent être remplacées. Par exemple, pour créer un utilisateur plus sophistiqué interface requiert uniquement substituer l’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Exemple  
 Ce qui suit est une implémentation « hello world » simple d’une page d’options. Ajouter le code suivant à un projet par défaut créé par le modèle de Package Visual Studio avec le **commande de Menu** option sélectionnée va vous montrer correctement fonctionnalité de page d’option.  
  
### <a name="description"></a>Description  
 La classe suivante définit une page d’options minimal « hello world ». Lors de l’ouverture, l’utilisateur peut définir le public `HelloWorld` propriété dans une grille des propriétés.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Description  
 Appliquer l’attribut suivant à la classe de package propose les options de page lors du chargement du package. Les nombres sont arbitraire ID de ressource de la catégorie et la page, et la valeur booléenne à la fin spécifie si la page prend en charge automation.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Description  
 Le Gestionnaire d’événements suivant affiche un résultat en fonction de la valeur de la propriété définie dans la page d’options. Elle utilise le <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> méthode avec le résultat est explicitement converti dans le type de page option personnalisée pour accéder aux propriétés exposées par la page.  
  
 Dans le cas d’un projet généré par le modèle de package, appelez cette fonction à partir de la `MenuItemCallback` fonction à attacher à la commande par défaut ajoutée à la **outils** menu.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options et paramètres d’extension utilisateur](../../extensibility/extending-user-settings-and-options.md)   
 [Prise en charge de l’automatisation pour les pages Options](../../extensibility/internals/automation-support-for-options-pages.md)