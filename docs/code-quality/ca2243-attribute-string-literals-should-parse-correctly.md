---
title: 'CA2243 : Littéraux de chaîne d’attribut doivent être analysés correctement | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0715624391b766649e48775470ed9e27f47f9613
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243 : Les littéraux de chaîne d'attribut doivent être correctement analysés
|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Paramètre de littéral de chaîne d’un attribut n’analyse pas correctement pour une URL, un GUID ou une Version.  
  
## <a name="rule-description"></a>Description de la règle  
 Étant donné que les attributs sont dérivés de <xref:System.Attribute?displayProperty=fullName>et ils sont utilisés au moment de la compilation, uniquement les valeurs de constantes peuvent être passées à leurs constructeurs. Paramètres d’attribut qui doivent représenter des URL, des GUID et des Versions ne peut pas être de type <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, et <xref:System.Version?displayProperty=fullName>, car ces types ne peut pas être représentées sous forme de constantes. Au lieu de cela, ils doivent être représentées par des chaînes.  
  
 Étant donné que le paramètre est typé en tant que chaîne, il est possible qu’un paramètre au format incorrect peut être passé au moment de la compilation.  
  
 Cette règle utilise une heuristique de dénomination pour rechercher des paramètres qui représentent un identificateur de ressource uniforme (URI), un identificateur global Unique (GUID) ou une Version et vérifie que la valeur passée est correcte.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifiez la chaîne de paramètre à une URL, GUID ou Version formée correctement.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si le paramètre ne représente pas une URL, un GUID ou une Version.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le code de l’AssemblyFileVersionAttribute qui viole cette règle.  
  
 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 La règle est déclenchée par les éléments suivants :  
  
-   Paramètres qui contiennent 'version' et ne peut pas être analysées en System.Version.  
  
-   Paramètres qui contiennent 'guid' et ne peut pas être analysées aux System.Guid.  
  
-   Paramètres qui contiennent « uri », « urn » ou « url » et ne peut pas être analysées en System.Uri.  
  
## <a name="see-also"></a>Voir aussi  
 [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)