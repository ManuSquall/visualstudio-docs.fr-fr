---
title: Hiérarchies et sélection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d59a5160b5c20a3243426eaf1fda4b72e58e93
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328877"
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