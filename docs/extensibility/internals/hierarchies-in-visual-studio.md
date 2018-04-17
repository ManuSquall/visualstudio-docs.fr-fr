---
title: Hiérarchies dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d1f018b9cc48d059761a26721c808024f60bb3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="hierarchies-in-visual-studio"></a>Hiérarchies dans Visual Studio
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) affiche un projet comme étant un *hiérarchie*. Dans l’IDE, une hiérarchie est une arborescence de nœuds, où chaque nœud dispose d’un ensemble de propriétés associées. A *hiérarchie du projet* est un conteneur qui conserve les éléments du projet, les relations, les éléments et propriétés associées des éléments et commandes.  
  
 Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], gérer les hiérarchies de projet à l’aide de l’interface de la hiérarchie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface redirige les commandes que vous appelez à partir d’éléments de projet dans la fenêtre hiérarchie appropriée à la place le Gestionnaire de commandes standard.  
  
## <a name="project-hierarchies"></a>Hiérarchies de projet  
 Chaque hiérarchie de projet contient des éléments que vous pouvez afficher et modifier. Ces éléments varient selon le type de projet. Par exemple, un projet de base de données peut contenir des procédures stockées, des vues de base de données et des tables de base de données. Un projet de langage de programmation, quant à eux, incluront fichiers sources et les fichiers de ressources pour les images bitmap et boîtes de dialogue. Les hiérarchies peuvent être imbriqués, ce qui vous donne une certaine flexibilité ajoutée lorsque vous créez une hiérarchie de projet.  
  
 Lorsque vous créez un nouveau type de projet, le type de projet détermine l’ensemble complet des éléments qui peuvent être modifiées qu’il contient. Toutefois, les projets peuvent contenir des éléments pour lesquels ils n’ont pas dans édition prise en charge. Par exemple, les projets Visual C++ peuvent contenir des fichiers HTML, bien que Visual C++ ne fournit pas de n’importe quel éditeur personnalisé pour le type de fichier HTML.  
  
 Gérer les hiérarchies de la persistance des éléments qu’ils contiennent. L’implémentation de la hiérarchie doit contrôler des propriétés spéciales qui affectent la persistance des éléments dans la hiérarchie. Par exemple, si les éléments représentent des objets dans un référentiel au lieu de fichiers, l’implémentation de la hiérarchie doit contrôler la persistance de ces objets. L’IDE lui-même dirige la hiérarchie afin d’enregistrer les éléments conformément à l’entrée d’utilisateur, mais l’IDE ne contrôle pas les actions requises pour enregistrer les éléments. Au lieu de cela, le projet est dans le contrôle.  
  
 Lorsqu’un utilisateur ouvre un élément dans un éditeur, la hiérarchie de contrôle de cet élément est sélectionnée et devient la hiérarchie active. La hiérarchie sélectionnée détermine l’ensemble des commandes disponibles pour agir sur l’élément. Suivi du focus de l’utilisateur de cette manière permet à la hiérarchie afin de refléter le contexte de l’utilisateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de projets](../../extensibility/internals/project-types.md)   
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples)