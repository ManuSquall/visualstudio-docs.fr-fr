---
title: "CA2243 : Les litt&#233;raux de cha&#238;ne d&#39;attribut doivent &#234;tre correctement analys&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2243 : Les litt&#233;raux de cha&#238;ne d&#39;attribut doivent &#234;tre correctement analys&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Le paramètre de littéral de chaîne d'un attribut n'effectue pas une analyse correcte pour une URL, un GUID ou une version.  
  
## Description de la règle  
 Dans la mesure où les attributs sont dérivés de <xref:System.Attribute?displayProperty=fullName> et qu'ils sont utilisés au moment de la compilation, seules les valeurs de constante peuvent être passées à leurs constructeurs.  Les paramètres d'attribut qui doivent représenter des URL, des GUID et des versions ne peuvent pas être de type <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> et <xref:System.Version?displayProperty=fullName>, car ces types ne peuvent pas être représentés sous forme de constantes.  Ils doivent plutôt être représentés par des chaînes.  
  
 Le paramètre étant de type chaîne, il est possible qu'un paramètre mis en forme de manière incorrecte soit passé au moment de la compilation.  
  
 Cette règle utilise une heuristique de dénomination pour rechercher des paramètres qui représentent un URI \(Uniform Resource Identifier\), un identificateur global unique \(GUID\) ou une version, et vérifie que la valeur passée est correcte.  
  
## Comment corriger les violations  
 Remplacez la chaîne de paramètre par une URL, un GUID ou une version formé correctement.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre ne représente pas une URL, un GUID ou une version.  
  
## Exemple  
 L'exemple suivant indique le code de l'AssemblyFileVersionAttribute qui viole cette règle.  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 La règle est déclenchée par les éléments suivants :  
  
-   Paramètres qui contiennent la "version" et qui ne peuvent pas être convertis en System.Version.  
  
-   Paramètres qui contiennent le "guid" et qui ne peuvent pas être convertis en System.Guid.  
  
-   Paramètres qui contiennent "uri", "urn" ou "url" et qui ne peuvent pas être convertis en System.Uri.  
  
## Voir aussi  
 [CA1054 : Les paramètres Uri ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)