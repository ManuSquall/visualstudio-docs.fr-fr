---
title: 'CA1047 : Ne pas déclarer les membres protégés dans les types sealed | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b4a8ec92b79fb7df72ebd1984fc49f3cf4396cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047 : Ne pas déclarer les membres protégés dans les types sealed
|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Category|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type public est `sealed` (`NotInheritable` en Visual basic) et déclare un membre protégé ou un type imbriqué protégé. Cette règle ne rapporte pas de violations de <xref:System.Object.Finalize%2A> , ces méthodes doivent suivre ce modèle.  
  
## <a name="rule-description"></a>Description de la règle  
 Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, vous ne peut pas hériter d’un type sealed, ce qui signifie que protégés des méthodes sur les types sealed ne peut pas être appelée.  
  
 Le compilateur c# émet un avertissement de cette erreur.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le niveau d’accès du membre privé ou rendez le type héritable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui viole cette règle.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]