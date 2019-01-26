---
title: Étendre les propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 095c9a81b6bd7d1c4eb75fafce6f3311b413581f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935538"
---
# <a name="extend-properties"></a>Étendre les propriétés
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propriétés** fenêtre est un navigateur de propriété universelle pour les composants COM et COM + et prend en charge tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produits. Le **propriétés** fenêtre fonctionne avec `ITypeInfo` informations de type et des métadonnées COM + pour répertorier les propriétés au moment du design pour l’objet actuellement sélectionné dans une autre fenêtre dans l’environnement de développement intégré (IDE).  
  
 Le **propriétés** fenêtre, ce qui peut être ouvert en appuyant sur **F4** sur le clavier, ou en sélectionnant **fenêtre Propriétés** sur le **vue** menu, est utilisé pour afficher et modifier les propriétés liées à la configuration, au moment du design et les événements des objets sélectionnés. Propriétés dépendantes de la configuration, associées aux solutions et projets, s’affichent sur [pages de propriétés](../../extensibility/internals/property-pages.md). Pour plus d’informations, [gérer les options de configuration](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Vue d’ensemble de la fenêtre Propriétés](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Fenêtre Propriétés  
  
 Cette section fournit des informations détaillées relatives aux zones individuelles de la **propriétés** fenêtre et les interfaces que vous devez implémenter et appel à remplir la fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la fenêtre Propriétés](../../extensibility/internals/properties-window-overview.md)  
 Explique l’objectif de la **propriétés** fenêtre par rapport à la fenêtre outil et la fenêtre de document.  
  
 [Stratégie de modèle et de la fenêtre Propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Explique comment un projet est contenu dans un projet de modèle d’entreprise, et comment ce projet de modèle d’entreprise peut appliquer la stratégie.  
  
 [Interfaces et les champs de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explique les critères de sélection qui détermine quelles informations sont affichées dans le **propriétés** fenêtre.  
  
 [Liste d’objets de fenêtre de propriétés](../../extensibility/internals/properties-window-object-list.md)  
 Décrit l’objectif de la **propriétés** liste d’objets de fenêtre, décrivant comment, quand un autre objet à partir de cette liste déclenche un appel, l’environnement est informé qu’un nouvel objet a été sélectionné.  
  
 [Boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md)  
 Explique l’objectif des boutons quatre par défaut affichées sur le **propriétés** barre d’outils de la fenêtre.  
  
 [Afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md)  
 Explique où figurent les noms de propriété et les champs de valeurs de propriété dans la grille.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Traite des projets en tant que blocs de construction de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compiler et générer](../../ide/compiling-and-building-in-visual-studio.md)  
 Décrit comment vous pouvez utiliser le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] platform pour tester et déboguer des applications que vous devez les créer en permanence.  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 Décrit le `IDispatch` interface, ce qui a été conçu tout d’abord pour prendre en charge d’automation, en fournissant un mécanisme à liaison tardive pour accéder à et récupérer des informations sur les méthodes et propriétés d’un objet.  
  
 [Gérer les paramètres d’application (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Fournit une vue d’ensemble des paramètres d’application vous permettent de configurer votre application afin que les valeurs de propriété sont stockées dans un fichier de configuration externe au lieu de code compilé de l’application.  
  
 [Solutions et projets](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explique comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère efficacement les éléments tels que les références, les connexions de données, les dossiers et les fichiers qui sont requis par votre travail de développement via des solutions et projets.  
  
 [Étendre d’autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser les services de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].