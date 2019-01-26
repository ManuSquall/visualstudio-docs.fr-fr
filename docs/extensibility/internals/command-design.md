---
title: Commande de conception | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42b41ee59f842c277400ba03ff682a757d5343e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009828"
---
# <a name="command-design"></a>Conception de la commande
Lorsque vous ajoutez une commande à un VSPackage, vous devez spécifier où il doit apparaître, lorsqu’il est disponible, et comment il doit être gérée.  
  
## <a name="define-commands"></a>Définir des commandes  
 Pour définir de nouvelles commandes, inclure une table de commandes de Visual Studio (*.vsct*) le fichier dans votre projet VSPackage. Si vous avez créé un VSPackage à l’aide du modèle de package Visual Studio, le projet inclut un de ces fichiers. Pour plus d’informations, consultez [fichiers Visual Studio command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio fusionne tous les *.vsct* fichiers recherche pour qu’il puisse afficher les commandes. Étant donné que ces fichiers sont distincts du VSPackage binaire, Visual Studio n’a pas de charger le package pour trouver les commandes. Pour plus d’informations, consultez [comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio utilise le <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attribut d’inscription pour définir des ressources de menu et commandes. Pour plus d’informations, consultez [implémentation de la commande](../../extensibility/internals/command-implementation.md).  
  
 Commandes peuvent être modifiés au moment de l’exécution dans un nombre de différentes façons. Ils peuvent être affichées ou masquées, activées ou désactivées. Ils peuvent afficher un texte différent ou icônes ou contiennent des valeurs différentes. Un grand nombre de fonctions peut être effectué avant que Visual Studio charge votre VSPackage. Pour plus d’informations, consultez [comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Gestionnaires de commandes  
 Lorsque vous créez une commande, vous devez fournir un gestionnaire d’événements pour exécuter la commande. Si l’utilisateur sélectionne la commande, il doit être routé de manière appropriée. Routage d’une commande signifie son envoi au VSPackage correct pour activer ou désactiver, masquer ou afficher et l’exécuter si l’utilisateur choisit de le faire. Pour plus d’informations, consultez [algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="visual-studio-command-environment"></a>Environnement de commande de Visual Studio  
 Visual Studio peut héberger un nombre quelconque de VSPackages, et chacun peut contribuer à son propre jeu de commandes. L’environnement affiche uniquement les commandes qui sont appropriés à la tâche actuelle. Pour plus d’informations, consultez [commande disponibilité](../../extensibility/internals/command-availability.md) et [les objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md).  
  
 Un VSPackage qui définit les nouvelles commandes, menus, barres d’outils, des menus contextuels fournit ses informations de commande à Visual Studio au moment de l’installation par le biais des entrées de Registre qui référencent des ressources dans des assemblys natifs ou managés. Chaque ressource fait ensuite référence à une ressource de données binaires (*.cto*) fichier, qui est généré lorsque vous compilez une table de commandes de Visual Studio (*.vsct*) fichier. Cela permet à Visual Studio fournir des jeux de commandes fusionnées, les menus et barres d’outils sans avoir à charger chaque VSPackage installé.  
  
### <a name="command-organization"></a>Organisation de commande  
 L’environnement positionne les commandes par groupe, de priorité et de menu.  
  
- Les groupes sont des collections logiques de commandes associées, par exemple, le **couper**, **copie**, et **coller** groupe de commandes. Les groupes sont les commandes qui s’affichent dans les menus.  
  
- Priorité détermine l’ordre dans lequel les commandes individuelles dans un groupe apparaissent dans le menu.  
  
- Menus agissent comme des conteneurs pour les groupes.  
  
  L’environnement prédéfinit certaines commandes, les groupes et les menus. Pour plus d’informations, consultez [placement de commande, le groupe et barre d’outils par défaut](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Une commande peut être attribuée à un groupe principal. Le groupe principal détermine la position de la commande dans la structure du menu principal et dans le **personnaliser** boîte de dialogue. Une commande peut apparaître dans plusieurs groupes ; par exemple, une commande peut être sur une barre d’outils dans le menu principal et dans un menu contextuel. Pour plus d’informations, consultez [comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Routage des commandes  
 Le processus d’appel et le routage des commandes pour les VSPackages diffère du processus d’appel de méthodes sur des instances d’objet.  
  
 L’environnement achemine les commandes séquentiellement dans le contexte de commande (local) plus profond, qui est basée sur la sélection actuelle, pour le contexte le plus extérieur (global). Le premier contexte qui est en mesure d’exécuter la commande est celle qui prend en charge. Pour plus d’informations, consultez [algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md).  
  
 Dans la plupart des cas, l’environnement gère les commandes à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Étant donné que le schéma de routage de commande permet de nombreux objets différents gérer les commandes, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> peut être implémentée par n’importe quel nombre d’objets ; ceux-ci incluent des contrôles Microsoft ActiveX, les implémentations de vue de fenêtre, les objets de document, hiérarchies de projet, et les objets VSPackage eux-mêmes (pour les commandes globales). Dans certains cas particuliers, par exemple, routage des commandes dans une hiérarchie, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface doit être implémentée.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Implémentation de la commande](../../extensibility/internals/command-implementation.md)|Décrit comment implémenter des commandes dans un VSPackage.|  
|[Disponibilité de la commande](../../extensibility/internals/command-availability.md)|Décrit comment le contexte de Visual Studio détermine les commandes qui sont disponibles.|  
|[Algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md)|Décrit comment architecture de routage de commande de Visual Studio permet les commandes pour être gérée par les VSPackages différents.|  
|[Instructions de positionnement de commande](../../extensibility/internals/command-placement-guidelines.md)|Suggère comment positionner les commandes dans l’environnement Visual Studio.|  
|[Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Décrit comment les VSPackages peuvent mieux exploiter l’architecture de commande de Visual Studio.|  
|[Placement de commande, le groupe et barre d’outils par défaut](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Décrit comment les VSPackages peuvent mieux utiliser les commandes qui sont inclus dans Visual Studio.|  
|[Gérer les packages VS](../../extensibility/managing-vspackages.md)|Décrit comment Visual Studio charge VSPackages.|  
|[Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fournit des informations sur basé sur XML *.vsct* fichiers, qui sont utilisés pour décrire la disposition et l’apparence des commandes dans VSPackages.|