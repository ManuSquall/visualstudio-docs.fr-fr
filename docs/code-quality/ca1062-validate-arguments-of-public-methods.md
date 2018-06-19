---
title: 'CA1062 : Valider les arguments de méthodes publiques'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8393123f34bf8c33e6a65f26944640b500334dcb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900876"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 : Valider les arguments de méthodes publiques

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode visible de l’extérieur déréférence l’un de ses arguments de référence sans vérifier si cet argument est `null` (`Nothing` en Visual Basic).

## <a name="rule-description"></a>Description de la règle

Tous les arguments de référence passés aux méthodes visibles de l’extérieur doivent être vérifiés `null`. Si besoin, levez une <xref:System.ArgumentNullException> lorsque l’argument est `null`.

Si une méthode peut être appelée à partir d’un assembly inconnu, car il est déclaré public ou protégé, vous devez valider tous les paramètres de la méthode. Si la méthode est conçue pour être appelée uniquement par les assemblys connus, vous devez rendre la méthode interne et appliquer le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> d’attribut à l’assembly qui contient la méthode.

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
                throw new ArgumentNullException("input");
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
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Exemple

Les constructeurs de copie qui remplissent les propriétés du champ ou qui sont des objets de référence peuvent également violer la règle CA1062. La violation se produit parce que l’objet copié est passé au constructeur de copie peut être `null` (`Nothing` en Visual Basic). Pour résoudre la violation, utilisez une méthode static (Shared en Visual Basic) pour vérifier que l’objet copié n’est pas null.

Dans l’exemple suivant `Person` exemple de classe, le `other` objet est passé à la `Person` constructeur de copie peut être `null`.

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

Suit révisé `Person` exemple, le `other` objet est passé au constructeur de copie est vérifié en premier pour la valeur null dans le `PassThroughNonNull` (méthode).

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
            throw new ArgumentNullException("person");
        return person;
    }
}

```