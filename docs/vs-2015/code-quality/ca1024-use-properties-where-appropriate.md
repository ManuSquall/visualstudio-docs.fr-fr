---
title: 'CA1024 : Utiliser des propriétés approprié | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fd859492faeb5af7a74d0261ff8d86333ff5ade8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222727"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024 : Utiliser les propriétés lorsque cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée a un nom qui commence par `Get`, n’accepte aucun paramètre et retourne une valeur qui n’est pas un tableau.

## <a name="rule-description"></a>Description de la règle
 Dans la plupart des cas, les propriétés représentent des données et méthodes effectuent des actions. Propriétés sont accessibles comme des champs, ce qui les rend plus facile à utiliser. Une méthode est un bon candidat pour devenir une propriété si une de ces conditions est présente :

-   N’accepte aucun argument et retourne les informations d’état d’un objet.

-   Accepte un argument unique pour définir une partie de l’état d’un objet.

 Propriétés doivent se comporter comme si elles étaient des champs ; Si la méthode ne peut pas, il ne doit pas être changé à une propriété. Méthodes sont plus performants que les propriétés dans les situations suivantes :

-   La méthode effectue une opération longue. La méthode est perçue comme plus lente que le temps nécessaire pour définir ou obtenir la valeur d’un champ.

-   La méthode effectue une conversion. L’accès à un champ ne retourne pas une version convertie des données qu’il stocke.

-   La méthode Get a un effet secondaire observable. Récupération de la valeur d’un champ ne produit pas d’effets secondaires.

-   L’ordre d’exécution est important. Définition de la valeur d’un champ ne repose pas sur l’occurrence d’autres opérations.

-   Appel de la méthode deux fois de suite crée des résultats différents.

-   La méthode est statique mais retourne un objet qui peut être modifié par l’appelant. Récupération de la valeur d’un champ n’autorise pas l’appelant de modifier les données qui sont stockées par le champ.

-   La méthode retourne un tableau.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la méthode à une propriété.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si la méthode rencontre au moins un des critères répertoriés précédemment.

## <a name="controlling-property-expansion-in-the-debugger"></a>Contrôle de l’Expansion de propriété dans le débogueur
 Les programmeurs évitent à l’aide d’une propriété est, car ils ne voulez pas que le débogueur développe automatiquement. Par exemple, la propriété pourrait impliquer d’allouer un grand objet ou d’appeler un P/Invoke, mais il peut en fait pas d’effets secondaires observables.

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
 L’exemple suivant contient plusieurs méthodes qui doivent être converties en propriétés, et plusieurs qui convient pas, car ils ne se comportent pas comme champs.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]



