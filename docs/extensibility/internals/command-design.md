---
title: Conception de commande | Microsoft Docs
description: Découvrez comment concevoir une commande pour un VSPackage dans Visual Studio. Notamment, comment spécifier où il s’affiche, quand il est disponible et comment il doit être géré.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab06ade9be1ccd0683cd298a5e758ddcfa883f8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304869"
---
# <a name="command-design"></a>Conception de commande
Lorsque vous ajoutez une commande à un VSPackage, vous devez spécifier où elle doit apparaître, quand elle est disponible et comment elle doit être gérée.

## <a name="define-commands"></a>Définir des commandes
 Pour définir de nouvelles commandes, incluez un fichier de table de commandes Visual Studio (*. vsct*) dans votre projet VSPackage. Si vous avez créé un VSPackage à l’aide du modèle de package Visual Studio, le projet comprend l’un de ces fichiers. Pour plus d’informations, consultez [fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

 Visual Studio fusionne tous les fichiers *. vsct* qu’il trouve afin qu’il puisse afficher les commandes. Étant donné que ces fichiers sont distincts du fichier binaire VSPackage, Visual Studio n’a pas besoin de charger le package pour rechercher les commandes. Pour plus d’informations, consultez [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio utilise l' <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attribut d’inscription pour définir les ressources et les commandes de menu. Pour plus d’informations, consultez Implémentation de la [commande](../../extensibility/internals/command-implementation.md).

 Les commandes peuvent être modifiées au moment de l’exécution de plusieurs façons. Ils peuvent être affichés ou masqués, activés ou désactivés. Ils peuvent afficher différents textes ou icônes, ou contenir des valeurs différentes. Une personnalisation très importante peut être effectuée avant que Visual Studio ne charge votre VSPackage. Pour plus d’informations, consultez [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Gestionnaires de commandes
 Lorsque vous créez une commande, vous devez fournir un gestionnaire d’événements pour exécuter la commande. Si l’utilisateur sélectionne la commande, celle-ci doit être routée de manière appropriée. Le routage d’une commande signifie l’envoyer au VSPackage approprié pour l’activer ou la désactiver, la masquer ou l’afficher, puis l’exécuter si l’utilisateur choisit de le faire. Pour plus d’informations, consultez [algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Environnement de commande Visual Studio
 Visual Studio peut héberger un nombre quelconque de VSPackages et chacun d’eux peut contribuer à son propre jeu de commandes. L’environnement affiche uniquement les commandes qui sont appropriées à la tâche actuelle. Pour plus d’informations, consultez [disponibilité des commandes](../../extensibility/internals/command-availability.md) et objets de contexte de [sélection](../../extensibility/internals/selection-context-objects.md).

 Un VSPackage qui définit de nouvelles commandes, menus, barres d’outils ou menus contextuels fournit ses informations de commande à Visual Studio au moment de l’installation via des entrées de Registre qui référencent des ressources dans des assemblys natifs ou managés. Chaque ressource fait ensuite référence à un fichier de ressources de données binaires (*. directeur technique*), qui est généré quand vous compilez un fichier de table de commandes Visual Studio (*. vsct*). Cela permet à Visual Studio de fournir des jeux de commandes, des menus et des barres d’outils fusionnés sans avoir à charger chaque VSPackage installé.

### <a name="command-organization"></a>Organisation de commande
 L’environnement positionne les commandes par groupe, priorité et menu.

- Les groupes sont des collections logiques de commandes associées, par exemple, le groupe de commandes **couper**, **copier** et **coller** . Les groupes sont les commandes qui s’affichent dans les menus.

- La priorité détermine l’ordre dans lequel les commandes individuelles d’un groupe apparaissent dans le menu.

- Les menus jouent le rôle de conteneurs pour les groupes.

  L’environnement prédéfinit certaines commandes, certains groupes et certains menus. Pour plus d’informations, consultez [positionnement par défaut des commandes, des groupes et des barres d’outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Une commande peut être assignée à un groupe principal. Le groupe principal contrôle la position de la commande dans la structure du menu principal et dans la boîte de dialogue **personnaliser** . Une commande peut apparaître dans plusieurs groupes. par exemple, une commande peut se trouver dans le menu principal, dans un menu contextuel et dans une barre d’outils. Pour plus d’informations, consultez [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Routage des commandes
 Le processus d’appel et de routage des commandes pour les VSPackages diffère du processus d’appel des méthodes sur les instances d’objet.

 L’environnement achemine les commandes de manière séquentielle du contexte de commande le plus profond (local), qui est basé sur la sélection actuelle, vers le contexte le plus à l’extérieur (Global). Le premier contexte qui est en mesure d’exécuter la commande est celui qui le gère. Pour plus d’informations, consultez [algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md).

 Dans la plupart des cas, l’environnement gère les commandes à l’aide de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Étant donné que le schéma de routage des commandes permet à de nombreux objets différents de gérer des commandes, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> peut être implémenté par un nombre quelconque d’objets ; ceux-ci incluent des contrôles Microsoft ActiveX, des implémentations d’affichage de fenêtre, des objets document, des hiérarchies de projets et des objets VSPackage eux-mêmes (pour les commandes globales). Dans certains cas particuliers, par exemple, le routage des commandes dans une hiérarchie, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface doit être implémentée.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Implémentation de la commande](../../extensibility/internals/command-implementation.md)|Décrit comment implémenter des commandes dans un VSPackage.|
|[Disponibilité des commandes](../../extensibility/internals/command-availability.md)|Décrit comment Visual Studio Context détermine les commandes disponibles.|
|[Algorithme de routage des commandes](../../extensibility/internals/command-routing-algorithm.md)|Décrit comment l’architecture de routage des commandes Visual Studio permet aux commandes d’être gérées par différents VSPackages.|
|[Directives relatives au positionnement des commandes](../../extensibility/internals/command-placement-guidelines.md)|Suggère comment positionner des commandes dans l’environnement Visual Studio.|
|[Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Décrit comment les VSPackages peuvent utiliser au mieux l’architecture de commande Visual Studio.|
|[Positionnement par défaut des commandes, des groupes et des barres d’outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Décrit comment les VSPackages peuvent utiliser au mieux les commandes incluses dans Visual Studio.|
|[Gérer VSPackages](../../extensibility/managing-vspackages.md)|Décrit comment Visual Studio charge les VSPackages.|
|[Fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fournit des informations sur les fichiers *. vsct* XML, qui sont utilisés pour décrire la disposition et l’apparence des commandes dans les VSPackages.|
