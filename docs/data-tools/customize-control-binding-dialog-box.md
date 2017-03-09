---
title: "Personnaliser la liaison de contr&#244;les, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Personnaliser la liaison de contrôles (boîte de dialogue)"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Personnaliser la liaison de contr&#244;les, bo&#238;te de dialogue
Utilisez la boîte de dialogue **Personnaliser la liaison de contrôles** pour spécifier les contrôles disponibles pour les éléments dans la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
 Chaque élément de la fenêtre **Sources de données** a une liste associée des contrôles qui peuvent être liés à l'élément.  Les contrôles disponibles pour chaque élément sont déterminés par le type de données de l'élément.  Chaque type de données possède une liste de contrôles associés valides définie dans cette boîte de dialogue, y compris un contrôle par défaut.  
  
 Avant de faire glisser un élément sur une aire de conception pour créer un contrôle lié aux données, vous pouvez sélectionner le contrôle à créer.  Si vous faites glisser un élément depuis la fenêtre **Sources de données** sur une aire de conception sans sélectionner de contrôle, le contrôle par défaut du type de données de l'élément sélectionné est ajouté à cette aire.  
  
 Pour plus d'informations sur la façon d'ajouter cette boîte de dialogue pour personnaliser la liste de contrôles pour les éléments de la fenêtre **Sources de données**, consultez [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Liste UIElement  
 **Type de données**  
 Affiche la liste des types que vous associez aux contrôles :  
  
-   Les tables, les entités et les objets sont représentés comme des types **\[Liste\]**.  
  
-   Les colonnes ou les propriétés publiques d'entités et d'objets sont représentés en tant que type de données réel de la colonne ou propriété dans le magasin de données sous\-jacent.  
  
-   Les objets possédant des formes définies par l'utilisateur sont représentés en tant que **\[Autre\]**.  Par exemple, si votre application possède un contrôle personnalisé qui affiche des données provenant de plusieurs propriétés d'un objet, sélectionnez le type de données **\[Autre\]** pour votre contrôle.  
  
 **Contrôles associés**  
 Affiche la liste des contrôles que vous pouvez associer à un type de données particulier.  Si vous souhaitez associer un contrôle particulier au type sélectionné dans la liste **Type de données**, activez la case à cocher correspondante.  Pour supprimer une association, désactivez la case à cocher correspondante.  Les contrôles activés apparaissent dans le menu contextuel présenté par la fenêtre **Sources de données** pour un élément du type de données associé.  
  
 Vous pouvez ajouter des contrôles à la liste en ajoutant des contrôles dotés d'un des attributs de liaison de données à la **boîte à outils**.  Pour plus d'informations, consultez [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Définir la valeur par défaut**  
 Assigne le type de contrôle sélectionné en tant que valeur par défaut pour les éléments du type de données sélectionné.  Le contrôle par défaut apparaît comme première sélection dans le menu contextuel présenté par la fenêtre **Sources de données** pour un élément.  Un seul type de contrôle peut être assigné en tant que valeur par défaut pour un type de données.  
  
 **Effacer la valeur par défaut**  
 Supprime la désignation d'un contrôle en tant que valeur par défaut pour le type de données sélectionné.  S'il n'existe aucune valeur par défaut pour le type de données sélectionné, **\[Aucun\]** apparaît comme première sélection dans le menu contextuel présenté par la fenêtre **Sources de données** pour un élément du type associé.  
  
## Voir aussi  
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)