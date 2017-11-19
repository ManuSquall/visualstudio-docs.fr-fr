---
title: "Envoyer des Messages de Diagnostic dans la fenêtre Sortie | Documents Microsoft"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2b898921b022dde9a666a42725bf63c0bb9e6ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Envoyer des Messages de Diagnostic dans la fenêtre Sortie
Vous pouvez écrire des messages d’exécution pour le **sortie** à l’aide de la fenêtre la `Debug` classe ou la `Trace` (classe), qui font partie de la <xref:System.Diagnostics> bibliothèque de classes. Utilisez la classe Debug si vous n'utilisez que la version Debug de votre programme pour la sortie. Utilisez la classe Trace si vous souhaitez obtenir une sortie pour les versions Debug et Release.  
  
## <a name="output-methods"></a>Méthodes de sortie  
 Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> fournissent les méthodes de sortie suivantes :  
  
-   Plusieurs méthodes `Write`, qui génèrent des informations de sortie sans interrompre l'exécution. Ces méthodes remplacent la méthode `Debug.Print` utilisée dans les versions précédentes de Visual Basic.  
  
-   Les méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, qui interrompent l'exécution et génèrent des informations de sortie si une condition spécifique échoue. Par défaut, la méthode `Assert` affiche les informations dans une boîte de dialogue. Pour plus d’informations, consultez [Assertions dans du Code managé](../debugger/assertions-in-managed-code.md).  
  
-   Les méthodes <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, qui interrompent toujours l'exécution et génèrent des informations de sortie. Par défaut, les méthodes `Fail` affichent les informations dans une boîte de dialogue.  
  
 En plus de programmer à partir de votre application, le **sortie** fenêtre peut afficher des informations sur :  
  
-   Modules que le débogueur a chargés ou déchargés.  
  
-   Exceptions qui sont levées.  
  
-   Processus qui  cessent de s'exécuter.  
  
-   Threads qui s'arrêtent.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Fenêtre Sortie](../ide/reference/output-window.md)   
 [Suivi et instrumentation d’applications](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)