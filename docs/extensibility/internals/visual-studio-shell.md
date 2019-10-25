---
title: Shell Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722054"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Le shell [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est l’agent principal d’intégration dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. L’interpréteur de commandes fournit les fonctionnalités nécessaires pour permettre aux VSPackages de partager des services communs. Étant donné que l’objectif architectural de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consiste à exercer des fonctionnalités principales dans les VSPackages, l’interpréteur de commandes est une infrastructure qui fournit des fonctionnalités de base et prend en charge la communication croisée entre ses VSPackages de composants.

## <a name="shell-responsibilities"></a>Responsabilités de l’interpréteur de commandes
 L’interpréteur de commandes a les responsabilités clés suivantes :

- Prise en charge (via des interfaces COM) éléments de base de l’interface utilisateur (IU). Il s’agit notamment des menus et barres d’outils par défaut, des cadres de fenêtre de document ou des fenêtres enfants MDI, ainsi que des frames de fenêtre d’outils et de la prise en charge de l’ancrage.

- Gestion d’une liste en cours d’exécution de tous les documents actuellement ouverts dans une table de documents en cours d’exécution (RDT) afin de coordonner la persistance des documents et de garantir qu’un document ne peut pas être ouvert de plusieurs façons ou d’une manière incompatible.

- Prise en charge de l’interface de routage de commande et de gestion de commande, `IOleCommandTarget`.

- Chargement des VSPackages aux moments appropriés. Le chargement différé d’un VSPackage est nécessaire pour améliorer les performances de l’interpréteur de commandes.

- La gestion de certains services partagés, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, qui fournit des fonctionnalités d’interpréteur de commandes de base et <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui fournit des fonctionnalités de fenêtrage de base.

- Gestion des fichiers de solution (. sln). Les solutions contiennent des groupes de projets connexes, similaires aux fichiers d’espace de travail ( C++ . dsw) dans Visual 6,0.

- Suivi de la sélection à l’ensemble du shell, du contexte et de la devise. L’interpréteur de commandes effectue le suivi des types d’éléments suivants :

  - Le projet actif

  - Élément de projet actuel ou ItemID du <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> actuel

  - Sélection actuelle pour la fenêtre **Propriétés** ou `SelectionContainer`

  - ID de contexte d’interface utilisateur ou CmdUIGuids qui contrôlent la visibilité des commandes, menus et barres d’outils

  - Éléments actuellement actifs, tels que la fenêtre active, le document et le gestionnaire d’annulation

  - Attributs de contexte de l’utilisateur qui pilotent l’aide dynamique

  L’interpréteur de commandes sert également à la communication entre les VSPackages installés et les services actuels. Il prend en charge les fonctionnalités principales de l’interpréteur de commandes et les met à disposition de tous les VSPackages intégrés dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ces fonctionnalités principales incluent les éléments suivants :

- Boîte de dialogue **à propos** de et écran de démarrage

- Boîtes **de dialogue Ajouter un nouvel élément et ajouter un élément existant**

- Fenêtre **affichage de classes** et **Explorateur d’objets**

- Boîte de dialogue **références**

- Fenêtre **structure du document**

- Fenêtre **d’aide dynamique**

- **Rechercher** et **remplacer**

- Boîtes de dialogue **ouvrir un projet** et **ouvrir un fichier** dans le menu **nouveau**

- Boîte de dialogue **options** du menu **Outils**

- Fenêtre **Propriétés**

- **Explorateur de solutions**

- Fenêtre **liste des tâches**

- **Boîte à outils**

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)