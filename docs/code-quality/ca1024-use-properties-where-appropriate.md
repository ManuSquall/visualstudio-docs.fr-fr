---
title: 'CA1024 : Utiliser les propriétés lorsque cela est approprié'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03318241206b812f4ffb57dddfc6b4f021d600f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024 : Utiliser les propriétés lorsque cela est approprié
|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée a un nom qui commence par `Get`ne prend aucun paramètre et retourne une valeur qui n’est pas un tableau.

## <a name="rule-description"></a>Description de la règle
 Dans la plupart des cas, les propriétés représentent des données et les méthodes effectuent des actions. Propriétés sont accessibles comme des champs, ce qui les rend plus faciles à utiliser. Une méthode est un bon candidat pour devenir une propriété si une de ces conditions est présente :

-   N’accepte aucun argument et retourne les informations d’état d’un objet.

-   Accepte un argument unique pour définir une partie de l’état d’un objet.

 Propriétés doivent se comporter comme si elles étaient des champs ; Si la méthode ne peut pas, il ne doit pas être modifié à une propriété. Les méthodes sont meilleures que les propriétés dans les situations suivantes :

-   La méthode effectue une opération de longue durée. La méthode est perçue comme plus lente que le temps nécessaire pour définir ou obtenir la valeur d’un champ.

-   La méthode effectue une conversion. L’accès à un champ ne retourne pas une version convertie des données qu’elle stocke.

-   La méthode Get a un effet secondaire observable. La récupération de la valeur d’un champ ne produit pas d’effets secondaires.

-   L’ordre d’exécution est important. Définition de la valeur d’un champ ne repose pas sur l’occurrence d’autres opérations.

-   Appel de la méthode deux fois de suite crée des résultats différents.

-   La méthode est statique mais retourne un objet qui peut être modifié par l’appelant. La récupération de la valeur d’un champ n’autorise pas l’appelant de modifier les données stockées par le champ.

-   La méthode retourne un tableau.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la méthode à une propriété.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle si la méthode rencontre au moins un des critères répertoriés précédemment.

## <a name="controlling-property-expansion-in-the-debugger"></a>Contrôle de l’Expansion de propriété dans le débogueur
 Les programmeurs évitent d’utiliser une propriété est, car ils ne voulez pas que le débogueur développe automatiquement. Par exemple, la propriété peut impliquer d’allouer un grand objet ou d’appeler un P/Invoke, mais elle ne peut pas avoir d’effets secondaires observables réellement.

 Vous pouvez empêcher le débogueur de développer automatiquement les propriétés en appliquant <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. L’exemple suivant illustre cet attribut est appliqué à une propriété d’instance.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Exemple
 L’exemple suivant contient plusieurs méthodes qui doivent être converties en propriétés et plusieurs autres qui ne devez pas, car ils ne se comportent pas comme des champs.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]