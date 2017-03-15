---
title: "L’expression appelle de mani&#232;re r&#233;cursive l’op&#233;rateur conteneur &#39;&lt;symbole_op&#233;rateur&gt;&#39; | Microsoft Docs"
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
  - "BC42004"
  - "vbc42004"
helpviewer_keywords: 
  - "BC42004"
ms.assetid: a874c44a-3aec-447d-90f7-5659f1b2f5f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’expression appelle de mani&#232;re r&#233;cursive l’op&#233;rateur conteneur &#39;&lt;symbole_op&#233;rateur&gt;&#39;
Une expression contenue dans une procédure d’opérateur utilise l’opérateur qui fait l’objet d’une définition. De cette façon, la procédure d’opérateur s’appelle elle\-même en raison des types de données utilisés.  
  
 La procédure d’opérateur que vous définissez s’appellera elle\-même si elle utilise le même opérateur avec l’un des éléments suivants :  
  
-   Les mêmes opérandes pour lesquels vous définissez l’opérateur  
  
-   Les opérandes des mêmes types de données pour lesquels vous définissez l’opérateur  
  
-   Les opérandes des types de données qui s’étendent aux types de données pour lesquels vous définissez l’opérateur  
  
 Un *appel récursif* correspond à l’appel d’une procédure par elle\-même. Les appels récursifs peuvent entraîner une *boucle infinie*, dans laquelle le contrôle passe par le même jeu d’instructions à plusieurs reprises, jusqu’à ce que votre application soit arrêtée depuis l’extérieur. Si votre code ne comprend pas un ou plusieurs tests qui peuvent être utilisés pour arrêter la récursivité, vous risquez de créer une boucle infinie.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42004  
  
### Pour corriger cette erreur  
  
-   Si votre logique nécessite que la procédure d’opérateur s’appelle elle\-même, veillez à tester au moins une condition qui doit se produire à un moment donné et utilisez ce test pour arrêter les appels récursifs.  
  
-   Si votre logique ne nécessite pas que la procédure d’opérateur s’appelle elle\-même, supprimez les appels récursifs ou remplacez\-les par des instructions qui n’appellent pas leur propre procédure.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)