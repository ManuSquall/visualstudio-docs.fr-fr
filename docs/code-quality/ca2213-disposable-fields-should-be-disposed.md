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
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804999"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213 : Les champs pouvant être supprimés doivent l’être

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> déclare des champs qui sont des types qui implémentent également <xref:System.IDisposable>. Le <xref:System.IDisposable.Dispose%2A> méthode du champ n’est pas appelée par le <xref:System.IDisposable.Dispose%2A> méthode du type déclarant.

## <a name="rule-description"></a>Description de la règle

Un type est chargé de se débarrasser de toutes ses ressources non managées. Règle CA2213 vérifie si un type jetable (autrement dit, celui qui implémente <xref:System.IDisposable>) `T` déclare un champ `F` qui est une instance d’un type jetable `FT`. Pour chaque champ `F` qui a assigné un objet créé localement dans les méthodes ou les initialiseurs du type conteneur `T`, la règle essaie de localiser un appel à `FT.Dispose`. La règle recherche les méthodes appelées par `T.Dispose` et un niveau inférieur (autrement dit, les méthodes appelées par les méthodes appelées par `T.Dispose`).

> [!NOTE]
> Autre que le [cas spéciaux](#special-cases), règle se déclenche CA2213 uniquement pour les champs qui sont affectés à un objet supprimable localement créé dans les initialiseurs d’objets et les méthodes du type conteneur. Si l’objet est créé ou affecté en dehors de type `T`, la règle ne se déclenche pas. Cela réduit le bruit dans les cas où le type conteneur ne possède pas la responsabilité de suppression de l’objet.

### <a name="special-cases"></a>Cas particuliers

CA2213 de règle peut également se déclencher pour les champs des types suivants même si l’objet qu'auquel elles sont affectées n’est pas créé localement :

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Transmission d’un objet d’un de ces types à un constructeur et en l’attribuant à un champ indiquent un *dispose de transfert de la propriété* pour le type qui vient d’être construit. Autrement dit, le type nouvellement construit est désormais responsable de suppression de l’objet. Si l’objet n’est pas supprimé, une violation de CA2213 se produit.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur les champs qui sont des types qui implémentent <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si :

- Le type avec indicateur n’est pas chargé de libérer la ressource détenue par le champ (autrement dit, le type n’a pas *dispose de la propriété*)
- L’appel à <xref:System.IDisposable.Dispose%2A> se produit à un niveau plus profond appelant que la règle de contrôle

## <a name="example"></a>Exemple

L’extrait de code suivant illustre un type `TypeA` qui implémente <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

L’extrait de code suivant illustre un type `TypeB` qui viole la règle CA2213 en déclarant un champ `aFieldOfADisposableType` comme un type jetable (`TypeA`) sans appeler <xref:System.IDisposable.Dispose%2A> sur le champ.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)