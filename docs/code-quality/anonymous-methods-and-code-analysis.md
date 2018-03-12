---
title: "Méthodes anonymes et analyse du Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0c7016145d5d34c9077f45f2dbf6c1507aa0e6fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="anonymous-methods-and-code-analysis"></a>Méthodes anonymes et analyse du code
Un *méthode anonyme* est une méthode qui n’a aucun nom. Méthodes anonymes sont fréquemment utilisés pour passer un bloc de code comme un paramètre de délégué.  
  
 Cette rubrique explique comment l’analyse du Code gère les avertissements et les mesures qui sont associés aux méthodes anonymes.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Méthodes anonymes déclarées dans un membre  
 Avertissements et la métrique d’une méthode anonyme qui est déclarée dans un membre, tel qu’une méthode ou un accesseur, est associés au membre qui déclare la méthode. Ils ne sont pas associées au membre qui appelle la méthode.  
  
 Par exemple, dans la classe suivante, les avertissements qui se trouvent dans la déclaration de **anonymousMethod** doit être déclenché sur **Method1** et non **méthode2**.  
  
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
  
## <a name="inline-anonymous-methods"></a>Méthodes anonymes inline  
 Avertissements et la métrique d’une méthode anonyme qui est déclarée comme une assignation inline à un champ est associés au constructeur. Si le champ est déclaré en tant que `static` (`Shared` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), les avertissements et les métriques sont associés au constructeur de classe ; sinon, ils sont associés au constructeur d’instance.  
  
 Par exemple, dans la classe suivante, les avertissements qui se trouvent dans la déclaration de **anonymousMethod1** sera déclenché concernant le constructeur par défaut généré implicitement **classe**. Tandis que ceux trouvés dans **anonymousMethod2** seront appliqués au constructeur de classe généré implicitement.  
  
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
  
 Une classe peut contenir une méthode anonyme inline qui assigne une valeur à un champ qui possède plusieurs constructeurs. Dans ce cas, les avertissements et la métrique est associés à tous les constructeurs, sauf si ce constructeur est lié à un autre constructeur de la même classe.  
  
 Par exemple, dans la classe suivante, les avertissements qui se trouvent dans la déclaration de **anonymousMethod** doit être déclenché sur **Class (int)** et **Class (String)** mais pas contre **Class()**.  
  
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
  
 Bien que cela peut paraître inattendu, cela se produit, car le compilateur génère une méthode unique pour chaque constructeur qui ne s’enchaîne pas à un autre constructeur. En raison de ce comportement, toute violation qui se produit dans **anonymousMethod** doit être supprimée séparément. Cela signifie également que si un nouveau constructeur est introduit, les avertissements qui ont été précédemment supprimés sur **Class (int)** et **Class (String)** doit également être supprimée sur le nouveau constructeur.  
  
 Vous pouvez contourner ce problème dans un des deux façons. Vous pouvez déclarer **anonymousMethod** dans un constructeur commun qui chaîne de tous les constructeurs. Ou vous pouvez la déclarer dans une méthode d’initialisation qui est appelée par tous les constructeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)