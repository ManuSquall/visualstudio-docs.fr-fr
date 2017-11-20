---
title: "CA1802 : Utilisez des littéraux lorsque nécessaire | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 66ee20e099de0206664390623b7a50c5fec723a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802 : Utilisez des littéraux lorsque nécessaire
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un champ est déclaré `static` et `readonly` (`Shared` et `ReadOnly` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) et est initialisé avec une valeur qui est calculable à la compilation.  
  
## <a name="rule-description"></a>Description de la règle  
 La valeur d’un `static``readonly` champ est calculé à l’exécution lorsque le constructeur statique du type déclarant est appelé. Si le `static``readonly` champ est initialisé lorsqu’il est déclaré et un constructeur statique n’est pas déclaré explicitement, le compilateur émet un constructeur statique pour initialiser le champ.  
  
 La valeur d’un `const` champ est calculé au moment de la compilation et stocké dans les métadonnées, ce qui augmente les performances d’exécution lorsqu’elle est comparée à une `static``readonly` champ.  
  
 La valeur assignée au champ ciblé étant calculable à la compilation, remplacez la déclaration par un `const` afin que la valeur est calculée au moment de la compilation plutôt qu’à l’exécution.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le `static` et `readonly` modificateurs avec le `const` modificateur.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle, ou désactiver la règle, si les performances ne sont pas posant problème.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente un type, `UseReadOnly`, qui enfreint la règle et un type, `UseConstant`, qui satisfait à la règle.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]