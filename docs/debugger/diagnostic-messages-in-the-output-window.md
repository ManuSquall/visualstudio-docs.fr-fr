---
title: Envoyer des messages dans la fenêtre Sortie | Microsoft Docs
ms.date: 11/08/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4493eb55b83b9f76d1a833ba2df359ae9683e8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682503"
---
# <a name="send-messages-to-the-output-window"></a>Envoyer des messages vers la Fenêtre Sortie

Vous pouvez écrire des messages d’exécution pour le **sortie** à l’aide de la fenêtre la <xref:System.Diagnostics.Debug> classe ou le <xref:System.Diagnostics.Trace> (classe), qui font partie de la <xref:System.Diagnostics> bibliothèque de classes. Utilisez le <xref:System.Diagnostics.Debug> classe si vous ne voulez que la sortie le *déboguer* version de votre programme. Utilisez le <xref:System.Diagnostics.Trace> classe si vous souhaitez que la sortie à la fois dans le *déboguer* et *version* versions.

## <a name="output-methods"></a>Méthodes de sortie
 Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> fournissent les méthodes de sortie suivantes :

- Plusieurs méthodes `Write`, qui génèrent des informations de sortie sans interrompre l'exécution. Ces méthodes remplacent la méthode `Debug.Print` utilisée dans les versions précédentes de Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> méthodes, qui interrompent l’exécution et la sortie des informations si une condition spécifique échoue. Par défaut, la méthode `Assert` affiche les informations dans une boîte de dialogue. Pour plus d’informations, consultez [Assertions dans du code managé](../debugger/assertions-in-managed-code.md).

- Le <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> méthodes, qui interrompent toujours les informations de l’exécution et de sortie. Par défaut, les méthodes `Fail` affichent les informations dans une boîte de dialogue.

Le **sortie** fenêtre peut également afficher des informations sur :

- Modules que le débogueur a chargés ou déchargés.

- Exceptions qui sont levées.

- Processus qui  cessent de s'exécuter.

- Threads qui s'arrêtent.

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Fenêtre Sortie](../ide/reference/output-window.md)
- [Trace et instrumenter des applications](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
