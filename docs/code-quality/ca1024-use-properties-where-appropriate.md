---
title: 'CA1024 : Utiliser les propriétés lorsque cela est approprié'
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e4008872a7cb96386ef702d21ba8a18d96037d83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779381"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024 : Utiliser les propriétés lorsque cela est approprié

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une méthode a un nom qui commence par `Get`, n’accepte aucun paramètre et retourne une valeur qui n’est pas un tableau.

Par défaut, cette règle examine uniquement les méthodes publiques et protégées, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Dans la plupart des cas, les propriétés représentent des données et méthodes effectuent des actions. Propriétés sont accessibles comme des champs, ce qui les rend plus facile à utiliser. Une méthode est un bon candidat pour devenir une propriété si une de ces conditions est présente :

- N’accepte aucun argument et retourne les informations d’état d’un objet.

- Accepte un argument unique pour définir une partie de l’état d’un objet.

Propriétés doivent se comporter comme si elles étaient des champs ; Si la méthode ne peut pas, il ne doit pas être changé à une propriété. Méthodes sont plus performants que les propriétés dans les situations suivantes :

- La méthode effectue une opération longue. La méthode est perçue comme plus lente que le temps nécessaire pour définir ou obtenir la valeur d’un champ.

- La méthode effectue une conversion. L’accès à un champ ne retourne pas une version convertie des données qu’il stocke.

- La méthode Get a un effet secondaire observable. Récupération de la valeur d’un champ ne produit pas d’effets secondaires.

- L’ordre d’exécution est important. Définition de la valeur d’un champ ne repose pas sur l’occurrence d’autres opérations.

- Appel de la méthode deux fois de suite crée des résultats différents.

- La méthode est statique mais retourne un objet qui peut être modifié par l’appelant. Récupération de la valeur d’un champ n’autorise pas l’appelant de modifier les données qui sont stockées par le champ.

- La méthode retourne un tableau.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifiez la méthode à une propriété.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle si la méthode rencontre au moins un des critères répertoriés précédemment.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1024.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Expansion de propriété de contrôle dans le débogueur

L’une des raisons les programmeurs évitent à l’aide d’une propriété sont, car ils ne voulez pas que le débogueur il. Par exemple, la propriété pourrait impliquer d’allouer un grand objet ou d’appeler un P/Invoke, mais il peut en fait pas d’effets secondaires observables.

Vous pouvez empêcher le débogueur à partir des propriétés d’autoexpanding en appliquant <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. L’exemple suivant illustre cet attribut est appliqué à une propriété d’instance.

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
}
```

## <a name="example"></a>Exemple

L’exemple suivant contient plusieurs méthodes qui doivent être converties en propriétés et plusieurs qui convient pas, car ils ne se comportent comme des champs.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]