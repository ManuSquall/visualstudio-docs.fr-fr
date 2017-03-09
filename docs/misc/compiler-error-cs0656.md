---
title: "Erreur du compilateur CS0656 | Microsoft Docs"
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
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0656
Membre requis par le compilateur 'membre.objet' manquant  
  
 Il existe l’un des problèmes suivants :  
  
-   Votre installation du common language runtime est endommagée.  
  
-   Il existe une référence à un assembly qui définit un type se trouvant aussi dans le common language runtime. Or, le type de votre assembly n’est pas défini comme l’attend le compilateur C\#.  
  
 Vérifiez vos références pour être certain que vous utilisez la bonne version du common language runtime.