---
title: "CA2204 : Les litt&#233;raux doivent &#234;tre correctement orthographi&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2204 : Les litt&#233;raux doivent &#234;tre correctement orthographi&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode passe une chaîne littérale qui est utilisée dans un paramètre ou propriété qui requiert une chaîne localisée et la chaîne littérale contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.  
  
## Description de la règle  
 Cette règle contrôle une chaîne littérale passée comme valeur à un paramètre ou une propriété lorsqu'un ou plusieurs des cas suivants se vérifient :  
  
-   L'attribut <xref:System.ComponentModel.LocalizableAttribute> du paramètre ou de la propriété a la valeur true.  
  
-   Le paramètre ou le nom de propriété contient "Text", "Message" ou "Caption".  
  
-   Le nom du paramètre de chaîne passé à une méthode Console.Write ou Console.WriteLine est "value" ou "format".  
  
 Cette règle analyse la chaîne littérale en mots en générant des jetons de mots composés et vérifie l'orthographe de chaque mot\/jeton.  Pour plus d'informations sur l'algorithme d'analyse, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 La version anglaise \(en\) du vérificateur d'orthographe est utilisée par défaut.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, corrigez l'orthographe du mot ou ajoutez le mot à un dictionnaire personnel.  Pour plus d'informations sur l'utilisation de dictionnaires personnels, consultez [Comment : personnaliser le dictionnaire d’analyse du code](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md).  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Les mots épelés correctement réduisent la durée d'apprentissage requise pour les nouvelles bibliothèques de logiciels.  
  
## Règles connexes  
 [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703 : L'orthographe des chaînes de ressources doit être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)