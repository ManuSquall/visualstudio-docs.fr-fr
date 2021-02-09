---
title: Hiérarchies dans Visual Studio | Microsoft Docs
description: En savoir plus sur les hiérarchies de projet dans l’environnement de développement intégré (IDE) de Visual Studio qui contiennent des éléments de projet et leurs propriétés associées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 826ef8f7836aaea0b934bb2a7fa8f568492f0b1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880006"
---
# <a name="hierarchies-in-visual-studio"></a>Hiérarchies dans Visual Studio
L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) affiche un projet sous la forme d’une *hiérarchie*. Dans l’IDE, une hiérarchie est une arborescence de nœuds, où chaque nœud a un ensemble de propriétés associées. Une *hiérarchie de projet* est un conteneur qui contient les éléments du projet, les relations des éléments, ainsi que les propriétés et les commandes associées des éléments.

 Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous gérez les hiérarchies de projet à l’aide de l’interface de hiérarchie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface redirige les commandes que vous appelez à partir d’éléments de projet vers la fenêtre de hiérarchie appropriée à la place du gestionnaire de commandes standard.

## <a name="project-hierarchies"></a>Hiérarchies de projet
 Chaque hiérarchie de projet contient des éléments que vous pouvez afficher et modifier. Ces éléments varient en fonction du type de projet. Par exemple, un projet de base de données peut contenir des procédures stockées, des vues de base de données et des tables de base de données. Un projet de langage de programmation, en revanche, inclut probablement des fichiers sources et des fichiers de ressources pour les bitmaps et les boîtes de dialogue. Les hiérarchies peuvent être imbriquées, ce qui vous offre une flexibilité accrue lorsque vous créez une hiérarchie de projet.

 Lorsque vous créez un nouveau type de projet, le type de projet contrôle l’ensemble complet des éléments qui peuvent être modifiés dans celui-ci. Toutefois, les projets peuvent contenir des éléments pour lesquels ils n’ont pas de prise en charge de la modification. Par exemple, les projets Visual C++ peuvent contenir des fichiers HTML, même si Visual C++ ne fournit pas d’éditeur personnalisé pour le type de fichier HTML.

 Les hiérarchies gèrent la persistance des éléments qu’elles contiennent. L’implémentation de la hiérarchie doit contrôler toutes les propriétés spéciales qui affectent la persistance des éléments dans la hiérarchie. Par exemple, si les éléments représentent des objets dans un dépôt au lieu de fichiers, l’implémentation de la hiérarchie doit contrôler la persistance de ces objets. L’IDE lui-même dirige la hiérarchie pour enregistrer les éléments en conformité avec l’entrée d’utilisateur, mais l’IDE ne contrôle pas les actions requises pour enregistrer ces éléments. Au lieu de cela, le projet est sous contrôle.

 Lorsqu’un utilisateur ouvre un élément dans un éditeur, la hiérarchie qui contrôle cet élément est sélectionnée et devient la hiérarchie Active. La hiérarchie sélectionnée détermine l’ensemble des commandes disponibles pour agir sur l’élément. Le suivi du focus utilisateur de cette manière permet à la hiérarchie de refléter le contexte actuel de l’utilisateur.

## <a name="see-also"></a>Voir aussi
- [Types de projets](../../extensibility/internals/project-types.md)
- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
