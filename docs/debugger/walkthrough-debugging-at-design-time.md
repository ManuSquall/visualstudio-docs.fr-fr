---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage au moment du design | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "points d'arrêt, débogage en mode Design"
  - "déboguer (Visual Studio), en mode Design"
  - "débogage en mode Design"
  - "Exécution (fenêtre), débogage en mode Design"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;bogage au moment du design
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans la fenêtre Visual Studio **Exécution**, vous pouvez exécuter une fonction ou une sous\-routine pendant que votre application ne s'exécute pas.  Si la fonction ou la sous\-routine contient un point d'arrêt, Visual Studio arrête l'exécution à ce point.  Vous pouvez utiliser ensuite les fenêtres du débogueur pour examiner l'état de votre programme.  Cette fonctionnalité est appelée débogage au moment du design.  
  
 La procédure suivante montre comment utiliser cette fonctionnalité.  
  
### Pour atteindre des points d'arrêt depuis la fenêtre Exécution  
  
1.  Collez le code suivant dans une application en console Visual Basic :  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Définissez un point d'arrêt sur la ligne où vous pouvez lire `s="Add BreakPoint Here"`.  
  
3.  Dans la fenêtre **Exécution**, tapez : `?MaFonction<entrée>`  
  
4.  Vérifiez que le point d'arrêt a été atteint et que la pile des appels est exacte.  
  
5.  Dans le menu **Déboguer**, cliquez sur **Continuer** et vérifiez que vous êtes encore en mode Design.  
  
6.  Dans la fenêtre **Exécution**, tapez : `?MaFonction<entrée>`  
  
7.  Dans la fenêtre **Exécution**, tapez : `?MaSousFonction<entrée>`  
  
8.  Vérifiez que vous atteignez le point d'arrêt et examinez la valeur de la variable statique `i` dans la fenêtre **Variables locales**.  Elle doit être égale à 3.  
  
9. Vérifiez que la pile des appels est exacte.  
  
10. Dans le menu **Déboguer**, cliquez sur **Continuer** et vérifiez que vous êtes encore en mode Design.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)