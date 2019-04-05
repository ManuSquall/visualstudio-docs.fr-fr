---
title: Étendre les propriétés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59afc6a95e327460602ece8db58f075b483d0e09
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950256"
---
# <a name="extending-properties"></a>Extension des propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **propriétés** fenêtre est un navigateur de propriété universelle pour les composants COM et COM + et prend en charge tous les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produits. Le **propriétés** fenêtre fonctionne avec `ITypeInfo` informations de type et des métadonnées COM + pour répertorier les propriétés au moment du design pour l’objet actuellement sélectionné dans une autre fenêtre dans l’environnement de développement intégré (IDE).  
  
 Le **propriétés** fenêtre, ce qui peut être ouvert en appuyant sur F4 du clavier, ou en sélectionnant **fenêtre Propriétés** sur le **vue** menu, est utilisé pour afficher et modifier propriétés indépendantes de la configuration, au moment du design et les événements des objets sélectionnés. Propriétés dépendantes de la configuration, associées aux solutions et projets, s’affichent sur [Pages de propriétés](../../extensibility/internals/property-pages.md). Pour plus d’informations, consultez [NIB : projet propriétés](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md), et [NIB : gestion des éléments dans les projets](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Vue d’ensemble de la fenêtre Propriétés](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Fenêtre Propriétés  
  
 Cette section fournit des informations détaillées relatives aux zones individuelles de la **propriétés** fenêtre et les interfaces que vous devez implémenter et appel à remplir la fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation de la fenêtre Propriétés](../../extensibility/internals/properties-window-overview.md)  
 Explique l’objectif de la **propriétés** fenêtre par rapport à la fenêtre outil et la fenêtre de document.  
  
 [Stratégie de modèle et fenêtre Propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Explique comment un projet est contenu dans un projet de modèle d’entreprise, et comment ce projet de modèle d’entreprise peut appliquer la stratégie.  
  
 [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explique les critères de sélection qui détermine quelles informations sont affichées dans le **propriétés** fenêtre.  
  
 [Liste d’objets de la fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md)  
 Décrit l’objectif de la **propriétés** liste d’objets de fenêtre, décrivant comment, quand un autre objet à partir de cette liste déclenche un appel, l’environnement est informé qu’un nouvel objet a été sélectionné.  
  
 [Boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md)  
 Explique l’objectif des boutons quatre par défaut affichées sur le **propriétés** barre d’outils de la fenêtre.  
  
 [Afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md)  
 Explique où figurent les noms de propriété et les champs de valeurs de propriété dans la grille.  
  
 [Annonce du suivi de sélection de la fenêtre Propriétés](../../misc/announcing-property-window-selection-tracking.md)  
 Décrit la sélection de suivi pour le **propriétés** fenêtre.  
  
 [Masquage des propriétés qui ont des propriétés enfants](../../misc/hiding-properties-that-have-child-properties.md)  
 Explique comment masquer les propriétés qui ont des propriétés enfants en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interface.  
  
 [Fourniture d’une fenêtre de propriétés personnalisée](../../misc/providing-a-custom-properties-window.md)  
 Décrit en détail les étapes pour fournir votre propre Explorateur de propriétés.  
  
 [Obtention de descriptions de champs à partir de la fenêtre Propriétés](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explique où trouver la zone de description qui affiche des informations relatives au champ de propriété sélectionnée.  
  
 [Mise à jour des valeurs de propriété dans la fenêtre Propriétés](../../misc/updating-property-values-in-the-properties-window.md)  
 Fournit des instructions pas à pas qui indiquent les deux façons de conserver le **propriétés** fenêtre synchronisé avec les modifications de valeur de propriété.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Traite des projets en tant que blocs de construction de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)  
 Décrit comment vous pouvez utiliser le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Platform pour tester et déboguer des applications que vous devez les créer en permanence.  
  
 [Propriétés des documents HTML, fenêtre Propriétés](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Fournit des instructions pour la modification d’un document HTML directement à partir de la fenêtre Propriétés et fournit un tableau détaillant les champs dans un document HTML dans la fenêtre Propriétés.  
  
 [IDispatch](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Décrit le `IDispatch` interface, ce qui a été conçu tout d’abord pour prendre en charge d’automation, en fournissant un mécanisme à liaison tardive pour accéder à et récupérer des informations sur les méthodes et propriétés d’un objet.  
  
 [NIB : Introduction aux propriétés dynamiques (Visual Studio)](http://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fournit une vue d’ensemble des propriétés dynamiques qui vous permettent de configurer votre application afin que les valeurs de propriété sont stockées dans un fichier de configuration externe au lieu de code compilé de l’application.  
  
 [NIB : projets comme conteneurs](http://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Décrit le rôle du projet en tant que conteneur dans une solution pour gérer logiquement, générer et déboguer les éléments qui composent votre application.  
  
 [NIB : projet propriétés](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Décrit la façon dont le projet gère les paramètres qui vous permettent de propriétés de contrôle qui s’appliquent à la totalité du projet ainsi que les propriétés qui sont limitées à certaines configurations de build du projet.  
  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explique comment [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gère efficacement les éléments tels que les références, les connexions de données, les dossiers et les fichiers qui sont requis par votre travail de développement via des solutions et projets.  
  
 [Extension d’autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser les services de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
