---
title: Architecture des Types de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 6
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
ms.openlocfilehash: c9b238f853d7dd3a246f4b3204b15eda34b56885
ms.lasthandoff: 02/22/2017

---
# <a name="project-types-architecture"></a>Architecture des Types de projet
Cette section contient des informations détaillées sur l’architecture des types de projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)  
 Répertorie les services de qu'un type de projet peut consommer et les interfaces, qu'elle doit implémenter.  
  
 [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md)  
 Décrit les interfaces, types de projets à la fois doivent implémenter et peuvent éventuellement implémenter pour fournir des fonctionnalités supplémentaires.  
  
 [Quand créer des Types de projets](../../extensibility/internals/when-to-create-project-types.md)  
 Tapez permet de décider si vous devez créer un projet et lorsque vous pouvez utiliser un autre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonctionnalité d’extensibilité telles que les packages VS et les éditeurs à atteindre le même objectif.  
  
 [Hiérarchies et la sélection](../../extensibility/internals/hierarchies-and-selection.md)  
 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise des hiérarchies et contexte de sélection pour fournir une expérience utilisateur cohérente et simplifié.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 Explique comment les sous-types de projet vous permettent de personnaliser le comportement des systèmes de projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit une vue d’ensemble des projets en tant que les blocs de construction de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Des liens sont fournis vers d’autres rubriques qui expliquent comment projets de contrôle de génération et compilation du code.
