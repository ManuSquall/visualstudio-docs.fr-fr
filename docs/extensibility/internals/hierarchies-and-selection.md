---
title: Hiérarchies et sélection | Microsoft Docs
description: Découvrez comment Visual Studio gère les hiérarchies telles que les projets, et comment il utilise le contexte de sélection pour déterminer ce qui est affiché à l’utilisateur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 927d55a5217699222aadcbcb7a3526f22e010e8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074728"
---
# <a name="hierarchies-and-selection"></a>Hiérarchies et sélection
Lorsque vous personnalisez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous devez comprendre comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère les hiérarchies telles que les projets et comment il utilise le contexte de sélection pour déterminer ce qui est affiché à l’utilisateur. Cette section décrit les concepts de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hiérarchies et de sélection.

## <a name="in-this-section"></a>Dans cette section
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Décrit les hiérarchies de projet et le concept général des hiérarchies.

- [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Décrit comment l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) gère les informations sur les objets actuellement actifs de l’utilisateur et permet aux VSPackages de suivre la devise.

- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)

 Décrit le modèle de la façon dont vous pouvez déterminer le focus du contexte de sélection de l’utilisateur sur une fenêtre.

- [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)

 Explique comment la fonctionnalité disponible dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est basée sur le contexte de sélection actuel de l’utilisateur et le contexte de l’IDE global.

## <a name="related-sections"></a>Sections connexes
- [Architecture des types de projets](../../extensibility/internals/project-types-architecture.md)

 Fournit des informations techniques détaillées sur les types de projets.
