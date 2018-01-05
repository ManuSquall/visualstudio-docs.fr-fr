---
title: "CA1721 : Les noms de propriétés ne doivent pas correspondre aux méthodes get | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb0a1b45276e6563ab645100377dec25a9060e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Le nom d’un membre public ou protégé commence par 'Get' et sinon correspond au nom d’une propriété publique ou protégée. Par exemple, un type qui contient une méthode nommée 'GetColor' et une propriété nommée 'Color' enfreint cette règle.  
  
## <a name="rule-description"></a>Description de la règle  
 Méthodes Get doivent avoir des noms distinguant clairement leur fonction.  
  
 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifier le nom afin qu’il ne corresponde pas le nom d’une méthode qui est précédé de 'Get'.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
> [!NOTE]
>  Cet avertissement peut être exclu si la méthode Get est causée par l’implémentation d’interface IExtenderProvider.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient une méthode et une propriété qui enfreignent cette règle.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)