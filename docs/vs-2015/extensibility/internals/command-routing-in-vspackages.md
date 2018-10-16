---
title: Routage des commandes dans VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ba68c04d95dfec7644a0a900134750db96c85bb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279615"
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

