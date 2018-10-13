---
title: 'Comment : définir un nom de Thread dans du Code managé | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a921fcdcd19114842e026f1ebc3bcb699e200f89
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256099"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Comment : définir un nom de thread dans le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il est possible d'attribuer des noms aux threads dans toutes les éditions de Visual Studio. Ces noms sont utiles pour effectuer le suivi des threads dans le **Threads** fenêtre. Étant donné que le **Threads** fenêtre n’est pas disponible dans les éditions Express de Visual Studio, d’affectation de noms thread a petit utilitaire dans les éditions Express.  
  
 Pour définir un nom de thread en code managé, utilisez la propriété <xref:System.Threading.Thread.Name%2A>.  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Guide pratique pour définir un nom de thread dans du code natif](../debugger/how-to-set-a-thread-name-in-native-code.md)



