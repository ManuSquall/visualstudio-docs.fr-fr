---
title: "CA1057&#160;: Les surcharges d&#39;uri de cha&#238;ne appellent les surcharges de System.Uri | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057&#160;: Les surcharges d&#39;uri de cha&#238;ne appellent les surcharges de System.Uri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d'un paramètre de chaîne par un paramètre <xref:System.Uri?displayProperty=fullName>, et la surcharge qui accepte le paramètre de chaîne n'appelle pas la surcharge qui accepte le paramètre <xref:System.Uri>.  
  
## Description de la règle  
 Sachant que les surcharges diffèrent uniquement par le paramètre de chaîne\/<xref:System.Uri>, la chaîne est censée représenter un identificateur de ressources uniformes \(URI\).  Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité.  La classe <xref:System.Uri> fournit ces services de manière sûre et sécurisée.  Pour profiter des avantages de la classe <xref:System.Uri>, la surcharge de chaîne doit appeler la surcharge <xref:System.Uri> à l'aide de l'argument string.  
  
## Comment corriger les violations  
 Réimplémentez la méthode qui utilise la représentation sous forme de chaîne de l'URI, afin qu'elle crée une instance de la classe <xref:System.Uri> à l'aide de l'argument string, puis passe l'objet <xref:System.Uri> à la surcharge qui possède le paramètre <xref:System.Uri>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le paramètre de chaîne ne représente pas une URI.  
  
## Exemple  
 L'exemple suivant présente une surcharge string correctement implémentée.  
  
 [!CODE [FxCop.Design.CallUriOverload#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload#1)]  
  
## Règles connexes  
 [CA2234 : Passez des objets System.Uri à la place de chaînes](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1056 : Les propriétés Uri ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054 : Les paramètres Uri ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055 : Les valeurs de retour Uri ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)