---
title: "Création de Pages d’Options | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>Création de Pages d’Options
Dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] infrastructure du package managé, les classes dérivées de <xref:Microsoft.VisualStudio.Shell.DialogPage>étendre la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE en ajoutant **Options** pages sous le **outils** menu.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Objet qui implémente une donnée **Option outils** page est associée à des VSPackages spécifiques par le <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>objet.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Étant donné que l’environnement instancie l’objet qui implémente un particulier **Outils/Options** page lorsque cette page est affichée par l’IDE :  
  
-   A **Option outils** page doit être implémentée sur son propre objet et non sur l’objet qui implémente un VSPackage.  
  
-   Un objet ne peut pas implémenter plusieurs **Outils/Options** pages.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>L’inscription d’un fournisseur de Page d’Options Outils  
 Une configuration utilisateur VSPackage la prise en charge via **Outils/Options** pages indique les objets qui fournit ces **Outils/Options** pages en appliquant des instances de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>appliquée à la <xref:Microsoft.VisualStudio.Shell.Package>implémentation.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Il doit y avoir une seule instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>pour chaque <xref:Microsoft.VisualStudio.Shell.DialogPage>-dérivées du type qui implémente un **Outils/Options** page.</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Chaque instance de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>utilise le type qui implémente le **Outils/Options** page, les chaînes qui contiennent la catégorie et sous-catégorie permettent d’identifier une **Outils/Options** page et pour enregistrer le type en fournissant des informations sur les ressources un **Outils/Options** page.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
## <a name="persisting-tools-options-page-state"></a>Outils de rendre persistant l’état Page Options  
 Si un **Outils/Options** mise en œuvre de la page est enregistré avec automation activé, l’interface IDE conserve l’état de la page, ainsi que tous les autres **Outils/Options** pages.  
  
 Un VSPackage peut gérer sa propre persistance à l’aide de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Seulement un ou l’autre méthode de persistance doit être utilisé.  
  
## <a name="implementing-dialogpage-class"></a>L’implémentation de classe de DialogPage  
 Objet qui fournit l’implémentation d’un VSPackage d’un <xref:Microsoft.VisualStudio.Shell.DialogPage>-type dérivé peut tirer parti des fonctionnalités héritées suivantes :</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   Une fenêtre d’interface utilisateur par défaut.  
  
-   A par défaut mécanisme de persistance disponible soit if <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>est appliqué à la classe, ou si la <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>est définie sur `true` pour <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>qui est appliqué à la classe.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   Prise en charge Automation.  
  
 La configuration minimale requise pour un objet qui implémente un **Outils/Options** à l’aide de la page <xref:Microsoft.VisualStudio.Shell.DialogPage>est l’ajout de propriétés publiques.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Si la classe est correctement enregistré comme un **Outils/Options** page fournisseur, puis ses propriétés publiques sont disponibles sur le **Options** section de la **outils** menu sous la forme d’une grille des propriétés.  
  
 Toutes ces fonctionnalités par défaut peuvent être substituées. Par exemple, pour créer une plus sophistiquées interface utilisateur nécessite seulement substituer l’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>  
  
## <a name="example"></a>Exemple  
 Ce qui suit est une implémentation simple « hello world » d’une page d’options. Ajouter le code suivant au projet par défaut créé par le modèle de Package Visual Studio avec le **des commandes de Menu** option sélectionnée va vous montrer correctement une page une fonctionnalité option.  
  
### <a name="description"></a>Description  
 La classe suivante définit une page d’options minimal « hello world ». Lors de l’ouverture, l’utilisateur peut définir le public `HelloWorld` propriété dans une grille de propriétés.  
  
### <a name="code"></a>Code  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Description  
 Appliquez l’attribut suivant à la classe de package propose les options de page lors du chargement du package. Les nombres sont arbitraire ID de ressource de la catégorie et la page, et la valeur booléenne à la fin spécifie si la page prend en charge automation.  
  
### <a name="code"></a>Code  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Description  
 Le Gestionnaire d’événements suivant affiche un résultat en fonction de la valeur de la propriété définie dans la page options. Il utilise le <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>méthode avec le résultat explicitement converties dans le type de page option personnalisée pour accéder aux propriétés exposées par la page.</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>  
  
 Dans le cas d’un projet généré par le modèle de package, appelez cette fonction à partir de la `MenuItemCallback` fonction à attacher à la commande par défaut ajoutée à la **outils** menu.  
  
### <a name="code"></a>Code  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options et paramètres d’extension utilisateur](../../extensibility/extending-user-settings-and-options.md)   
 [Prise en charge d’Automation pour les Pages d’Options](../../extensibility/internals/automation-support-for-options-pages.md)
