---
title: "Erreur du compilateur CS2021 | Microsoft Docs"
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
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2021
Le nom de fichier 'file' est trop long ou n’est pas valide  
  
 Tous les noms de fichiers passés au compilateur C\# ne doivent pas être plus longs que `_MAX_PATH` \(défini dans un fichier d’en\-tête Windows\). Le compilateur génère cette erreur dans les situations suivantes :  
  
-   Un nom de fichier \(chemin inclus\) est plus long que `_MAX_PATH`.  
  
-   Le nom du fichier contient des caractères non valides.  
  
-   Le nom du fichier contient des caractères génériques alors que ceux\-ci n’y sont pas autorisés \(par exemple, dans les noms de fichiers de ressources\).