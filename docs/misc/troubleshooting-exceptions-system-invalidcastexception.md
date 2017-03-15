---
title: "D&#233;pannage des exceptions&#160;: System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidCastException (classe)"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.InvalidCastException
Une exception <xref:System.InvalidCastException> est levée lorsqu'une défaillance se produit pendant une conversion de référence explicite. Des conversions de références sont des conversions d'un type référence à un autre. Si elles peuvent modifier le type de la référence, elles ne modifient jamais le type ou la valeur de la cible de la conversion L'exécution d'un cast des objets d'un type en un autre est souvent à l'origine de cette exception.  
  
## Conseils associés  
 **Comparez les types sources aux types de destination pour vérifier la validité de la conversion.**  
 Pour plus d'informations sur les conversions prises en charge par le système, consultez <xref:System.Convert>.  
  
## Notes  
 Pour réussir une conversion de référence explicite, la valeur source doit être Null \(`Nothing` en Visual Basic\) ou le type d'objet référencé par l'argument source doit être convertible au type de destination par une conversion de référence implicite.  
  
 Lorsqu'une application Visual Basic 6.0 avec un appel à un événement personnalisé dans un contrôle utilisateur est mise à niveau vers une version plus récente de Visual Basic et qu'elle s'exécute, cette exception peut se produire avec les informations supplémentaires : "Le cast spécifié n'est pas valide." Pour corriger cette erreur, recherchez la ligne de code suivante dans  `Form1` :  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 Puis, remplacez\-la par :  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## Voir aussi  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [Conversion de chaînes en types de données .NET Framework](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [Comment : implémenter des conversions définies par l'utilisateur entre des structs](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)