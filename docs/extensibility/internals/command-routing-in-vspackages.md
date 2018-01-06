---
title: Routage des commandes dans les VSPackages | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90f3d2347f8bf37173f3eb257293b71d706eb0a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="command-routing-in-vspackages"></a>Routage des commandes dans des VSPackages
Une commande est acheminée dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en fonction du contexte dans lequel elle est exécutée. À partir du contexte initial vers l’extérieur, il est acheminé vers le contexte global.  
  
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