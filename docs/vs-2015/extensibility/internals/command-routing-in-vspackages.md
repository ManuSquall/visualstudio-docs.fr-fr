---
title: Routage des commandes dans VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 954d3f25a425652d8adcb31bd36fab06de0d04d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195083"
---
# <a name="command-routing-in-vspackages"></a>Routage des commandes dans VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une commande est acheminée dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] selon le contexte dans lequel elle est exécutée. Il est acheminé à partir du contexte initial vers l’extérieur vers le contexte global.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Algorithme de routage](../../extensibility/internals/command-routing-algorithm.md)  
 Décrit l’ordre de résolution de routage de commande.  
  
 [Disponibilité](../../extensibility/internals/command-availability.md)  
 Décrit le routage des commandes.  
  
 [Commandes et menus utilisant des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Décrit les considérations sur les commandes de routage entre le code managé et COM.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)  
 Décrit le modèle pour comment vous pouvez déterminer le focus de contexte de sélection de l’utilisateur sur une fenêtre.  
  
 [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.
