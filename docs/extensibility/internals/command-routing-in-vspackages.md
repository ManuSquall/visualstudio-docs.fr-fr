---
title: Routage des commandes dans les VSPackages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58be191a3b7a2256d0883e313f77b264f6be4d69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135801"
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