---
title: 'Comment : définir un nom de Thread en Code managé | Documents Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8b2eeed6a597dc64b6f346e85a426c2105a2565e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Comment : définir un nom de thread dans le code managé
Il est possible d'attribuer des noms aux threads dans toutes les éditions de Visual Studio. Ces noms sont utiles pour effectuer le suivi des threads dans le **Threads** fenêtre.
  
 Pour définir un nom de thread en code managé, utilisez la propriété <xref:System.Threading.Thread.Name%2A>.  
  
## <a name="example"></a>Exemple  

```csharp
public class Needle
{
    // This method will be called when the thread is started.  
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.   
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".  
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate  
    oThread.Start();
}
```

```VB 
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
    ' Set the Thread name to "MyThread".  
    oThread.Name = "MyThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Guide pratique pour définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)