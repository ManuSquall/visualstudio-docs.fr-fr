---
title: "CA1054&#160;: Les param&#232;tres Uri ne doivent pas &#234;tre des cha&#238;nes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1054&#160;: Les param&#232;tres Uri ne doivent pas &#234;tre des cha&#238;nes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type déclare une méthode avec un paramètre de chaîne dont le nom contient "uri", "Uri", "urn", "Urn", "url" ou "Url", et le type ne déclare aucune surcharge correspondante qui accepte un paramètre <xref:System.Uri?displayProperty=fullName>.  
  
## Description de la règle  
 Cette règle fractionne le nom de paramètres en jetons fondés sur la convention de casse mixte et contrôle si chaque jeton est égal à "uri", "Uri", "urn", "Urn", "url" ou "Url."  En cas de correspondance, la règle considère que le paramètre représente un identificateur de ressources uniformes, ou URI \(Uniform Resource Identifier\).  Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité.  Si une méthode accepte une représentation sous forme de chaîne d'un URI, une surcharge correspondante qui accepte une instance de la classe <xref:System.Uri> doit être fournie ; elle\-même fournit ces services de manière sûre et sécurisée.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez le paramètre en un type <xref:System.Uri> ; il s'agit d'une modification avec rupture.  Vous pouvez également fournir une surcharge de la méthode qui accepte un paramètre <xref:System.Uri> ; il s'agit d'une modification sans rupture.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre ne représente pas une URI.  
  
## Exemple  
 L'exemple suivant affiche un type, `ErrorProne`, qui enfreint cette règle et un autre, `SaferWay`, qui la satisfait.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## Règles connexes  
 [CA1056 : Les propriétés Uri ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055 : Les valeurs de retour Uri ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234 : Passez des objets System.Uri à la place de chaînes](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)