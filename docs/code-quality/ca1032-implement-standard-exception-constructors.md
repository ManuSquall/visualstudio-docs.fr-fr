---
title: "CA1032&#160;: Impl&#233;menter des constructeurs d&#39;exception standard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1032&#160;: Impl&#233;menter des constructeurs d&#39;exception standard
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type étend <xref:System.Exception?displayProperty=fullName> et ne déclare pas tous les constructeurs requis.  
  
## Description de la règle  
 Les types d'exception doivent implémenter les constructeurs suivants :  
  
-   public NewException\(\)  
  
-   public NewException\(string\)  
  
-   public NewException\(string, Exception\)  
  
-   NewException\(SerializationInfo, StreamingContext\) protégé ou privé  
  
 Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte.  Par exemple, le constructeur avec la signature `NewException(string, Exception)` est utilisé pour créer des exceptions provoquées par d'autres exceptions.  Sans ce constructeur, vous ne pouvez ni créer, ni lever une instance de votre exception personnalisée contenant une exception interne \(imbriquée\) qui correspond à l'action que doit effectuer un code managé dans une telle situation.  Les trois premiers constructeurs d'exceptions sont publics par convention.  Le constructeur quatrième est protégé dans les classes non\-sealed, et privé dans les classes sealed.  Pour plus d'informations, consultez [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez les constructeurs manquants à l'exception, et assurez\-vous qu'ils bénéficient de l'accessibilité appropriée.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle quand la violation est provoquée par l'utilisation d'un niveau d'accès différent pour les constructeurs publics.  
  
## Exemple  
 L'exemple suivant présente un type d'exception qui enfreint cette règle, et un autre d'implémentation correcte.  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]