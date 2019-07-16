---
title: Hiérarchies
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22943d3049ff0e24d00c7c29750e7dcd0efaf846
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158358"
---
# <a name="hierarchies-in-visual-studio"></a>Hiérarchies dans Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE) affiche un projet comme étant un *hiérarchie*. Dans l’IDE, une hiérarchie est une arborescence de nœuds, où chaque nœud possède un ensemble de propriétés associées. Un *hiérarchie du projet* est un conteneur qui contient les éléments du projet, les relations d’éléments et les propriétés associées et les commandes.

 Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], gérer les hiérarchies de projet à l’aide de l’interface de la hiérarchie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface redirige les commandes que vous appelez à partir d’éléments de projet dans la fenêtre de hiérarchie appropriée au lieu du Gestionnaire de commandes standard.

## <a name="project-hierarchies"></a>Hiérarchies de projet
 Chaque hiérarchie de projet contient des éléments que vous pouvez afficher et modifier. Ces éléments varient selon le type de projet. Par exemple, un projet de base de données peut contenir des procédures stockées, les vues de base de données et les tables de base de données. Un projet de langage de programmation, quant à eux, inclura probablement fichiers sources et fichiers de ressources pour les bitmaps et boîtes de dialogue. Les hiérarchies peuvent être imbriqués, ce qui vous donne une certaine flexibilité ajoutée lorsque vous créez une hiérarchie de projet.

 Lorsque vous créez un nouveau type de projet, le type de projet détermine l’ensemble complet des éléments qui peuvent être modifiées qu’il contient. Toutefois, les projets peuvent contenir des éléments pour lesquels ils n’ont pas dans édition prise en charge. Par exemple, les projets Visual C++ peuvent contenir des fichiers HTML, bien que Visual C++ ne fournit pas de n’importe quel éditeur personnalisé pour le type de fichier HTML.

 Hiérarchies de gérer la persistance des éléments qu’ils contiennent. L’implémentation de la hiérarchie doit contrôler toutes les propriétés spéciales qui affectent la persistance des éléments dans la hiérarchie. Par exemple, si les éléments représentent des objets dans un référentiel au lieu de fichiers, l’implémentation de la hiérarchie doit contrôler la persistance de ces objets. L’IDE lui-même dirige la hiérarchie pour enregistrer les éléments en conformité avec les entrées d’utilisateur, mais l’IDE ne contrôle pas les actions requises pour enregistrer les éléments. Au lieu de cela, le projet est dans le contrôle.

 Lorsqu’un utilisateur ouvre un élément dans un éditeur, la hiérarchie des contrôles de cet élément est sélectionnée et devient la hiérarchie active. La hiérarchie sélectionnée détermine l’ensemble des commandes disponibles pour agir sur l’élément. Suivi de focus de l’utilisateur de cette manière permet à la hiérarchie afin de refléter le contexte de l’utilisateur actuel.

## <a name="see-also"></a>Voir aussi
 [Types de projets](../../extensibility/internals/project-types.md) [sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md) [exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md)
