---
title: 'CA2213 : Les champs pouvant être supprimés doivent l’être'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1838d7e57b841c932d95006d1ff33972dd7a1a1f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231612"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213 : Les champs pouvant être supprimés doivent l’être

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> déclare des champs de types qui implémentent <xref:System.IDisposable>également. La <xref:System.IDisposable.Dispose%2A> méthode du champ n’est pas appelée par la <xref:System.IDisposable.Dispose%2A> méthode du type déclarant.

## <a name="rule-description"></a>Description de la règle

Un type est responsable de la suppression de toutes ses ressources non managées. La règle CA2213 vérifie si un type jetable (autrement dit, un type qui implémente <xref:System.IDisposable>) `T` déclare un champ `F` qui est une instance d’un type `FT`jetable. Pour chaque champ `F` auquel un objet créé localement est assigné dans les méthodes ou les initialiseurs du type `T`conteneur, la règle tente de localiser un appel à `FT.Dispose`. La règle recherche les méthodes appelées `T.Dispose` par et un niveau plus bas (autrement dit, les méthodes appelées par les `T.Dispose`méthodes appelées par).

> [!NOTE]
> À part les [cas particuliers](#special-cases), la règle CA2213 se déclenche uniquement pour les champs auxquels un objet jetable créé localement est assigné dans les méthodes et les initialiseurs du type conteneur. Si l’objet est créé ou assigné en dehors de `T`type, la règle n’est pas déclenchée. Cela réduit le bruit dans les cas où le type conteneur ne possède pas la responsabilité de la suppression de l’objet.

### <a name="special-cases"></a>Cas particuliers

La règle CA2213 peut également se déclencher pour les champs des types suivants, même si l’objet auquel elles sont affectées n’est pas créé localement :

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Passer un objet de l’un de ces types à un constructeur, puis l’assigner à un champ indique un *transfert de propriété dispose* vers le type nouvellement construit. Autrement dit, le type nouvellement construit est désormais responsable de la suppression de l’objet. Si l’objet n’est pas supprimé, une violation de CA2213 se produit.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur des champs qui sont des types qui <xref:System.IDisposable>implémentent.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle dans les cas suivants :

- Le type avec indicateur n’est pas responsable de la libération de la ressource détenue par le champ (autrement dit, le type n’a pas la *propriété dispose*)
- L’appel à <xref:System.IDisposable.Dispose%2A> se produit à un niveau d’appel plus profond que le contrôle de la règle

## <a name="example"></a>Exemple

L’extrait de code suivant montre `TypeA` un type qui <xref:System.IDisposable>implémente.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

L’extrait de code suivant montre `TypeB` un type qui viole la règle CA2213 en déclarant `aFieldOfADisposableType` un champ comme type jetable`TypeA`() et n' <xref:System.IDisposable.Dispose%2A> appelant pas sur le champ.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Pour corriger la violation, appelez `Dispose()` sur le champ jetable :

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)