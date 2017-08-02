---
title: "Étendre les propriétés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>Étendre les propriétés
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propriétés** fenêtre est une fenêtre de propriétés universel pour les composants COM et COM + et prend en charge tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produits. Le **propriétés** fenêtre fonctionne avec `ITypeInfo` informations de type et des métadonnées COM + pour répertorier les propriétés au moment du design pour l’objet actuellement sélectionné dans les autres fenêtres de l’environnement de développement intégré (IDE).  
  
 Le **propriétés** fenêtre, qui peut être ouvert en appuyant sur F4 du clavier, ou en sélectionnant **fenêtre Propriétés** sur la **affichage** menu, est utilisé pour afficher et modifier les propriétés liées à la configuration, au moment du design et les événements des objets sélectionnés. Propriétés dépendantes de la configuration, des solutions et des projets, sont affichent sur [Pages de propriétés](../../extensibility/internals/property-pages.md). Pour plus d’informations, consultez [NIB : projet propriétés](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md), et [NIB : Item Management in Projects](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Présentation de la fenêtre Propriétés](~/docs/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Fenêtre Propriétés  
  
 Cette section fournit des informations détaillées relatives aux zones individuelles de la **propriétés** fenêtre et les interfaces que vous devez implémenter et appel à remplir la fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation de la fenêtre Propriétés](../../extensibility/internals/properties-window-overview.md)  
 Explique l’objectif de la **propriétés** fenêtre par rapport à la fenêtre d’outils et la fenêtre de document.  
  
 [Stratégie de modèle et de la fenêtre Propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Explique comment un projet est contenu dans un projet de modèle d’entreprise, et comment ce projet de modèle d’entreprise peut appliquer la stratégie.  
  
 [Interfaces et les champs de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explique les critères de sélection qui détermine quelles informations sont affichées dans le **propriétés** fenêtre.  
  
 [Objet liste de la fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md)  
 Décrit l’objectif de la **propriétés** liste d’objets de fenêtre, décrivant comment, lorsqu’un autre objet dans la liste déclenche un appel, l’environnement est informé qu’un objet a été sélectionné.  
  
 [Boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md)  
 Explique l’objectif des boutons quatre par défaut affichés sur le **propriétés** barre d’outils.  
  
 [Afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md)  
 Explique où figurent les noms de propriété et les champs de valeurs de propriété dans la grille.  
  
 [Annonce du suivi de sélection de la fenêtre Propriétés](../../misc/announcing-property-window-selection-tracking.md)  
 Décrit la sélection de suivi pour le **propriétés** fenêtre.  
  
 [Masquage des propriétés qui ont des propriétés enfants](../../misc/hiding-properties-that-have-child-properties.md)  
 Explique comment masquer des propriétés qui ont des propriétés enfants en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [Fourniture d’une fenêtre de propriétés personnalisée](../../misc/providing-a-custom-properties-window.md)  
 Décrit les étapes pour fournir votre propre Explorateur de propriétés.  
  
 [Obtention de descriptions de champs à partir de la fenêtre Propriétés](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explique où trouver la zone de description qui affiche des informations relatives au champ de propriété sélectionnée.  
  
 [Mise à jour des valeurs de propriété dans la fenêtre Propriétés](../../misc/updating-property-values-in-the-properties-window.md)  
 Fournit des instructions pas à pas qui montrent les deux façons de conserver le **propriétés** fenêtre synchronisé avec les modifications de valeur de propriété.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Présente les projets en tant que blocs de construction de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)  
 Décrit comment vous pouvez utiliser la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plate-forme de test et débogage d’applications que vous devez les créer en continu.  
  
 [Propriétés des documents HTML, fenêtre Propriétés](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Fournit des instructions pour la modification d’un document HTML directement à partir de la fenêtre Propriétés et fournit un tableau détaillant les champs dans un document HTML dans la fenêtre Propriétés.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Décrit le `IDispatch` interface, ce qui a été tout d’abord conçu pour prendre en charge automation, fournissant un mécanisme à liaison tardive pour accéder à et récupérer des informations sur les méthodes et propriétés d’un objet.  
  
 [NIB : Présentation des propriétés dynamiques (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fournit une vue d’ensemble de propriétés dynamiques qui vous permettent de configurer votre application afin que les valeurs de propriété sont stockées dans un fichier de configuration externe au lieu du code compilé de l’application.  
  
 [NIB : projets comme conteneurs](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Décrit le rôle du projet en tant que conteneur dans une solution pour gérer logiquement, générer et déboguer les éléments qui composent votre application.  
  
 [NIB : projet propriétés](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Décrit comment le projet gère les paramètres qui vous permettent de propriétés de contrôle qui s’appliquent à la totalité du projet ainsi que les propriétés qui sont limitées à certaines configurations de build du projet.  
  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explique comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère efficacement les éléments tels que les références, connexions de données, dossiers et fichiers requis par votre travail de développement via des solutions et projets.  
  
 [Extension des autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] services pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
