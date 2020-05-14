---
title: Project Types Architecture (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706318"
---
# <a name="project-types-architecture"></a>Architecture des types de projets
Cette section contient des informations détaillées [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sur l’architecture des types de projets dans .

## <a name="in-this-section"></a>Dans cette section
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)

 Répertorie les services qu’un type de projet peut consommer et les interfaces qu’il doit mettre en œuvre.

- [Principaux composants d’un modèle de projet](../../extensibility/internals/project-model-core-components.md)

 Décrit les types de projets d’interfaces à la fois doit implémenter et peut implémenter d’option pour fournir des fonctionnalités supplémentaires.

- [Quand créer des types de projets](../../extensibility/internals/when-to-create-project-types.md)

 Vous aide à décider quand vous devez créer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un type de projet et quand vous pouvez utiliser une autre fonctionnalité d’extensibility comme VSPackages et éditeurs pour atteindre le même objectif.

- [Hiérarchies et sélection](../../extensibility/internals/hierarchies-and-selection.md)

 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise les hiérarchies et le contexte de sélection pour fournir une expérience utilisateur cohérente et simplifiée.

## <a name="related-sections"></a>Sections connexes
- [Sous-types de projets](../../extensibility/internals/project-subtypes.md)

 Explique comment les sous-types de projet vous permettent [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]personnaliser le comportement des systèmes de projet de et .

- [Types de projets](../../extensibility/internals/project-types.md)

 Fournit un aperçu des projets comme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éléments de base de l’environnement de développement intégré (IDE). Des liens sont fournis à d’autres sujets qui expliquent comment les projets contrôlent la construction et la compilation du code.
