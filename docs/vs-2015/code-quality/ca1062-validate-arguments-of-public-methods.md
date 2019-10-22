---
title: 'CA1062 : valider les arguments des méthodes publiques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663654"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 : Valider les arguments de méthodes publiques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Exemple
 Dans [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], cette règle ne détecte pas que les paramètres sont passés à une autre méthode qui effectue la validation.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Exemple
 Les constructeurs de copie qui remplissent des champs ou des propriétés qui sont des objets de référence peuvent également enfreindre la règle CA1062. La violation se produit parce que l’objet copié qui est passé au constructeur de copie peut être `null` (`Nothing` dans Visual Basic). Pour résoudre la violation, utilisez une méthode statique (Shared in Visual Basic) pour vérifier que l’objet copié n’a pas la valeur null.

 Dans l’exemple de classe `Person` suivant, l’objet `other` qui est passé au constructeur de copie `Person` peut être `null`.

```

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

```
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
