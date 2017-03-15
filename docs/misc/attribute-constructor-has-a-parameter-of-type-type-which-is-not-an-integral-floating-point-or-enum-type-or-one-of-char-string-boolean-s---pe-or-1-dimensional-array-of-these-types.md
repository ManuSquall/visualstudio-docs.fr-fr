---
title: "Le constructeur d’attribut a un param&#232;tre de type &#39;&lt;type&gt;&#39;, qui n’est pas un type int&#233;gral, virgule flottante ni Enum, ni encore Char, String, Boolean, System.Type ou un tableau unidimensionnel de ces types | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le constructeur d’attribut a un param&#232;tre de type &#39;&lt;type&gt;&#39;, qui n’est pas un type int&#233;gral, virgule flottante ni Enum, ni encore Char, String, Boolean, System.Type ou un tableau unidimensionnel de ces types
Une définition d’attribut personnalisée comprend un constructeur qui spécifie un type de données non valide pour un paramètre. Les attributs peuvent uniquement accepter certains types de données en tant que paramètres, car seuls ces types peuvent être sérialisés dans les métadonnées de l’assembly.  
  
 **ID d’erreur :** BC30045  
  
### Pour corriger cette erreur  
  
1.  Remplacez le type de données du paramètre par `Byte`, `Short`, `Integer`, `Long`, `Single`, `Double`, `Char`, `String`, `Boolean`, `System.Type` ou par un type d’énumération.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs personnalisés en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)