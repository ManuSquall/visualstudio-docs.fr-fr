---
title: "CA2204 : Les littéraux doivent être correctement orthographiés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ad1fb951f17d223f248c678738070d1c5b70ae7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204 : Les littéraux doivent être correctement orthographiés
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode passe une chaîne littérale qui est utilisée dans un paramètre ou une propriété qui requiert une chaîne localisée et la chaîne littérale contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d’orthographe Microsoft.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle recherche une chaîne littérale est passée comme une valeur à un paramètre ou une propriété lorsqu’un ou plusieurs des cas suivants est vrai :  
  
-   Le <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de propriété est définie sur true.  
  
-   Le nom de paramètre ou la propriété contient « Texte », « Message » ou « Caption ».  
  
-   Le nom du paramètre de chaîne qui est passé à une méthode Console.Write ou Console.WriteLine est « value » ou « format ».  
  
 Cette règle analyse la chaîne littérale en mots, jetons de mots composés et vérifie l’orthographe de chaque mot/jeton. Pour plus d’informations sur l’algorithme d’analyse, consultez [CA1704 : les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot au dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés, consultez [Comment : personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Les mots orthographiés correctement réduisent la courbe d’apprentissage requise pour les nouvelles bibliothèques de logiciels.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)