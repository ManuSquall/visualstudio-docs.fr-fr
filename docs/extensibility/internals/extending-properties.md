---
title: Étendre les propriétés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1a34edfbc6cede24f3238068549412d630827cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="extending-properties"></a>Étendre les propriétés
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propriétés** fenêtre est une fenêtre de propriétés universel pour les composants COM et COM + et prend en charge tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produits. Le **propriétés** fenêtre fonctionne avec `ITypeInfo` informations de type et des métadonnées COM + pour répertorier les propriétés au moment du design pour l’objet actuellement sélectionné dans les autres fenêtres de l’environnement de développement intégré (IDE).  
  
 Le **propriétés** fenêtre, qui peut être ouvert en appuyant sur F4 du clavier, ou en sélectionnant **fenêtre Propriétés** sur la **vue** menu, est utilisé pour afficher et modifier les propriétés liées à la configuration, au moment du design et les événements des objets sélectionnés. Propriétés dépendantes de la configuration associés à des solutions et des projets sont affichées sur [Pages de propriétés](../../extensibility/internals/property-pages.md). Pour plus d’informations, [la gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Vue d’ensemble de la fenêtre Propriétés](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Fenêtre Propriétés  
  
 Cette section fournit des informations détaillées relatives aux zones individuelles de la **propriétés** fenêtre et les interfaces que vous devez implémenter et appel à remplir la fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation de la fenêtre Propriétés](../../extensibility/internals/properties-window-overview.md)  
 Explique l’objectif de la **propriétés** fenêtre par rapport à la fenêtre d’outils et la fenêtre de document.  
  
 [Stratégie de modèle et fenêtre Propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Explique comment un projet est contenu dans un projet de modèle d’entreprise, et comment ce projet de modèle d’entreprise peut appliquer la stratégie.  
  
 [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explique les critères de sélection qui détermine quelles informations sont affichées dans le **propriétés** fenêtre.  
  
 [Liste d’objets de la fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md)  
 Décrit l’objectif de la **propriétés** liste d’objets de fenêtre, qui décrit comment, quand un autre objet à partir de cette liste déclenche un appel, l’environnement est informé qu’un objet a été sélectionné.  
  
 [Boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md)  
 Explique l’objectif de quatre boutons affichés sur la **propriétés** barre d’outils de la fenêtre.  
  
 [Afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md)  
 Explique où figurent les noms de propriété et les champs de valeurs de propriété dans la grille.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Traite des projets en tant que blocs de construction de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)  
 Décrit comment vous pouvez utiliser la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Platform pour tester et déboguer les applications que vous devez les créer en permanence.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 Décrit le `IDispatch` interface, ce qui a été conçu tout d’abord pour prendre en charge d’automation, qui fournit un mécanisme à liaison tardive pour accéder à et récupérer des informations sur les méthodes et propriétés d’un objet.  
  
 [Gestion des paramètres d’application (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Fournit une vue d’ensemble des paramètres d’application vous permettent de configurer votre application afin que les valeurs de propriété sont stockées dans un fichier de configuration externe au lieu de code compilé de l’application.  
  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explique comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère efficacement les éléments tels que les références, les connexions de données, les dossiers et les fichiers qui sont requis par votre effort de développement via des solutions et projets.  
  
 [Extension d’autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] services pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].