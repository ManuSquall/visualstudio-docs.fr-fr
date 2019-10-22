---
title: Méthodes anonymes et analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652225"
---
# <a name="anonymous-methods-and-code-analysis"></a>Méthodes anonymes et analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une *méthode anonyme* est une méthode qui n’a pas de nom. Les méthodes anonymes sont le plus souvent utilisées pour passer un bloc de code en tant que paramètre de délégué.

 Cette rubrique explique comment l’analyse du code gère les avertissements et les métriques associés aux méthodes anonymes.

## <a name="anonymous-methods-declared-in-a-member"></a>Méthodes anonymes déclarées dans un membre
 Les avertissements et les métriques pour une méthode anonyme déclarée dans un membre, tel qu’une méthode ou un accesseur, sont associés au membre qui déclare la méthode. Ils ne sont pas associés au membre qui appelle la méthode.

 Par exemple, dans la classe suivante, tous les avertissements qui se trouvent dans la déclaration de **anonymousMethod** doivent être déclenchés sur **Method1** et non pas sur **méthode2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
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

## <a name="inline-anonymous-methods"></a>Méthodes anonymes Inline
 Les avertissements et les métriques pour une méthode anonyme déclarée comme une assignation Inline à un champ sont associés au constructeur. Si le champ est déclaré comme `static` (`Shared` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), les avertissements et les métriques sont associés au constructeur de classe. dans le cas contraire, elles sont associées au constructeur d’instance.

 Par exemple, dans la classe suivante, tous les avertissements qui se trouvent dans la déclaration de **anonymousMethod1** seront déclenchés par rapport au constructeur par défaut généré implicitement de la **classe**. En revanche, ceux qui se trouvent dans **anonymousMethod2** seront appliqués au constructeur de classe implicitement généré.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
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

 Une classe peut contenir une méthode anonyme inline qui assigne une valeur à un champ ayant plusieurs constructeurs. Dans ce cas, les avertissements et les métriques sont associés à tous les constructeurs, sauf si ce constructeur est chaîné à un autre constructeur de la même classe.

 Par exemple, dans la classe suivante, tous les avertissements détectés dans la déclaration de **anonymousMethod** doivent être déclenchés par rapport à la classe **(int)** et à la **classe (String)** , mais pas à la **classe ()** .

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
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

 Bien que cela puisse paraître inattendu, cela se produit car le compilateur génère une méthode unique pour chaque constructeur qui n’est pas lié à un autre constructeur. En raison de ce comportement, toute violation qui se produit dans **anonymousMethod** doit être supprimée séparément. Cela signifie également que si un nouveau constructeur est introduit, les avertissements précédemment supprimés de la **classe (int)** et de la **classe (String)** doivent également être supprimés du nouveau constructeur.

 Vous pouvez contourner ce problème de deux manières. Vous pouvez déclarer **anonymousMethod** dans un constructeur commun que tous les constructeurs chaînent. Ou vous pouvez le déclarer dans une méthode d’initialisation qui est appelée par tous les constructeurs.

## <a name="see-also"></a>Voir aussi
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
