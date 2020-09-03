---
title: Hiérarchies et sélection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0e38c2cea464abded5ecf6ee2c8ac087868b07e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708138"
---
# <a name="hierarchies-and-selection"></a>Hiérarchies et sélection
Lorsque vous personnalisez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous devez comprendre comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère les hiérarchies telles que les projets et comment il utilise le contexte de sélection pour déterminer ce qui est affiché à l’utilisateur. Cette section décrit les concepts de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hiérarchies et de sélection.

## <a name="in-this-section"></a>Contenu de cette section
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
