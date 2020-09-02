---
title: Extension des propriétés | Microsoft Docs
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
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690993"
---
# <a name="extending-properties"></a>Extension des propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fenêtre **Propriétés** est un Explorateur de propriétés universel pour les composants COM et com+ et prend en charge tous les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] produits. La fenêtre **Propriétés** fonctionne avec les `ITypeInfo` informations de type et les métadonnées com+ pour répertorier les propriétés au moment du design de l’objet actuellement sélectionné dans toute autre fenêtre de l’environnement de développement intégré (IDE).  
  
 La fenêtre **Propriétés** , qui peut être ouverte en appuyant sur F4 sur le clavier, ou en sélectionnant **fenêtre Propriétés** dans le menu **affichage** , permet d’afficher et de modifier les propriétés et événements de conception indépendants, au moment du design et les objets sélectionnés. Les propriétés dépendantes de la configuration, associées aux solutions et aux projets, sont affichées dans les [pages de propriétés](../../extensibility/internals/property-pages.md). Pour plus d’informations, consultez [plume : propriétés du projet](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)et [plume : gestion des éléments dans les projets](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Vue d'ensemble de la fenêtre Propriétés](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Fenêtre Propriétés  
  
 Cette section fournit des informations détaillées relatives aux zones individuelles de la fenêtre **Propriétés** et aux interfaces que vous devez implémenter et appeler pour remplir la fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble de la fenêtre Propriétés](../../extensibility/internals/properties-window-overview.md)  
 Explique l’objectif de la fenêtre **Propriétés** par rapport à la fenêtre outil et à la fenêtre de document.  
  
 [Stratégie de modèle et fenêtre Propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Explique comment un projet est contenu dans un projet de modèle d’entreprise et comment ce projet de modèle d’entreprise peut appliquer la stratégie.  
  
 [Champs et interfaces de la fenêtre Propriétés](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Décrit la base de la sélection qui détermine les informations qui s’affichent dans la fenêtre **Propriétés** .  
  
 [Liste d’objets de la fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md)  
 Décrit l’objectif de la liste d’objets de la fenêtre **Propriétés** , décrivant comment, lorsqu’un autre objet de cette liste déclenche un appel, l’environnement est informé qu’un nouvel objet a été sélectionné.  
  
 [Boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md)  
 Explique l’objectif des quatre boutons par défaut affichés dans la barre d’outils de la fenêtre **Propriétés** .  
  
 [Afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md)  
 Explique où se trouvent les champs des noms de propriétés et des valeurs de propriété dans la grille.  
  
 [Annonce du suivi de sélection de la fenêtre Propriétés](../../misc/announcing-property-window-selection-tracking.md)  
 Décrit le suivi de sélection pour la fenêtre **Propriétés** .  
  
 [Masquage des propriétés qui ont des propriétés enfants](../../misc/hiding-properties-that-have-child-properties.md)  
 Explique comment masquer les propriétés qui ont des propriétés enfants en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interface.  
  
 [Fourniture d’une fenêtre de propriétés personnalisée](../../misc/providing-a-custom-properties-window.md)  
 Décrit en détail les étapes à suivre pour fournir votre propre Explorateur de propriétés.  
  
 [Obtention de descriptions de champs à partir de la fenêtre Propriétés](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explique où trouver la zone de description qui affiche des informations relatives au champ de propriété sélectionné.  
  
 [Mise à jour des valeurs de propriété dans la fenêtre Propriétés](../../misc/updating-property-values-in-the-properties-window.md)  
 Fournit des instructions pas à pas qui illustrent les deux méthodes permettant de synchroniser la fenêtre **Propriétés** avec les modifications de valeur de propriété.  
  
## <a name="related-sections"></a>Sections connexes  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Décrit les projets comme des blocs de construction de l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)  
 Décrit comment vous pouvez utiliser la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plateforme pour tester et déboguer des applications en continu au fur et à mesure de leur génération.  
  
 [Propriétés des documents HTML, fenêtre Propriétés](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Fournit des instructions pour modifier un document HTML directement à partir de la Fenêtre Propriétés et fournit un tableau détaillant les champs d’un document HTML dans le Fenêtre Propriétés.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Décrit l' `IDispatch` interface, qui a été conçue pour prendre en charge l’automatisation, en fournissant un mécanisme de liaison tardive permettant d’accéder à des informations sur les méthodes et les propriétés d’un objet et de les récupérer.  
  
 [PLUME : présentation des propriétés dynamiques (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fournit une vue d’ensemble des propriétés dynamiques qui vous permettent de configurer votre application afin que les valeurs de propriété soient stockées dans un fichier de configuration externe plutôt que dans le code compilé de l’application.  
  
 [NIB : projets comme conteneurs](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Décrit le rôle du projet en tant que conteneur dans une solution pour gérer logiquement, générer et déboguer les éléments qui composent votre application.  
  
 [PLUME : propriétés du projet](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Décrit comment le projet gère les paramètres qui vous permettent de contrôler les propriétés qui s’appliquent à l’ensemble du projet, ainsi que les propriétés limitées à certaines configurations de build du projet.  
  
 [Solutions et projets](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explique comment [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gère efficacement les éléments tels que les références, les connexions de données, les dossiers et les fichiers requis par votre effort de développement via des solutions et des projets.  
  
 [Extension d’autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explique comment utiliser les services de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
