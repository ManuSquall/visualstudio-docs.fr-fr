---
title: Itinéraire de commande dans VSPackages (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709553"
---
# <a name="command-routing-in-vspackages"></a>Itinéraire de commande dans VSPackages
Une commande est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] acheminée en fonction du contexte dans lequel elle est exécutée. Il est acheminé du contexte initial vers le contexte mondial.

## <a name="in-this-section"></a>Contenu de cette section
- [Algorithme de routage de commande](../../extensibility/internals/command-routing-algorithm.md)

 Décrit l’ordre de résolution de l’itinéraire de commande.

- [Disponibilité de commande](../../extensibility/internals/command-availability.md)

 Discute de l’itinéraire de commande.

- [Commandes et menus qui utilisent des assemblages interop](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Discute des considérations relatives à l’acheminement des commandes entre code géré et COM.

## <a name="related-sections"></a>Sections connexes
- [Objets contextuelles de sélection](../../extensibility/internals/selection-context-objects.md)

 Discute du modèle pour savoir comment vous pouvez déterminer le contexte de sélection de l’utilisateur se concentrer sur une fenêtre.

- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.
