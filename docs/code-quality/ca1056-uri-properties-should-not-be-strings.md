---
title: "CA1056&#160;: Les propri&#233;t&#233;s Uri ne doivent pas &#234;tre des cha&#238;nes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1056&#160;: Les propri&#233;t&#233;s Uri ne doivent pas &#234;tre des cha&#238;nes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type déclare une propriété de type chaîne dont le nom contient "uri", "Uri", "urn", "Urn", "url" ou "Url".  
  
## Description de la règle  
 Cette règle fractionne le nom de propriété en jetons fondés sur la convention de casse Pascal et contrôle si chaque jeton est égal à "uri", "Uri", "urn", "Urn", "url" ou "Url".  En cas de correspondance, la règle considère que la propriété représente un identificateur de ressources uniformes, ou URI \(Uniform Resource Identifier\).  Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité.  La classe <xref:System.Uri?displayProperty=fullName> fournit ces services de manière sûre et sécurisée.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez la propriété en type <xref:System.Uri>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si la propriété ne représente pas une URI.  
  
## Exemple  
 L'exemple suivant affiche un type, `ErrorProne`, qui enfreint cette règle et un autre, `SaferWay`, qui la satisfait.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## Règles connexes  
 [CA1054 : Les paramètres Uri ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055 : Les valeurs de retour Uri ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234 : Passez des objets System.Uri à la place de chaînes](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)