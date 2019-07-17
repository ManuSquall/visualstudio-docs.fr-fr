---
title: 'CA1062 : Valider les arguments de méthodes publiques | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13ea687ea9ca68693af7e2aa5c22881a36207d2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200444"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 : Valider les arguments de méthodes publiques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode visible de l’extérieur déréférence l’un de ses arguments de référence sans vérifier si cet argument est `null` (`Nothing` en Visual Basic).

## <a name="rule-description"></a>Description de la règle
 Tous les arguments de référence passés aux méthodes visibles de l’extérieur doivent être vérifiés pour `null`. Si besoin, levez une <xref:System.ArgumentNullException> lorsque l’argument est `null`.

 Si une méthode peut être appelée à partir d’un assembly inconnu, car il est déclaré public ou protégé, vous devez valider tous les paramètres de la méthode. Si la méthode est conçue pour être appelée uniquement par les assemblys connus, vous devez rendre la méthode interne et appliquer le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> d’attribut à l’assembly qui contient la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, validez chaque argument de référence par rapport à `null`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer un avertissement de cette règle si vous êtes sûr que le paramètre déréférencé a été validé par un autre appel de méthode dans la fonction.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui viole la règle et une méthode qui satisfait la règle.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Exemple
 Dans [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], cette règle ne détecte pas les paramètres qui sont passés à une autre méthode qui effectue la validation.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Exemple
 Les constructeurs de copie qui remplissent les propriétés du champ ou qui sont des objets de référence peuvent également violer la règle CA1062. La violation se produit parce que l’objet copié est passé au constructeur de copie peut être `null` (`Nothing` en Visual Basic). Pour résoudre la violation, utilisez une méthode statique (Shared en Visual Basic) pour vérifier que l’objet copié n’est pas null.

 Dans l’exemple suivant `Person` exemple de classe, le `other` objet qui est passé à la `Person` constructeur de copie peut être `null`.

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

## <a name="example"></a>Exemples
 Dans le code suivant révisée `Person` exemple, le `other` objet qui est passé au constructeur de copie est vérifié en premier pour null dans le `PassThroughNonNull` (méthode).

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
