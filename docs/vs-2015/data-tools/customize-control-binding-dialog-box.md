---
title: Personnaliser la boîte de dialogue liaison de contrôles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4d47fe3962651db91dcfdf6e59653db539a9f44b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502878"
---
# <a name="customize-control-binding-dialog-box"></a>Personnaliser la liaison de contrôles, boîte de dialogue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez le **personnaliser la liaison de contrôle** boîte de dialogue pour spécifier quels contrôles sont disponibles pour les éléments dans le [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Chaque élément dans le **des Sources de données** fenêtre a une liste associée des contrôles qui peuvent être liés à l’élément. Les contrôles disponibles pour chaque élément sont déterminés par le type de données de l’élément. Chaque type de données possède une liste de contrôles associés valides définie dans cette boîte de dialogue, y compris un contrôle par défaut.  
  
 Avant de faire glisser un élément à une aire de conception pour créer un contrôle lié aux données, vous pouvez sélectionner le contrôle à créer. Si vous faites glisser un élément à partir de la **des Sources de données** fenêtre sur une aire de conception sans sélectionner un contrôle, le contrôle par défaut pour le type de données de l’élément sélectionné est ajouté à l’aire de conception.  
  
 Pour plus d’informations sur l’utilisation de cette boîte de dialogue pour personnaliser la liste des contrôles pour les éléments dans le **des Sources de données** fenêtre, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Type de données**  
 Affiche la liste des types que vous associez à des contrôles :  
  
-   Tables, les entités et les objets sont représentés en tant que **[liste]** types.  
  
-   Colonnes ou des propriétés publiques d’entités et les objets sont représentées en tant que type de données réel de la colonne ou une propriété dans le magasin de données sous-jacent.  
  
-   Les objets avec des formes définis par l’utilisateur sont représentés en tant que **[autre]**. Par exemple, si votre application comporte un contrôle personnalisé qui affiche les données à partir de plusieurs propriétés d’un objet, sélectionnez le **[autre]** type de données pour votre contrôle.  
  
 **Contrôles associés**  
 Affiche une liste de contrôles que vous pouvez associer à un type de données particulier. Si vous souhaitez associer un contrôle particulier avec le type de données sélectionné dans le **Type de données** , sélectionnez la case à cocher correspondante. Désactivez la case à cocher pour supprimer une association. Vérifié les contrôles apparaissent dans le menu contextuel présenté par le **des Sources de données** fenêtre pour un élément du type de données associé.  
  
 Vous pouvez ajouter des contrôles à la liste en ajoutant des contrôles qui ont une de plusieurs attributs de liaison de données pour le **boîte à outils**. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Définir par défaut**  
 Assigne le type de contrôle sélectionné à la valeur par défaut pour les éléments du type de données sélectionné. Le contrôle par défaut apparaît comme première sélection dans le menu contextuel présenté par le **des Sources de données** fenêtre pour un élément. Type de contrôle qu’un seul peut être affecté en tant que la valeur par défaut pour un type de données.  
  
 **Effacer la valeur par défaut**  
 Supprime la désignation d’un contrôle en tant que la valeur par défaut pour le type de données sélectionnée. S’il n’existe aucune valeur par défaut pour le type de données sélectionné, **[None]** apparaît comme première sélection dans le menu contextuel présenté par le **des Sources de données** fenêtre pour un élément du type associé.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)