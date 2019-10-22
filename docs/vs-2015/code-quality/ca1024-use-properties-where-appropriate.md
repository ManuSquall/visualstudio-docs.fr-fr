---
title: 'CA1024 : utilisez les propriétés lorsque cela est approprié | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b190e007cfdb016e54148cf0295c68baf68c5033
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661963"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024 : Utiliser les propriétés lorsque cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée a un nom qui commence par `Get`, ne prend aucun paramètre et retourne une valeur qui n’est pas un tableau.

## <a name="rule-description"></a>Description de la règle
 Dans la plupart des cas, les propriétés représentent des données et des méthodes qui effectuent des actions. Les propriétés sont accessibles comme les champs, ce qui les rend plus faciles à utiliser. Une méthode est un bon candidat à devenir une propriété si l’une de ces conditions est présente :

- N’accepte aucun argument et retourne les informations d’état d’un objet.

- Accepte un seul argument pour définir une partie de l’état d’un objet.

  Les propriétés doivent se comporter comme s’il s’agissait de champs ; Si la méthode ne peut pas, elle ne doit pas être remplacée par une propriété. Les méthodes sont meilleures que les propriétés dans les cas suivants :

- La méthode effectue une opération qui prend du temps. La méthode est perçue plus lentement que le temps nécessaire pour définir ou obtenir la valeur d’un champ.

- La méthode effectue une conversion. L’accès à un champ ne retourne pas une version convertie des données qu’il stocke.

- La méthode d’extraction a un effet secondaire observable. La récupération de la valeur d’un champ ne produit aucun effet secondaire.

- L’ordre d’exécution est important. La définition de la valeur d’un champ ne repose pas sur l’occurrence d’autres opérations.

- L’appel de la méthode deux fois à la suite crée des résultats différents.

- La méthode est statique mais retourne un objet qui peut être modifié par l’appelant. La récupération de la valeur d’un champ ne permet pas à l’appelant de modifier les données stockées par le champ.

- La méthode retourne un tableau.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez la méthode par une propriété.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si la méthode remplit au moins l’un des critères précédemment listés.

## <a name="controlling-property-expansion-in-the-debugger"></a>Contrôle de l’expansion des propriétés dans le débogueur
 L’une des raisons pour lesquelles les programmeurs évitent d’utiliser une propriété est parce qu’ils ne souhaitent pas que le débogueur le développe automatiquement. Par exemple, la propriété peut impliquer l’allocation d’un objet volumineux ou l’appel d’un P/Invoke, mais elle peut ne pas avoir d’effets secondaires observables.

 Vous pouvez empêcher le débogueur d’étendre automatiquement les propriétés en appliquant <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. L’exemple suivant montre que cet attribut est appliqué à une propriété d’instance.

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
 L’exemple suivant contient plusieurs méthodes qui doivent être converties en propriétés, et plusieurs qui ne le sont pas, car elles ne se comportent pas comme des champs.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
