---
title: Optimisation des menus et commandes de la barre d’outils | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c76e4f37fd77bd35526153bd86d419417a6cdb6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333124"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Optimisation des commandes de menu et de barre d’outils
L’ajout des VSPackages et leurs commandes correspondantes à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut entraîner une interface utilisateur encombrée. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Fournit des méthodes permettant de limiter la confusion de commande de l’interface utilisateur.

## <a name="in-this-section"></a>Dans cette section
- [Rendre les commandes disponibles](../../extensibility/internals/making-commands-available.md)

 Fournit des recommandations générales destinées à minimiser au rassemblement de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur lorsque vous ajoutez des VSPackages.

- [Instructions de positionnement](../../extensibility/internals/command-placement-guidelines.md)

 Fournit des recommandations spécifiques pour l’implémentation d’un VSPackage en fonction de la taille du jeu de commandes.

## <a name="related-sections"></a>Rubriques connexes
- [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.