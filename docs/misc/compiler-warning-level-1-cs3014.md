---
title: "Avertissement du compilateur (niveau&#160;1) CS3014 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS3014
'member' n’a pas besoin d’un attribut CLSCompliant, car l’assembly n’a pas d’attribut CLSCompliant  
  
 Dans un fichier de code source dans lequel la conformité CLS \(Common Language Specification\) n’a pas été spécifiée, une construction du fichier a été marquée comme étant conforme CLS. Cette opération n’est pas autorisée. Pour résoudre cet avertissement, ajoutez un attribut de conformité CLS de niveau assembly au fichier \(dans l’exemple qui suit, supprimez les marques de commentaire sur la ligne qui contient l’attribut de niveau assembly\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3014 :  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```