---
title: Conception de commande (en anglais) Microsoft Docs
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
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709662"
---
# <a name="command-design"></a>Conception de commande
Lorsque vous ajoutez une commande à un VSPackage, vous devez spécifier où elle doit apparaître, quand elle est disponible et comment elle doit être traitée.

## <a name="define-commands"></a>Définir les commandes
 Pour définir de nouvelles commandes, incluez un fichier de commande Visual Studio *(.vsct)* dans votre projet VSPackage. Si vous avez créé un VSPackage en utilisant le modèle de paquet Visual Studio, le projet comprend l’un de ces fichiers. Pour plus d’informations, consultez [les fichiers visual Studio table de commande (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio fusionne tous les fichiers *.vsct* qu’il trouve afin qu’il puisse afficher les commandes. Parce que ces fichiers sont distincts du binaire VSPackage, Visual Studio n’a pas à charger le paquet pour trouver les commandes. Pour plus d’informations, voir [Comment VSPackages ajouter des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> utilise l’attribut d’enregistrement pour définir les ressources et les commandes du menu. Pour plus d’informations, voir [la mise en œuvre du Commandement](../../extensibility/internals/command-implementation.md).

 Les commandes peuvent être modifiées au moment de la course de différentes façons. Ils peuvent être affichés ou cachés, activés ou désactivés. Ils peuvent afficher différents textes ou icônes, ou contenir des valeurs différentes. Une grande personnalisation peut être effectuée avant Visual Studio charge votre VSPackage. Pour plus d’informations, voir [Comment VSPackages ajouter des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Gestionnaires de commandement
 Lorsque vous créez une commande, vous devez fournir un gestionnaire d’événements pour exécuter la commande. Si l’utilisateur sélectionne la commande, elle doit être acheminée de manière appropriée. L’acheminement d’une commande signifie l’envoyer à l’emballage VS correct pour l’activer ou la désactiver, la cacher ou l’afficher, et l’exécuter si l’utilisateur choisit de le faire. Pour plus d’informations, voir [l’algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Environnement de commande Visual Studio
 Visual Studio peut héberger n’importe quel nombre de VSPackages, et chacun peut contribuer son propre ensemble de commande. L’environnement affiche uniquement les commandes qui conviennent à la tâche actuelle. Pour plus d’informations, voir [la disponibilité de commande](../../extensibility/internals/command-availability.md) et les objets [contextuelles de sélection](../../extensibility/internals/selection-context-objects.md).

 Un VSPackage qui définit les nouvelles commandes, menus, barres d’outils ou menus raccourcis fournit ses informations de commande au Studio visuel au moment de l’installation par le biais d’entrées de registre qui font référence aux ressources dans les assemblages autochtones ou gérés. Chaque ressource fait ensuite référence à une ressource de données binaires (*.cto)* fichier, qui est produite lorsque vous compilez une table de commande Visual Studio (*.vsct*) fichier. Cela permet à Visual Studio de fournir des ensembles de commande, des menus et des barres d’outils fusionnés sans avoir à charger tous les VSPackage installés.

### <a name="command-organization"></a>Organisation de commandement
 L’environnement positionne par groupe, priorité et menu.

- Les groupes sont des collections logiques de commandes connexes, par exemple, le groupe de commande **Cut,** **Copy**et **Paste.** Les groupes sont les commandes qui apparaissent sur les menus.

- La priorité détermine l’ordre dans lequel les commandes individuelles d’un groupe apparaissent sur le menu.

- Les menus servent de conteneurs pour les groupes.

  L’environnement prédéfinise certaines commandes, groupes et menus. Pour plus d’informations, consultez [le placement de la commande par défaut, du groupe et de la barre d’outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Une commande peut être affectée à un groupe primaire. Le groupe principal contrôle la position de la commande dans la structure principale du menu et dans la boîte de dialogue **Customize.** Une commande peut apparaître en plusieurs groupes; par exemple, une commande peut être sur le menu principal, sur un menu raccourci, et sur une barre d’outils. Pour plus d’informations, voir [Comment VSPackages ajouter des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Routage des commandes
 Le processus d’invocation et de routage des commandes pour VSPackages diffère du processus de traitement des méthodes d’appel sur les instances d’objets.

 Les itinéraires de l’environnement commandent séquentiellement du contexte de commande le plus intime (local), qui est basé sur la sélection actuelle, au contexte le plus extérieur (global). Le premier contexte qui est capable d’exécuter la commande est celui qui la gère. Pour plus d’informations, voir [l’algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md).

 Dans la plupart des cas, l’environnement gère les commandes en utilisant l’interface. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Parce que le schéma de routage de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> commande permet à de nombreux objets différents de manipuler des commandes, peut être implémenté par n’importe quel nombre d’objets; il s’agit notamment des contrôles Microsoft ActiveX, des implémentations de vue de fenêtre, des objets de documents, des hiérarchies de projets et des objets VSPackage eux-mêmes (pour les commandes globales). Dans certains cas spécialisés, par exemple, les commandes <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de routage dans une hiérarchie, l’interface doit être implémentée.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Mise en œuvre du commandement](../../extensibility/internals/command-implementation.md)|Décrit comment implémenter les commandes dans un VSPackage.|
|[Disponibilité de commande](../../extensibility/internals/command-availability.md)|Décrit comment le contexte visual Studio détermine quelles commandes sont disponibles.|
|[Algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md)|Décrit comment l’architecture de routage de commande Visual Studio permet de manipuler les commandes par différents VSPackages.|
|[Lignes directrices sur le placement de commandement](../../extensibility/internals/command-placement-guidelines.md)|Suggère comment positionner les commandes dans l’environnement Visual Studio.|
|[Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Décrit comment VSPackages peut mieux utiliser l’architecture de commande Visual Studio.|
|[Placement par défaut de commande, de groupe et de barre d’outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Décrit comment VSPackages peut mieux utiliser les commandes qui sont incluses dans Visual Studio.|
|[Gérer VSPackages](../../extensibility/managing-vspackages.md)|Décrit comment Visual Studio charge VSPackages.|
|[Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fournit des informations sur les fichiers *.vsct* basés sur XML, qui sont utilisés pour décrire la mise en page et l’apparence des commandes dans VSPackages.|
