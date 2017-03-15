---
title: "Cr&#233;ation de la commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes"
  - "commandes, mise en œuvre"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Cr&#233;ation de la commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous ajoutez une commande à un VSPackage, vous devez spécifier où il est d'apparaître, si celui\-ci est disponible, et comment il doit être gérée.  
  
## définir des commandes  
 Pour définir de nouvelles commandes, incluez un fichier du Tableau de commande Visual Studio \(.vsct\) dans votre projet de VSPackage.  Si vous avez créé un VSPackage à l'aide de le modèle de package Visual Studio, le projet inclut un de ces fichiers.  Pour plus d'informations, consultez [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio fusionne tous les fichiers de .vsct qu'il recherche afin de pouvoir afficher les commandes.  Comme ces fichiers sont distincts du fichier binaire d'un VSPackage, Visual Studio ne doit pas charger le package pour rechercher les commandes.  Pour plus d'informations, consultez [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio utilise l'attribut d'alignement de <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> pour définir des ressources de menu et des commandes.  Pour plus d'informations, consultez [Implémentation](../../extensibility/internals/command-implementation.md).  
  
 Les commandes peuvent être modifiés au moment de l'exécution de différentes façons.  ils peuvent être affichés ou masqués, activés ou désactivés.  Ils peuvent afficher les différents texte ou des icônes, ou contiennent des valeurs différentes.  beaucoup de personnalisation peut être exécutée avant que Visual Studio charge votre VSPackage.  Pour plus d'informations, consultez [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## gestionnaires de commandes  
 Lorsque vous créez une commande, vous devez fournir un gestionnaire d'événements pour exécuter la commande.  Si l'utilisateur sélectionne la commande, elle doit être correctement routée.  Le routage une commande signifie l'envoyer au VSPackage correct pour activer ou désactiver celui\-ci, la masquer ou pour l'afficher, et l'exécute si l'utilisateur choisit de le faire.  Pour plus d'informations, consultez [Algorithme de routage](../../extensibility/internals/command-routing-algorithm.md).  
  
## L'environnement de commande Visual Studio  
 Visual Studio peut héberger un certain nombre de VSPackages, et peut fournir son propre jeu de commandes.  L'environnement affiche uniquement les commandes relatives à la tâche actuelle.  Pour plus d'informations, consultez [Disponibilité](../../extensibility/internals/command-availability.md) et [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md).  
  
 Un VSPackage qui définit de nouvelles commandes, les menus, les barres d'outils, ou des menus contextuels fournit ses informations de commande dans Visual Studio au moment de l'installation à l'aide de les entrées du Registre que les sources de référence dans le code natif ou des assemblys managés.  Chaque ressource référence ensuite un fichier de ressources données binaires \(.cto\), qui se produit lorsque vous compilez un fichier du Tableau de commande Visual Studio \(.vsct\).  Cela permet à Visual Studio de fournir des jeux de commandes fusionnés, les menus, et les barres d'outils sans devoir charger chaque VSPackage installé.  
  
### organisation de commande  
 L'environnement positionne les commandes par le groupe, priorité, et le menu.  
  
-   Les groupes sont des collections logiques de commandes connexes, du groupe de commandes par exemple, de **Couper**, de **Copier**, et de **Coller** .  Les groupes sont des commandes qui s'affichent dans les menus.  
  
-   La priorité détermine l'ordre dans lequel les différentes commandes à un groupe apparaissent dans le menu.  
  
-   Les menus agissent comme conteneurs pour les groupes.  
  
 L'environnement prédéfinit certaines commandes, groupes, et menus.  Pour plus d'informations, consultez [Commande par défaut, le groupe et la sélection élective de la barre d'outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 une commande peut être assignée à un groupe principal.  le groupe principal contrôle la position de la commande dans la structure de menu principal et dans la boîte de dialogue de **Personnaliser** .  Une commande peut apparaître à plusieurs groupes ; par exemple, une commande peut être dans le menu principal, dans un menu contextuel, puis sur une barre d'outils.  Pour plus d'informations, consultez [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### Routage de commandes  
 Le processus d'appel et router des commandes pour les VSPackages diffère du processus d'appeler des méthodes sur des instances d'objet.  
  
 L'environnement itinéraire des commandes de manière séquentielle du contexte \(local\) la plus profonde de commande, en fonction de la sélection actuelle, au contexte \(global\) extérieur.  Le premier contexte qui peut exécuter la commande est l'élément qui la gérer.  Pour plus d'informations, consultez [Algorithme de routage](../../extensibility/internals/command-routing-algorithm.md).  
  
 Dans la plupart des instances, les commandes de handles d'environnement à l'aide de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  Étant donné que le modèle de routage des commandes active de nombreux objets aux commandes de handles, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> peut être implémenté par plusieurs objets ; ceux\-ci incluent les contrôles Microsoft ActiveX, les implémentations de vue fenêtre, les objets document, des hiérarchies de projet, des objets d'un VSPackage eux\-mêmes \(pour les commandes globales\).  Dans certains cas, par exemple, le routage des commandes dans une hiérarchie, l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> doit être implémenté.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Implémentation](../../extensibility/internals/command-implementation.md)|décrit comment implémenter des commandes dans un VSPackage.|  
|[Disponibilité](../../extensibility/internals/command-availability.md)|Décrit comment le contexte de Visual Studio définit les commandes disponibles.|  
|[Algorithme de routage](../../extensibility/internals/command-routing-algorithm.md)|Décrit comment l'architecture de routage des commandes de Visual Studio active des commandes d'être géré par les VSPackages différent.|  
|[Instructions de sélection élective](../../extensibility/internals/command-placement-guidelines.md)|Indique comment positionner des commandes de l'environnement Visual Studio.|  
|[Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Décrit comment les VSPackages peut mieux utiliser l'architecture de commande Visual Studio.|  
|[Commande par défaut, le groupe et la sélection élective de la barre d'outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Décrit comment les VSPackages peut la meilleure utilisation des commandes qui sont inclus dans Visual Studio.|  
|[La gestion de packages VS](../../extensibility/managing-vspackages.md)|Décrit comment Visual Studio charge les VSPackages.|  
|[Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fournit des informations sur les fichiers du XML .vsct, qui sont utilisés pour décrire la disposition et l'apparence des commandes de VSPackages.|