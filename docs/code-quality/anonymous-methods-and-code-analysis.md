---
title: "M&#233;thodes anonymes et analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthodes anonymes, analyse du code"
  - "analyse du code, méthodes anonymes"
  - "méthodes, anonymes"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# M&#233;thodes anonymes et analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une *méthode anonyme* est une méthode sans nom.  Les méthodes anonymes sont le plus souvent utilisées pour passer un bloc de code en paramètre de délégué.  
  
 Cette rubrique explique comment l'analyse du code gère les avertissements et la métrique associés aux méthodes anonymes.  
  
## Méthodes anonymes déclarées dans un membre  
 Les avertissements et la métrique d'une méthode anonyme déclarés dans un membre, tels qu'une méthode ou un accesseur, sont associés au membre qui déclare la méthode.  Ils ne sont pas associés au membre qui appelle la méthode.  
  
 Par exemple, dans la classe suivante, tout avertissement trouvé dans la déclaration d'**anonymousMethod** doit être déclenché concernant **Method1** et non **Method2**.  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
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
  
## Méthodes anonymes inline  
 Les avertissements et la métrique pour une méthode anonyme déclarée comme une assignation inline à un champ sont associés au constructeur.  Si le champ est déclaré comme `static` \(`Shared` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), les avertissements et la métrique sont associés au constructeur de classe ; sinon, ils sont associés au constructeur d'instance.  
  
 Par exemple, dans la classe suivante, tout avertissement trouvé dans la déclaration d'**anonymousMethod1** sera déclenché concernant le constructeur par défaut généré implicitement de **Class**.  Tandis que ceux trouvés dans **anonymousMethod2** seront appliqués au constructeur de classe généré implicitement.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
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
  
 Une classe pourrait contenir une méthode anonyme inline qui assigne une valeur à un champ comportant plusieurs constructeurs.  Dans ce cas, les avertissements et la métrique sont associés à tous les constructeurs à moins que ce constructeur s'enchaîne à un autre constructeur dans la même classe.  
  
 Par exemple, dans la classe suivante, tout avertissement trouvé dans la déclaration d'**anonymousMethod** doit être déclenché concernant **Class\(int\)** et **Class\(string\)**, mais pas concernant **Class\(\)**.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
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
  
 Bien que cela puisse paraître inattendu, ceci est dû au fait que le compilateur génère une méthode unique pour chaque constructeur qui ne s'enchaîne pas à un autre constructeur.  À cause de ce comportement, toute violation se produisant dans **anonymousMethod** doit être supprimée séparément.  Cela signifie également que si un nouveau constructeur est présenté, les avertissements concernant **Class\(int\)** et **Class\(string\)** supprimés précédemment doivent également être supprimés concernant le nouveau constructeur.  
  
 Vous pouvez contourner ce problème de deux façons.  Vous pouvez déclarer **anonymousMethod** dans un constructeur commun auquel tous les constructeurs s'enchaînent.  Vous pouvez également le déclarer dans une méthode d'initialisation appelée par tous les constructeurs.  
  
## Voir aussi  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)