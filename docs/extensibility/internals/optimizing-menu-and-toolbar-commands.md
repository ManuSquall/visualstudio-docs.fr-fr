---
title: "Optimisation des menus et des commandes de barre d&#39;outils | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes de menus (Visual Studio)"
  - "commandes de barres d'outils (Visual Studio)"
  - "menus (Visual Studio SDK), commandes"
  - "commandes de menu, l'implémentation"
  - "barres d'outils (Visual Studio), commandes"
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Optimisation des menus et des commandes de barre d&#39;outils
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'ajout de packages VS et leurs commandes correspondantes à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut entraîner une interface utilisateur encombrée.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Fournit des méthodes permettant de limiter la confusion des commandes de l'interface utilisateur.  
  
## Dans cette section  
 [Disposition des commandes](../../extensibility/internals/making-commands-available.md)  
 Fournit des recommandations générales pour minimiser la charger de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'interface utilisateur lorsque vous ajoutez des packages VS.  
  
 [Instructions de sélection élective](../../extensibility/internals/command-placement-guidelines.md)  
 Fournit des instructions pour l'implémentation d'un VSPackage en fonction de la taille de l'ensemble de commandes.  
  
## Rubriques connexes  
 [Commandes, Menus et barres d'outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explique comment créer une interface utilisateur qui comprend les menus, barres d'outils et les zones de liste déroulante de commande.