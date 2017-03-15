---
title: "Proc&#233;dure&#160;: activer et d&#233;sactiver la pluralisation (Concepteur O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: activer et d&#233;sactiver la pluralisation (Concepteur O/R)
Par défaut, lorsque vous faites glisser des objets de base de données dont le nom finit par s ou ies de l'**Explorateur de serveurs**\/**Explorateur de bases de données** vers le [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md), les noms des classes d'entité générées sont mis au singulier.C'est pour insister sur le fait que la classe d'entité instanciée mappe à un enregistrement unique de données.Par exemple, l'ajout d'une table Customers au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] génère une classe d'entité nommée Customer parce que la classe gérera les données d'un seul client.  
  
> [!NOTE]
>  Par défaut, la pluralisation est activée uniquement dans la version de langue anglaise de Visual Studio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour activer et désactiver la pluralisation  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options**, développez **Outils de base de données**.  
  
> [!NOTE]
>  Sélectionnez **Afficher tous les paramètres** si le nœud **Outils de base de données** n'est pas visible.  
  
1.  Cliquez sur **Concepteur O\/R**.  
  
2.  Affecter à **Pluralisation des noms** la valeur **Enabled** \= **False** pour obliger le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] à ne pas modifier les noms de classes.  
  
3.  Affectez à **Pluralisation des noms** la valeur **Enabled** \= **True** pour appliquer des règles de pluralisation aux noms de classes d'objets ajouté au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)