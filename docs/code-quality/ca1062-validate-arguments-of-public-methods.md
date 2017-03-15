---
title: "CA1062&#160;: Valider les arguments de m&#233;thodes publiques | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062&#160;: Valider les arguments de m&#233;thodes publiques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode visible de l'extérieur déréférence l'un de ses arguments de référence sans vérifier si cet argument a la valeur `null` \(`Nothing` en Visual Basic\).  
  
## Description de la règle  
 Tous les arguments de référence passés aux méthodes visibles de l'extérieur doivent être vérifiés pour voir s'ils ont la valeur `null`.  Si besoin, levez une exception <xref:System.ArgumentNullException> lorsque l'argument a la valeur `null`.  
  
 Si une méthode peut être appelée à partir d'un assembly inconnu car il est déclaré public ou protégé, vous devez valider tous les paramètres de la méthode.  Si la méthode est conçue pour être appelée uniquement par les assemblys connus, vous devez rendre la méthode interne et appliquer l'attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> à l'assembly qui contient la méthode.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, validez chaque argument de référence par rapport à `null`.  
  
## Quand supprimer les avertissements  
 Vous pouvez supprimer un avertissement de cette règle si vous êtes certain que le paramètre déréférencé a été validé par un autre appel de méthode dans la fonction.  
  
## Exemple  
 L'exemple suivant présente une méthode qui viole la règle et une autre qui satisfait à la règle.  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## Exemple  
 Dans [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], cette règle ne détecte pas les paramètres qui sont passés à une autre méthode qui fait la validation.  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## Exemple  
 Les constructeurs de copie qui remplissent u  champ ou des propriétés qui sont des objets de référence peuvent également violer la règle CA1062.  La violation se produit parce que l'objet copié passé au constructeur de copie peut être `null` \(`Nothing` en Visual Basic\).  Pour résoudre la violation, utilisez une méthode statique \(méthode partagée en Visual Basic\) pour vérifier que l'objet copié n'est pas null.  
  
 Dans l'exemple de classe `Person` suivant, l'objet `other` passé au constructeur de copie `Person` peut être `null`.  
  
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
  
## Exemple  
 Dans l'exemple modifié `Person` suivant, l'objet `other` passé au constructeur de copie est vérifié en premier pour null dans la méthode `PassThroughNonNull`.  
  
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