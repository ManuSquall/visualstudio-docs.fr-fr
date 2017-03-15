---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; sur la classe &#39;&lt;nom_classe&gt;&#39; d&#233;clare &lt;type&gt; &#39;&lt;nom_membre&gt;&#39;, ce qui provoque un conflit avec un membre du m&#234;me nom dans &lt;type&gt; &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BC42101"
ms.assetid: 001c8eaa-19b6-44fa-8056-4186ecffbda8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; sur la classe &#39;&lt;nom_classe&gt;&#39; d&#233;clare &lt;type&gt; &#39;&lt;nom_membre&gt;&#39;, ce qui provoque un conflit avec un membre du m&#234;me nom dans &lt;type&gt; &#39;&lt;nom_type&gt;&#39;
'Microsoft.VisualBasic.ComClassAttribute' sur la classe '\<nom\_classe\>' déclare \<type\> '\<nom\_membre\>', ce qui provoque un conflit avec un membre du même nom dans \<type\> '\<nom\_type\>'. Utilisez 'Microsoft.VisualBasic.ComClassAttribute\(InterfaceShadows:\=True\)' pour masquer le nom dans le '\<nom\_type\>' de base.  
  
 Une classe qui utilise un bloc d’attributs `COMClassAttribute` définit implicitement une interface portant le même nom qu’un membre de la classe de base. Dans ce cas, le nom de l’interface doit occulter le membre de la classe de base.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42101  
  
### Pour corriger cette erreur  
  
1.  Si vous souhaitez masquer le membre de la classe de base, définissez `InterfaceShadows:=True` dans le bloc d’attributs `ComClassAttribute`.  
  
2.  Dans le cas contraire, changez le nom de la classe.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [ComClassAttribute.InterfaceShadows, propriété](http://msdn.microsoft.com/fr-fr/0fae25bd-e0ba-4755-a76c-3b526b1ac795)