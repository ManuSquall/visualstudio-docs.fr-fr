---
title: Avertissements d’analyse de code de méthode anonyme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47f90e0a9ca01e76ea1a3686c790dcf00a4becde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860778"
---
# <a name="anonymous-methods-and-code-analysis"></a>Méthodes anonymes et analyse du code

Un *méthode anonyme* est une méthode qui n’a aucun nom. Méthodes anonymes sont fréquemment utilisés pour passer un bloc de code comme un paramètre de délégué. Cet article explique comment l’analyse du code gère les avertissements et les métriques pour les méthodes anonymes.

## <a name="anonymous-methods-declared-in-a-member"></a>Méthodes anonymes déclarées dans un membre

Avertissements et les métriques pour une méthode anonyme qui est déclarée dans un membre, tel qu’une méthode ou un accesseur, sont associés au membre qui déclare la méthode. Ils ne sont pas associés au membre qui appelle la méthode.

Par exemple, dans la classe suivante, les avertissements qui se trouvent dans la déclaration de **anonymousMethod** doit être déclenché sur **Method1** et non **Method2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Méthodes anonymes inline

Avertissements et les métriques pour une méthode anonyme qui est déclarée comme une assignation inline à un champ sont associés au constructeur. Si le champ est déclaré en tant que `static` (`Shared` en Visual Basic), les avertissements et les métriques sont associés au constructeur de classe. Sinon, elles sont associées avec le constructeur d’instance.

Par exemple, dans la classe suivante, les avertissements qui se trouvent dans la déclaration de **anonymousMethod1** sera déclenché concernant le constructeur par défaut généré implicitement de **classe**. Les avertissements qui sont trouvent dans **anonymousMethod2** seront appliqués au constructeur de classe généré implicitement.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

Une classe peut contenir une méthode anonyme inline qui assigne une valeur à un champ qui possède plusieurs constructeurs. Dans ce cas, les avertissements et les métriques sont associés à tous les constructeurs, sauf si ce constructeur est lié à un autre constructeur dans la même classe.

Par exemple, dans la classe suivante, les avertissements qui se trouvent dans la déclaration de **anonymousMethod** doit être déclenché sur **Class (int)** et **Class (String)**, mais pas contre **Class()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

Les avertissements sont déclenchés sur les constructeurs, car le compilateur génère une méthode unique pour chaque constructeur qui n’est pas lié à un autre constructeur. Étant donné ce comportement, toute violation qui se produit dans **anonymousMethod** doit être supprimée séparément. Cela signifie également que si un nouveau constructeur est introduit, les avertissements qui ont été précédemment supprimés sur **Class (int)** et **Class (String)** doit également être supprimée sur le nouveau constructeur.

Vous pouvez contourner ce problème de deux manières :

- Déclarer **anonymousMethod** dans un constructeur commun qui chaîne de tous les constructeurs.
- Déclarer **anonymousMethod** dans une méthode d’initialisation qui est appelée par tous les constructeurs.

## <a name="see-also"></a>Voir aussi

- [Analyse de la qualité d’un code managé](../code-quality/code-analysis-for-managed-code-overview.md)