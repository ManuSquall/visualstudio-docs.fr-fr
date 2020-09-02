---
title: Messages de diagnostic dans le Fenêtre Sortie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695297"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Messages de diagnostic dans la fenêtre Sortie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez écrire des messages d'exécution dans la fenêtre Sortie en utilisant les classes Debug ou Trace, qui font partie de la bibliothèque de classes <xref:System.Diagnostics>. Utilisez la classe Debug si vous n'utilisez que la version Debug de votre programme pour la sortie. Utilisez la classe Trace si vous souhaitez obtenir une sortie pour les versions Debug et Release.  
  
## <a name="output-methods"></a>Méthodes de sortie  
 Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> fournissent les méthodes de sortie suivantes :  
  
- Plusieurs méthodes `Write`, qui génèrent des informations de sortie sans interrompre l'exécution. Ces méthodes remplacent la méthode `Debug.Print` utilisée dans les versions précédentes de Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName><xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>les méthodes et, qui interrompent l’exécution et génèrent des informations en cas d’échec d’une condition spécifiée. Par défaut, la méthode `Assert` affiche les informations dans une boîte de dialogue. Pour plus d’informations, consultez [assertions dans du code managé](../debugger/assertions-in-managed-code.md).  
  
- Les méthodes <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, qui interrompent toujours l'exécution et génèrent des informations de sortie. Par défaut, les méthodes `Fail` affichent les informations dans une boîte de dialogue.  
  
  En plus de programmer à partir de votre application, la fenêtre **sortie** peut afficher des informations sur les éléments suivants :  
  
- Modules que le débogueur a chargés ou déchargés.  
  
- Exceptions qui sont levées.  
  
- Processus qui  cessent de s'exécuter.  
  
- Threads qui s'arrêtent.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Fenêtre Sortie](../ide/reference/output-window.md)   
 [Traçage et instrumentation d’applications](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Présentation de l’instrumentation et du suivi](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Types de projets C#, F # et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)
