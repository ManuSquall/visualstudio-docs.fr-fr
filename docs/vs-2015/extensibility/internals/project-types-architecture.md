---
title: Architecture des Types de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 775656d2190a36f62c2b047c1ff7f1e02575c1ca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948960"
---
# <a name="project-types-architecture"></a>Architecture des types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section contient des informations détaillées sur l’architecture des types de projets dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)  
 Répertorie les services de qu'un type de projet peut consommer et les interfaces, qu'elle doit implémenter.  
  
 [Principaux composants d’un modèle de projet](../../extensibility/internals/project-model-core-components.md)  
 Décrit les interfaces, types de projets à la fois doivent implémenter et éventuellement peuvent implémenter pour fournir des fonctionnalités supplémentaires.  
  
 [Quand créer des types de projets](../../extensibility/internals/when-to-create-project-types.md)  
 Permet de décider quand vous devez créer un projet de type et le moment où vous pouvez utiliser un autre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fonctionnalité d’extensibilité tels que les VSPackages et éditeurs pour atteindre le même objectif.  
  
 [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)  
 Décrit comment [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilise des hiérarchies et contexte de sélection pour fournir une expérience utilisateur cohérente et simplifiée.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sous-types de projets](../../extensibility/internals/project-subtypes.md)  
 Explique comment les sous-types de projet vous permettent de personnaliser le comportement des systèmes de projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 [Types de projets](../../extensibility/internals/project-types.md)  
 Fournit une vue d’ensemble des projets en tant que blocs de construction de base de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE). Liens sont fournis vers des rubriques supplémentaires qui expliquent comment projets de contrôle de génération et compilation du code.
