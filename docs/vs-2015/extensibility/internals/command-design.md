---
title: Commande de conception | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953835"
---
# <a name="command-design"></a>Création de commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsque vous ajoutez une commande à un VSPackage, vous devez spécifier où il doit apparaître, lorsqu’il est disponible, et comment il doit être gérée.  
  
## <a name="defining-commands"></a>Définition de commandes  
 Pour définir les nouvelles commandes, inclure un fichier Visual Studio Command Table (.vsct) dans votre projet VSPackage. Si vous avez créé un VSPackage à l’aide du modèle de Package Visual Studio, le projet inclut un de ces fichiers. Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio fusionne tous les fichiers .vsct qu’il trouve pour qu’il puisse afficher les commandes. Étant donné que ces fichiers sont distincts du VSPackage binaire, Visual Studio n’a pas de charger le package pour trouver les commandes. Pour plus d’informations, consultez [comment VSPackages ajouter des éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio utilise le <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attribut d’inscription pour définir des ressources de menu et commandes. Pour plus d’informations, consultez [implémentation](../../extensibility/internals/command-implementation.md).  
  
 Commandes peuvent être modifiés au moment de l’exécution dans un nombre de différentes façons. Ils peuvent être affichées ou masquées, activées ou désactivées. Ils peuvent afficher un texte différent ou icônes ou contiennent des valeurs différentes. Un grand nombre de fonctions peut être effectué avant que Visual Studio charge votre VSPackage. Pour plus d’informations, consultez [comment VSPackages ajouter des éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Gestionnaires de commandes  
 Lorsque vous créez une commande, vous devez fournir un gestionnaire d’événements pour exécuter la commande. Si l’utilisateur sélectionne la commande, il doit être routé de manière appropriée. Routage d’une commande signifie son envoi au VSPackage correct pour activer ou désactiver, masquer ou afficher et l’exécuter si l’utilisateur choisit de le faire. Pour plus d’informations, consultez [algorithme de routage](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>L’environnement de commande de Visual Studio  
 Visual Studio peut héberger un nombre quelconque de VSPackages, et chacun peut contribuer à son propre jeu de commandes. L’environnement affiche uniquement les commandes qui sont appropriés à la tâche actuelle. Pour plus d’informations, consultez [disponibilité](../../extensibility/internals/command-availability.md) et [les objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md).  
  
 Un VSPackage qui définit les nouvelles commandes, menus, barres d’outils, des menus contextuels fournit ses informations de commande à Visual Studio au moment de l’installation par le biais des entrées de Registre qui référencent des ressources dans des assemblys natifs ou managés. Chaque ressource fait ensuite référence à un fichier de ressources (.cto) de données binaires, qui est généré lorsque vous compilez un fichier Visual Studio Command Table (.vsct). Cela permet à Visual Studio fournir des jeux de commandes fusionnées, les menus et barres d’outils sans avoir à charger chaque VSPackage installé.  
  
### <a name="command-organization"></a>Organisation de commande  
 L’environnement positionne les commandes par groupe, de priorité et de menu.  
  
- Les groupes sont des collections logiques de commandes associées, par exemple, le **couper**, **copie**, et **coller** groupe de commandes. Les groupes sont les commandes qui s’affichent dans les menus.  
  
- Priorité détermine l’ordre dans lequel les commandes individuelles dans un groupe apparaissent dans le menu.  
  
- Menus agissent comme des conteneurs pour les groupes.  
  
  L’environnement prédéfinit certaines commandes, les groupes et les menus. Pour plus d’informations, consultez [commande par défaut, le groupe et positionnement de la barre d’outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Une commande peut être attribuée à un groupe principal. Le groupe principal détermine la position de la commande dans la structure du menu principal et dans le **personnaliser** boîte de dialogue. Une commande peut apparaître dans plusieurs groupes ; par exemple, une commande peut être sur une barre d’outils dans le menu principal et dans un menu contextuel. Pour plus d’informations, consultez [comment VSPackages ajouter des éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>routage des commandes  
 Le processus d’appel et le routage des commandes pour les VSPackages diffère du processus d’appel de méthodes sur des instances d’objet.  
  
 L’environnement achemine les commandes séquentiellement dans le contexte de commande (local) plus profond, qui est basée sur la sélection actuelle, pour le contexte le plus extérieur (global). Le premier contexte qui est en mesure d’exécuter la commande est celle qui prend en charge. Pour plus d’informations, consultez [algorithme de routage](../../extensibility/internals/command-routing-algorithm.md).  
  
 Dans la plupart des cas, l’environnement gère les commandes à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Étant donné que le schéma de routage de commande permet de nombreux objets différents gérer les commandes, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> peut être implémentée par n’importe quel nombre d’objets ; ceux-ci incluent des contrôles Microsoft ActiveX, les implémentations de vue de fenêtre, les objets de document, hiérarchies de projet, et les objets VSPackage eux-mêmes (pour les commandes globales). Dans certains cas particuliers, par exemple, routage des commandes dans une hiérarchie, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface doit être implémentée.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Implémentation](../../extensibility/internals/command-implementation.md)|Décrit comment implémenter des commandes dans un VSPackage.|  
|[Disponibilité](../../extensibility/internals/command-availability.md)|Décrit comment le contexte de Visual Studio détermine les commandes qui sont disponibles.|  
|[Algorithme de routage](../../extensibility/internals/command-routing-algorithm.md)|Décrit comment architecture de routage de commande de Visual Studio permet les commandes pour être gérée par les VSPackages différents.|  
|[Instructions de positionnement](../../extensibility/internals/command-placement-guidelines.md)|Suggère comment positionner les commandes dans l’environnement Visual Studio.|  
|[Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Décrit comment les VSPackages peuvent mieux exploiter l’architecture de commande de Visual Studio.|  
|[Emplacement de commande, de groupe et de barre d’outils par défaut](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Décrit comment les VSPackages peuvent mieux utiliser les commandes qui sont inclus dans Visual Studio.|  
|[Gestion de VSPackages](../../extensibility/managing-vspackages.md)|Décrit comment Visual Studio charge VSPackages.|  
|[Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fournit des informations sur les fichiers .vsct basé sur XML, qui sont utilisés pour décrire la disposition et l’apparence des commandes dans VSPackages.|
