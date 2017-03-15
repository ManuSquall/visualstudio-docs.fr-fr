---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type &#224; partir de ces arguments, car ils ne sont pas convertis vers le m&#234;me type | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36659"
  - "bc36659"
  - "vbc36656"
  - "bc36656"
helpviewer_keywords: 
  - "BC36659"
  - "BC36656"
ms.assetid: 0aa809da-3b44-4d78-b3c5-0a148bdf7ce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type &#224; partir de ces arguments, car ils ne sont pas convertis vers le m&#234;me type
Impossible de déduire le ou les types de données du ou des paramètres de type à partir de ces arguments, car ils ne sont pas convertis vers le même type. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Cette erreur se produit quand la résolution de surcharge a échoué. Elle entraîne l’affichage d’un message subordonné qui indique pourquoi un candidat de surcharge particulier a été éliminé. L’erreur explique que le compilateur ne peut pas utiliser l’inférence de type pour rechercher des types de données pour les paramètres de type qui sont compatibles avec les arguments.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Pour plus d’informations et d’exemples, consultez [Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode '\<nom\_méthode\>' à partir de ces arguments, car ils ne sont pas convertis vers le même type](../Topic/Data%20type\(s\)%20of%20the%20type%20parameter\(s\)%20in%20method%20'%3Cmethodname%3E'%20cannot%20be%20inferred%20from%20these%20arguments%20because%20they%20do%20not%20convert%20to%20the%20same%20type.md).  
  
 **ID d’erreur :** BC36659 et BC36656  
  
## Voir aussi  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)