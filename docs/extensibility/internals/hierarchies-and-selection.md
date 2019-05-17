---
title: Hiérarchies et sélection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 741d61f4f3a62638e56aabb1f62f97aac4519d0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861011"
---
# <a name="hierarchies-and-selection"></a>Hiérarchies et sélection
Lorsque vous personnalisez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez comprendre comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère les hiérarchies telles que les projets et comment il utilise le contexte de sélection pour déterminer ce qui est affiché à l’utilisateur. Cette section décrit les concepts de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hiérarchies et sélection.

## <a name="in-this-section"></a>Dans cette section
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Décrit le concept général de hiérarchies et les hiérarchies de projet.

- [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Décrit comment la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) conserve les informations sur les objets actuellement actif de l’utilisateur et permet d’effectuer le suivi de la devise VSPackages.

- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)

 Décrit le modèle pour comment vous pouvez déterminer le focus de contexte de sélection de l’utilisateur sur une fenêtre.

- [Vos commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)

 Explique comment les fonctionnalités disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est basé sur le contexte de sélection actuel et le contexte IDE global de l’utilisateur.

## <a name="related-sections"></a>Rubriques connexes
- [Architecture des types de projet](../../extensibility/internals/project-types-architecture.md)

 Fournit des informations techniques détaillées sur les types de projets.