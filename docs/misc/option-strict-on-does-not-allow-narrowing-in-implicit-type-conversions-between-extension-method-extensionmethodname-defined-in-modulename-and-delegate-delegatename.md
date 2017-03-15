---
title: "Option Strict On n’autorise pas les conversions restrictives lors des conversions de types implicites entre la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode_extension&gt;&#39; d&#233;finie dans &#39;&lt;nom_module&gt;&#39; et le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n’autorise pas les conversions restrictives lors des conversions de types implicites entre la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode_extension&gt;&#39; d&#233;finie dans &#39;&lt;nom_module&gt;&#39; et le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Quand `Option Strict` est On, vous ne pouvez pas avoir une conversion restrictive à partir du type de données d’un paramètre dans un délégué vers le paramètre correspondant d’une méthode d’extension assignée à une variable de ce type de délégué. Le type de données du paramètre de délégué doit s’étendre au type de données de la méthode d’extension.  
  
 **ID d’erreur :** BC36709  
  
### Pour corriger cette erreur  
  
-   Modifiez le type de données du paramètre dans le délégué ou la méthode d’extension pour que la relation d’étendue nécessaire existe.  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NOT IN BUILD : Délégués et opérateur AddressOf](http://msdn.microsoft.com/fr-fr/7b2ed932-8598-4355-b2f7-5cedb23ee86f)