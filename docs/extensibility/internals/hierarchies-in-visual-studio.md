---
title: Hiérarchies en studio visuel (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708190"
---
# <a name="hierarchies-in-visual-studio"></a>Hiérarchies dans Visual Studio
L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) affiche un projet comme une *hiérarchie.* Dans l’IDE, une hiérarchie est un arbre de nœuds, où chaque nœud a un ensemble de propriétés associées. Une *hiérarchie de projet* est un conteneur qui contient les éléments du projet, les relations des éléments et les propriétés et commandes associées aux articles.

 Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous gérez les hiérarchies <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>de projet en utilisant l’interface de hiérarchie, . L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> redirige les commandes que vous invoquez des éléments de projet à la fenêtre de hiérarchie appropriée au lieu du gestionnaire de commande standard.

## <a name="project-hierarchies"></a>Hiérarchies de projet
 Chaque hiérarchie de projet contient des éléments que vous pouvez afficher et modifier. Ces éléments varient selon le type de projet. Par exemple, un projet de base de données peut contenir des procédures stockées, des vues de base de données et des tables de base de données. Par contre, un projet en langage de programmation comprendra probablement des fichiers source et des fichiers de ressources pour les bitmaps et les boîtes de dialogue. Les hiérarchies peuvent être imbriquées, ce qui vous donne une certaine flexibilité supplémentaire lorsque vous créez une hiérarchie de projet.

 Lorsque vous créez un nouveau type de projet, le type de projet contrôle l’ensemble complet d’éléments qui peuvent y être modifiés. Cependant, les projets peuvent contenir des éléments pour lesquels ils n’ont pas de support d’édition. Par exemple, les projets Visual CMD peuvent contenir des fichiers HTML, même si Visual CMD ne fournit aucun éditeur personnalisé pour le type de fichier HTML.

 Les hiérarchies gèrent la persistance des objets qu’ils contiennent. La mise en œuvre de la hiérarchie doit contrôler toutes les propriétés spéciales qui affectent la persistance des éléments au sein de la hiérarchie. Par exemple, si les éléments représentent des objets dans un référentiel au lieu de fichiers, la mise en œuvre de la hiérarchie doit contrôler la persistance de ces objets. L’IDE lui-même ordonne à la hiérarchie d’enregistrer les éléments en conformité avec l’entrée de l’utilisateur, mais l’IDE ne contrôle pas les mesures nécessaires pour enregistrer ces éléments. Au lieu de cela, le projet est en contrôle.

 Lorsqu’un utilisateur ouvre un élément dans un éditeur, la hiérarchie qui contrôle cet élément est sélectionnée et devient la hiérarchie active. La hiérarchie sélectionnée détermine l’ensemble des commandes disponibles pour agir sur l’élément. Le suivi de la mise au point de l’utilisateur de cette manière permet à la hiérarchie de refléter le contexte actuel de l’utilisateur.

## <a name="see-also"></a>Voir aussi
- [Types de projet](../../extensibility/internals/project-types.md)
- [Sélection et monnaie dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Échantillons DE VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
