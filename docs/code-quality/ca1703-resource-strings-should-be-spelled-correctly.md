---
title: "CA1703&#160;: L&#39;orthographe des cha&#238;nes de ressources doit &#234;tre correcte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1703&#160;: L&#39;orthographe des cha&#238;nes de ressources doit &#234;tre correcte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.  
  
## Description de la règle  
 Cette règle analyse la chaîne de ressource en des mots \(jetons de mots composés\) et vérifie l'orthographe de chaque mot\/jeton.  Pour plus d'informations sur l'algorithme d'analyse, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 La version anglaise \(en\) du vérificateur d'orthographe est utilisée par défaut.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, utilisez des mots complets épelés correctement ou ajoutez les mots à un dictionnaire personnel.  Pour plus d'informations sur l'utilisation de dictionnaires personnels, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Les mots épelés correctement réduisent la durée requise pour apprendre les nouvelles bibliothèques de logiciels.  
  
## Règles connexes  
 [CA1701: La casse des mots composés de chaînes de ressources doit être correcte](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)