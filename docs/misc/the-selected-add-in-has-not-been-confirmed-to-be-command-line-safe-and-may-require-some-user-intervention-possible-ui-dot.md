---
title: "The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI). | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0031"
  - "vs.message.VB_E_IDWADDINCMDLINE"
ms.assetid: 19dd24d4-b0f5-4c92-9005-aad48ffda7d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI).
Cette erreur se produit généralement quand un complément a été sélectionné pour être utilisé à partir de l'invite de commande \(commandes MS\-DOS\) alors qu'il n'est pas répertorié comme pouvant être utilisé avec la ligne de commande.  Le complément peut afficher une interface utilisateur susceptible de perturber le fonctionnement de la ligne de commande.  
  
### Pour corriger cette erreur  
  
1.  Dans le menu **Outils**, choisissez **Gestionnaire de compléments**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de compléments**, désactivez la case à cocher **Ligne de commande** du complément.  
  
## Voir aussi  
 [Comment : contrôler des compléments avec le Gestionnaire de compléments](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md)   
 [Comment : créer un complément](../Topic/How%20to:%20Create%20an%20Add-In.md)