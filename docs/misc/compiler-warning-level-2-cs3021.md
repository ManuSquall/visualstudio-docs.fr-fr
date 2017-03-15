---
title: "Avertissement du compilateur (niveau&#160;2) CS3021 | Microsoft Docs"
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
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS3021
'type' n’a pas besoin d’un attribut CLSCompliant, car l’assembly n’a pas d’attribut CLSCompliant  
  
 Cet avertissement se produit si `[CLSCompliant(false)]`  apparaît sur une classe dans un assembly dont l’attribut CLSCompliant de niveau assembly n’a pas la valeur true \(c’est\-à\-dire la ligne `[assembly: CLSCompliant(true)]`\). Étant donné que l’assembly ne se déclare pas comme conforme CLS, il est inutile que son contenu se déclare comme non conforme, puisqu’il est déjà supposé être non conforme. Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
 Pour supprimer cet avertissement, supprimez l’attribut ou ajoutez l’attribut de niveau assembly.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS3021 :  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## Voir aussi  
 [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)