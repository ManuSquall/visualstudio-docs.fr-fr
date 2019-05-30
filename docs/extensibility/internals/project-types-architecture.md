---
title: Architecture des Types de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d77524097509c45c23d6a3d9cc147e5aba6691d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318894"
---
# <a name="project-types-architecture"></a>Architecture des types de projets
Cette section contient des informations détaillées sur l’architecture des types de projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Dans cette section
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)

 Répertorie les services de qu'un type de projet peut consommer et les interfaces, qu'elle doit implémenter.

- [Principaux composants d’un modèle de projet](../../extensibility/internals/project-model-core-components.md)

 Décrit les interfaces, types de projets à la fois doivent implémenter et éventuellement peuvent implémenter pour fournir des fonctionnalités supplémentaires.

- [Quand créer des types de projets](../../extensibility/internals/when-to-create-project-types.md)

 Permet de décider quand vous devez créer un projet de type et le moment où vous pouvez utiliser un autre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonctionnalité d’extensibilité tels que les VSPackages et éditeurs pour atteindre le même objectif.

- [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)

 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise des hiérarchies et contexte de sélection pour fournir une expérience utilisateur cohérente et simplifiée.

## <a name="related-sections"></a>Rubriques connexes
- [Sous-types de projets](../../extensibility/internals/project-subtypes.md)

 Explique comment les sous-types de projet vous permettent de personnaliser le comportement des systèmes de projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit une vue d’ensemble des projets en tant que blocs de construction de base de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Liens sont fournis vers des rubriques supplémentaires qui expliquent comment projets de contrôle de génération et compilation du code.