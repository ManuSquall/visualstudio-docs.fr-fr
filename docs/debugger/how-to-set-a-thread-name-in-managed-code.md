---
title: "Comment&#160;: d&#233;finir un nom de thread dans le code manag&#233; | Microsoft Docs"
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
helpviewer_keywords: 
  - "déboguer (Visual Studio), threads"
  - "noms de threads"
  - "Thread.Name (propriété)"
  - "threads (Visual Studio), noms"
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Comment&#160;: d&#233;finir un nom de thread dans le code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il est possible d'attribuer des noms aux threads dans toutes les éditions de Visual Studio.  Ces noms sont utiles pour effectuer le suivi des threads dans la fenêtre **Threads**.  Étant donné que la fenêtre **Threads** n'est pas disponible dans les éditions Visual Studio Express, l'attribution de noms de threads est liée à un petit utilitaire dans ces éditions.  
  
 Pour définir un nom de thread en code managé, utilisez la propriété <xref:System.Threading.Thread.Name%2A>.  
  
## Exemple  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : définir un nom de thread dans le code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)