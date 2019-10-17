---
title: 'CA1062 : Valider les arguments de méthodes publiques'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6019956d37d420b72275223148c2a3468a820884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440708"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 : Valider les arguments de méthodes publiques

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode visible de l’extérieur déréférence l’un de ses arguments de référence sans vérifier si cet argument est `null` (`Nothing` dans Visual Basic).

## <a name="rule-description"></a>Description de la règle

Tous les arguments de référence passés aux méthodes visibles de l’extérieur doivent être vérifiés par rapport à `null`. Le cas échéant, levez une <xref:System.ArgumentNullException> lorsque l’argument est `null`.

Si une méthode peut être appelée à partir d’un assembly inconnu, car elle est déclarée publique ou protégée, vous devez valider tous les paramètres de la méthode. Si la méthode est conçue pour être appelée uniquement par des assemblys connus, vous devez rendre la méthode interne et appliquer l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> à l’assembly qui contient la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, validez chaque argument de référence par rapport à `null`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer un avertissement de cette règle si vous êtes sûr que le paramètre déréférencé a été validé par un autre appel de méthode dans la fonction.

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode qui enfreint la règle et une méthode qui satisfait la règle.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException(nameof(input));
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException(NameOf(input))
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Exemple

Les constructeurs de copie qui remplissent des champs ou des propriétés qui sont des objets de référence peuvent également enfreindre la règle CA1062. La violation se produit parce que l’objet copié qui est passé au constructeur de copie peut être `null` (`Nothing` dans Visual Basic). Pour résoudre la violation, utilisez une méthode statique (Shared in Visual Basic) pour vérifier que l’objet copié n’a pas la valeur null.

Dans l’exemple de classe `Person` suivant, l’objet `other` qui est passé au constructeur de copie `Person` peut être `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Exemple

Dans l’exemple `Person` révisé suivant, l’objet `other` qui est passé au constructeur de copie est d’abord vérifié pour la valeur null dans la méthode `PassThroughNonNull`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException(nameof(person));
        return person;
    }
}
```
