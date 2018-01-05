---
title: "CA1062 : Valider les arguments de méthodes publiques | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb659fa8bfd18d8caf4a7473f6cd53809d0a126b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
 Dans [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], cette règle ne détecte pas les paramètres qui sont passés à une autre méthode qui effectue la validation.  

```csharp
public string Method(string value)
{
    EnsureNotNull(value);

    // Fires incorrectly    
    return value.ToString();
}

private void EnsureNotNull(string value)
{
    if (value == null)
        throw new ArgumentNullException("value");
}
```

```vb
Public Function Method(ByVal value As String) As String
    EnsureNotNull(value)

    ' Fires incorrectly    
    Return value.ToString()
End Function

Private Sub EnsureNotNull(ByVal value As String)
    If value Is Nothing Then
        Throw (New ArgumentNullException("value"))
    End If
End Sub
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