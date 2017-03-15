---
title: "Erreur du compilateur CS0265 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0265"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0265"
ms.assetid: d43d19c2-8a66-4bb1-95a0-557b0a29bce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0265
Les déclarations partielles de 'type' ont des contraintes incohérentes pour le paramètre de type 'paramètre\_type'  
  
 Cette erreur se produit lorsque vous définissez une classe générique comme classe partielle, que ses définitions partielles se trouvent à plusieurs emplacements et que les contraintes sur le type générique sont incohérentes ou différentes à deux ou plusieurs emplacements. Si vous spécifiez les contraintes à plusieurs emplacements, elles doivent toutes être identiques. La solution la plus simple consiste à spécifier les contraintes à un seul emplacements et à les omettre partout ailleurs. Pour plus d’informations, consultez [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) et [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
 Le code suivant génère l’erreur CS0265.  
  
## Exemple  
 Dans ce code, les définitions de classe partielles se trouvent toutes dans un seul fichier, mais elles peuvent également être réparties sur plusieurs fichiers.  
  
```  
// CS0265.cs public class GenericsErrors { interface IFace1 { } interface IFace2 { } partial class PartialBadBounds<T> where T : IFace1 { } // CS0265 partial class PartialBadBounds<T> where T : IFace2 { } }  
```