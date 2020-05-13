---
title: Hiérarchies et Sélections (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708138"
---
# <a name="hierarchies-and-selection"></a>Hiérarchies et sélection
Lorsque vous [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]personnalisez, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous devez comprendre comment gère les hiérarchies telles que les projets et comment il utilise le contexte de sélection pour déterminer ce qui est affiché à l’utilisateur. Cette section traite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des concepts de hiérarchies et de sélection.

## <a name="in-this-section"></a>Contenu de cette section
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Décrit les hiérarchies de projet et le concept général des hiérarchies.

- [Sélection et monnaie dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) conserve des informations sur les objets actuellement actifs de l’utilisateur et permet à VSPackages de suivre la monnaie.

- [Objets contextuelles de sélection](../../extensibility/internals/selection-context-objects.md)

 Discute du modèle pour savoir comment vous pouvez déterminer le contexte de sélection de l’utilisateur se concentrer sur une fenêtre.

- [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)

 Discute de la façon [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dont les fonctionnalités disponibles sont basées sur le contexte de sélection actuel de l’utilisateur et le contexte global de l’IDE.

## <a name="related-sections"></a>Sections connexes
- [Architecture de types de projets](../../extensibility/internals/project-types-architecture.md)

 Fournit des informations techniques détaillées sur les types de projets.
