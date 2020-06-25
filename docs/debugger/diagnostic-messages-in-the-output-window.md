---
title: Envoyer des messages à la fenêtre sortie | Microsoft Docs
ms.date: 11/08/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d3c146775ac06b3118186738ee74932a4c452a
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350470"
---
# <a name="send-messages-to-the-output-window"></a>Envoyer des messages vers la Fenêtre Sortie

Vous pouvez écrire des messages d’exécution dans la fenêtre **sortie** à l’aide de la <xref:System.Diagnostics.Debug> classe ou <xref:System.Diagnostics.Trace> de la classe, qui font partie de la <xref:System.Diagnostics> bibliothèque de classes. Utilisez la <xref:System.Diagnostics.Debug> classe si vous souhaitez uniquement générer la sortie dans la version *Debug* de votre programme. Utilisez la <xref:System.Diagnostics.Trace> classe si vous souhaitez générer une sortie à la fois dans les versions *Debug* et *Release* .

## <a name="output-methods"></a>Méthodes de sortie
 Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> fournissent les méthodes de sortie suivantes :

- Plusieurs méthodes `Write`, qui génèrent des informations de sortie sans interrompre l'exécution. Ces méthodes remplacent la méthode `Debug.Print` utilisée dans les versions précédentes de Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName><xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>les méthodes et, qui interrompent l’exécution et les informations de sortie en cas d’échec d’une condition spécifiée. Par défaut, la méthode `Assert` affiche les informations dans une boîte de dialogue. Pour plus d’informations, consultez [Assertions dans du code managé](../debugger/assertions-in-managed-code.md).

- Les <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> méthodes et, qui interrompent toujours les informations d’exécution et de sortie. Par défaut, les méthodes `Fail` affichent les informations dans une boîte de dialogue.

La fenêtre **sortie** peut également afficher des informations sur les éléments suivants :

- Modules que le débogueur a chargés ou déchargés.

- Exceptions qui sont levées.

- Processus qui  cessent de s'exécuter.

- Threads qui s'arrêtent.

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Fenêtre Sortie](../ide/reference/output-window.md)
- [Trace et instrumentation d’applications](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Types de projets C#, F # et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Débogage de code managé](../debugger/debugging-managed-code.md)
