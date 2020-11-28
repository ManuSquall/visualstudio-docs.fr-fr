---
title: Routage des commandes dans les VSPackages | Microsoft Docs
description: En savoir plus sur le routage des commandes dans les VSPackages et la façon dont les commandes sont routées en fonction du contexte dans lequel elles sont exécutées dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8168fbe3ad5ba9b1b332aebc4675ecd8e752ee7e
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305222"
---
# <a name="command-routing-in-vspackages"></a>Routage des commandes dans les VSPackages
Une commande est routée en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonction du contexte dans lequel elle est exécutée. Il est routé du contexte initial vers le contexte global.

## <a name="in-this-section"></a>Dans cette section
- [Algorithme de routage des commandes](../../extensibility/internals/command-routing-algorithm.md)

 Décrit l’ordre de résolution du routage des commandes.

- [Disponibilité des commandes](../../extensibility/internals/command-availability.md)

 Décrit le routage des commandes.

- [Commandes et menus qui utilisent des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Décrit les considérations relatives à l’acheminement des commandes entre le code managé et COM.

## <a name="related-sections"></a>Sections connexes
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)

 Décrit le modèle de la façon dont vous pouvez déterminer le focus du contexte de sélection de l’utilisateur sur une fenêtre.

- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.
