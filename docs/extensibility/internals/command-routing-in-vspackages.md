---
title: Routage des commandes dans les VSPackages | Microsoft Docs
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
ms.openlocfilehash: 957ddcca46365a882609c15c96d666c2848ace6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709553"
---
# <a name="command-routing-in-vspackages"></a>Routage des commandes dans les VSPackages
Une commande est routée en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonction du contexte dans lequel elle est exécutée. Il est routé du contexte initial vers le contexte global.

## <a name="in-this-section"></a>Contenu de cette section
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
