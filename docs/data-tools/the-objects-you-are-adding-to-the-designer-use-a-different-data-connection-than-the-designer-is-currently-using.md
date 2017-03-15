---
title: "Les objets que vous ajoutez au concepteur utilisent une connexion de donn&#233;es diff&#233;rente du concepteur en cours d&#39;utilisation | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Les objets que vous ajoutez au concepteur utilisent une connexion de donn&#233;es diff&#233;rente du concepteur en cours d&#39;utilisation
Les objets que vous ajoutez au concepteur utilisent une connexion de données différente du concepteur en cours d'utilisation.Voulez\-vous remplacer la connexion utilisée par le concepteur ?  
  
 Lorsque vous ajoutez des éléments au [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), tous les éléments utilisent une connexion de données partagée.\(L'aire de conception représente le <xref:System.Data.Linq.DataContext> qui utilise une connexion unique pour tous les objets sur l'aire.\) Si vous ajoutez un objet au concepteur qui utilise une connexion de données différente de la connexion de données qui est actuellement utilisée par le concepteur, ce message apparaît.Pour résoudre cette erreur, vous pouvez maintenir la connexion existante.Dans ce cas, l'objet sélectionné n'est pas ajouté.Vous pouvez également choisir d'ajouter l'objet et de réinitialiser la connexion <xref:System.Data.Linq.DataContext> à la nouvelle connexion.  
  
> [!NOTE]
>  Si vous cliquez sur **Oui**, toutes les classes d'entité sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sont mappées à la nouvelle connexion.  
  
### Pour remplacer la connexion existante par la connexion qu'utilise l'objet sélectionné  
  
-   Cliquez sur **Oui**.  
  
     L'objet sélectionné est ajouté au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] et DataContext.Connection a pour valeur la nouvelle connexion.  
  
### Pour continuer d'utiliser la connexion existante et annuler l'ajout de l'objet sélectionné  
  
-   Cliquez sur **Non**.  
  
     L'action est annulée.DataContext.Connection conserve la connexion existante.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)