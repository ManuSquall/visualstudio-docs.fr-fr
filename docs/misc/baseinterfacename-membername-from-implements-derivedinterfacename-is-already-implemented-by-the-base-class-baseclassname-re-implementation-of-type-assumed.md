---
title: "&#39;&lt;nom_interface_base&gt;.&lt;nom_membre&gt;&#39; de &#39;implements &lt;nom_interface_d&#233;riv&#233;e&gt;&#39; est d&#233;j&#224; impl&#233;ment&#233; par la classe de base &#39;&lt;nom_classe_base&gt;&#39;. R&#233;impl&#233;mentation de &lt; type &gt; attendue. | Microsoft Docs"
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
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_interface_base&gt;.&lt;nom_membre&gt;&#39; de &#39;implements &lt;nom_interface_d&#233;riv&#233;e&gt;&#39; est d&#233;j&#224; impl&#233;ment&#233; par la classe de base &#39;&lt;nom_classe_base&gt;&#39;. R&#233;impl&#233;mentation de &lt; type &gt; attendue.
Une propriété, une procédure ou un événement dans une classe dérivée utilise une clause `Implements` qui spécifie un membre d’interface dérivé déjà implémenté sur l’interface de base dans la classe de base.  
  
 Le membre implémenté est défini par l’interface de base et hérité par l’interface dérivée. La classe de base implémente directement l’interface de base. La classe dérivée implémente l’interface dérivée et peut facilement oublier le fait que la classe de base a déjà implémenté le membre.  
  
 Une classe dérivée peut réimplémenter un membre d’interface qui est implémenté par sa classe de base. La substitution de l’implémentation de la classe de base est une procédure différente. Pour plus d’informations, consultez [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42014  
  
### Pour corriger cette erreur  
  
-   Si vous comptez réimplémenter le membre d’interface, aucune mesure n’est nécessaire. Le code de votre classe dérivée accède au membre réimplémenté, sauf si vous utilisez le mot clé [MyBase \- delete](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) pour accéder à l’implémentation de la classe de base.  
  
-   Si vous ne comptez pas réimplémenter le membre d’interface, supprimez la clause `Implements` de la déclaration de la propriété, de la procédure ou de l’événement.  
  
## Voir aussi  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [NOT IN BUILD : Implements \(mot clé\) et Implements \(instruction\)](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)