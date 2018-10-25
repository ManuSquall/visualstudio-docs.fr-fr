---
title: Envoyer des Messages de Diagnostic dans la fenêtre de sortie | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be9081bc2b6778d2f115ebe61078956aeace85e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842792"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Envoyer des Messages de Diagnostic dans la fenêtre Sortie
Vous pouvez écrire des messages d’exécution pour le **sortie** à l’aide de la fenêtre la <xref:System.Diagnostics.Debug> classe ou le <xref:System.Diagnostics.Trace> (classe), qui font partie de la <xref:System.Diagnostics> bibliothèque de classes. Utilisez le <xref:System.Diagnostics.Debug> classe si vous copiez uniquement dans le *déboguer* version de votre programme. Utilisez le <xref:System.Diagnostics.Trace> classe si vous souhaitez que la sortie à la fois dans le *déboguer* et *version* versions.  
  
## <a name="output-methods"></a>Méthodes de sortie  
 Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> fournissent les méthodes de sortie suivantes :  
  
- Plusieurs méthodes `Write`, qui génèrent des informations de sortie sans interrompre l'exécution. Ces méthodes remplacent la méthode `Debug.Print` utilisée dans les versions précédentes de Visual Basic.  
  
- Les méthodes <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, qui interrompent l'exécution et génèrent des informations de sortie si une condition spécifique échoue. Par défaut, la méthode `Assert` affiche les informations dans une boîte de dialogue. Pour plus d’informations, consultez [Assertions dans du Code managé](../debugger/assertions-in-managed-code.md).  
  
- Les méthodes <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, qui interrompent toujours l'exécution et génèrent des informations de sortie. Par défaut, les méthodes `Fail` affichent les informations dans une boîte de dialogue.  
  
  En plus de programmer à partir de votre application, le **sortie** fenêtre peut afficher des informations sur :  
  
- Modules que le débogueur a chargés ou déchargés.  
  
- Exceptions qui sont levées.  
  
- Processus qui  cessent de s'exécuter.  
  
- Threads qui s'arrêtent.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Fenêtre Sortie](../ide/reference/output-window.md)   
 [Suivi et instrumentation d’applications](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)
