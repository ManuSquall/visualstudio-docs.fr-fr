---
title: "Utilisation inappropri&#233;e du mot cl&#233; &lt;mot_cl&#233;&gt; dans un module | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Utilisation inappropri&#233;e du mot cl&#233; &lt;mot_cl&#233;&gt; dans un module
Les modules n’ont pas d’instances, ne prennent pas en charge l’héritage et n’implémentent pas les interfaces. Les mots clés suivants ne s’appliquent donc pas à une déclaration de module :  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 Les seuls mots clés pris en charge dans une [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement) sont [Public](/dotnet/visual-basic/language-reference/modifiers/public) et [Friend](/dotnet/visual-basic/language-reference/modifiers/friend).  
  
 De plus, vous ne pouvez pas utiliser l’instruction [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) ni l’instruction [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) dans le bloc d’instructions du module.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42028  
  
### Pour corriger cette erreur  
  
-   Si vous prévoyez d’utiliser cet élément de programmation en tant que module, utilisez uniquement le mot clé `Public` ou `Friend` dans sa déclaration. Par défaut, un module utilise `Friend` si vous ne spécifiez pas son niveau d’accès.  
  
-   Si vous envisagez de créer des instances de cet élément de programmation, déclarez\-le en tant que classe. Vous pouvez ensuite utiliser les mots clés qui s’appliquent à une déclaration de classe.  
  
## Voir aussi  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)