---
title: "Routage des commandes dans les packages VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "routage des commandes"
  - "routage des commandes, Visual Studio SDK"
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Routage des commandes dans les packages VS
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Une commande est acheminée dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en fonction du contexte dans lequel elle est exécutée. À partir du contexte initial vers l'extérieur, il est acheminé vers le contexte global.  
  
## Dans cette section  
 [Algorithme de routage](../../extensibility/internals/command-routing-algorithm.md)  
 Décrit l'ordre de résolution de routage de commande.  
  
 [Disponibilité](../../extensibility/internals/command-availability.md)  
 Décrit le routage des commandes.  
  
 [Commandes et des Menus qui utilisent des assemblys PIA](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Décrit les considérations sur les commandes de routage entre le code managé et COM.  
  
## Rubriques connexes  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)  
 Décrit le modèle de la manière de déterminer le focus de contexte de sélection de l'utilisateur sur une fenêtre.  
  
 [Commandes, Menus et barres d'outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explique comment créer une interface utilisateur qui comprend les menus, barres d'outils et les zones de liste déroulante de commande.