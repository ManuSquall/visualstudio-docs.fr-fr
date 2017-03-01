---
title: "Hiérarchies dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca8fa51a14f38dcd651f26e8ed10ca48d670f37b
ms.lasthandoff: 02/22/2017

---
# <a name="hierarchies-in-visual-studio"></a>Hiérarchies dans Visual Studio
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) affiche un projet comme un *hiérarchie*. Dans l’IDE, une hiérarchie est une arborescence de nœuds, où chaque nœud possède un ensemble de propriétés associées. A *hiérarchie du projet* est un conteneur qui contient les éléments du projet, relations d’éléments, les propriétés associées et des commandes.  
  
 Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], gérer les hiérarchies de projet à l’aide de l’interface de la hiérarchie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface redirige les commandes que vous appelez à partir d’éléments de projet dans la fenêtre hiérarchie appropriée au lieu du Gestionnaire de commandes standard.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
## <a name="project-hierarchies"></a>Hiérarchies de projet  
 Chaque hiérarchie de projet contient des éléments que vous pouvez afficher et modifier. Ces éléments varient en fonction du type de projet. Par exemple, un projet de base de données peut contenir des procédures stockées, vues et tables de base de données. Un projet de langage de programmation, en revanche, incluront les fichiers source et fichiers de ressources pour les images bitmap et boîtes de dialogue. Les hiérarchies peuvent être imbriqués, ce qui vous donne une certaine flexibilité ajoutée lorsque vous créez une hiérarchie de projet.  
  
 Lorsque vous créez un nouveau type de projet, le type de projet détermine l’ensemble d’éléments qui peuvent être modifiées qu’il contient. Toutefois, les projets peuvent contenir des éléments pour lesquels ils n’ont pas dans édition prise en charge. Par exemple, les projets Visual C++ peuvent contenir des fichiers HTML, bien que Visual C++ ne fournit pas d’un éditeur personnalisé pour le type de fichier HTML.  
  
 Hiérarchies de gérer la persistance des éléments qu’ils contiennent. L’implémentation de la hiérarchie doit contrôler des propriétés spéciales qui affectent la persistance des éléments dans la hiérarchie. Par exemple, si les éléments représentent des objets dans un référentiel au lieu de fichiers, l’implémentation de la hiérarchie doit contrôler la persistance de ces objets. L’IDE lui-même dirige la hiérarchie pour enregistrer les éléments compatibles avec les entrées d’utilisateur, mais l’IDE ne contrôle pas les actions requises pour enregistrer les éléments. Au lieu de cela, le projet est dans le contrôle.  
  
 Lorsqu’un utilisateur ouvre un élément dans un éditeur, la hiérarchie des contrôles de cet élément est sélectionnée et devient la hiérarchie active. La hiérarchie sélectionnée détermine l’ensemble des commandes disponibles pour agir sur l’élément. Suivi de focus de l’utilisateur de cette manière permet la hiérarchie refléter le contexte de l’utilisateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de projets](../../extensibility/internals/project-types.md)   
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md)
