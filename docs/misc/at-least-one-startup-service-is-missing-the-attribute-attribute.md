---
title: "At least one startup service is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_ss_attrib"
ms.assetid: 987c42dc-4394-4b07-b7fa-a8e7afc6fdfb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one startup service is missing the &#39;attribute&#39; attribute
Un service de démarrage nécessite l'attribut ID, qui est introuvable dans un élément `<Service>`.  Par exemple :  
  
```  
<Service ID="{0000-0000-0000-00000000-000000000000}"/>  
```  
  
 Ceci indique que le fichier projet est endommagé.  
  
 La cause la plus probable de cette erreur est la modification manuelle du fichier projet.  
  
 **Pour corriger cette erreur**  
  
-   Enregistrez le fichier projet.  
  
     La section défectueuse ne sera pas écrite et cette erreur ne se produira pas à la prochaine ouverture du projet.  
  
## Voir aussi  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)