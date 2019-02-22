---
title: Routage des commandes dans VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5749875a440a3122a06b81ae9d721e75ded6202c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641297"
---
# <a name="command-routing-in-vspackages"></a>Routage des commandes dans VSPackages
Une commande est acheminée dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] selon le contexte dans lequel elle est exécutée. Il est acheminé à partir du contexte initial vers l’extérieur vers le contexte global.

## <a name="in-this-section"></a>Dans cette section
- [Algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md)

 Décrit l’ordre de résolution de routage de commande.

- [Disponibilité de la commande](../../extensibility/internals/command-availability.md)

 Décrit le routage des commandes.

- [Commandes et des menus qui utilisent des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Décrit les considérations sur les commandes de routage entre le code managé et COM.

## <a name="related-sections"></a>Rubriques connexes
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)

 Décrit le modèle pour comment vous pouvez déterminer le focus de contexte de sélection de l’utilisateur sur une fenêtre.

- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.