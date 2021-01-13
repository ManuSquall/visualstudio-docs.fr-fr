---
title: Instructions Stop dans Visual Basic | Microsoft Docs
description: Passez en revue l’instruction Visual Basic Stop, qui fournit une alternative de programmation à la définition d’un point d’arrêt dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b36f00f628d9551d8e45075d790d8e5d2de294dc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149428"
---
# <a name="stop-statements-in-visual-basic"></a>Instructions Stop en Visual Basic

L'instruction Stop de Visual Basic fournit une alternative de programmation à la définition d'un point d'arrêt. Lorsque le débogueur rencontre une instruction Stop, il interrompt l'exécution du programme (passe en mode arrêt). Les programmeurs C# peuvent obtenir le même effet à l’aide d’un appel à <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Vous définissez ou supprimez une instruction Stop en modifiant votre code source. Vous ne pouvez pas définir ou supprimer des instructions Stop en utilisant des commandes du débogueur, comme pour un point d'arrêt.

À la différence d'une instruction End, l'instruction Stop ne réinitialise pas les variables ou ne retourne pas en mode design. Vous pouvez choisir Continuer dans le menu Déboguer pour poursuivre l'exécution de l'application.

Quand vous exécutez une Visual Basic application en dehors du débogueur, une instruction Stop lance le débogueur si le débogage juste-à-temps est activé. Si le débogage juste-à-temps n’est pas activé, l’instruction Stop se comporte comme s’il s’agissait d’une instruction end et termine l’exécution. Si aucun événement QueryUnload ou Unload ne se produit, vous devez supprimer toutes les instructions Stop de la version Release de votre application Visual Basic. Pour plus d’informations, consultez [Débogage juste-à-temps](just-in-time-debugging-in-visual-studio.md).

 Pour éviter de supprimer les instructions Stop, vous pouvez utiliser la compilation conditionnelle :

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Une autre solution consiste à utiliser une <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> instruction au lieu de l’instruction Stop. Une <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> instruction interrompt l’exécution uniquement lorsqu’une condition spécifiée n’est pas remplie. <xref:System.Diagnostics.Debug.Assert%2A> les instructions sont automatiquement supprimées lorsque vous générez une version Release. Pour plus d’informations, consultez [assertions dans du code managé](assertions-in-managed-code.md). Si vous souhaitez une <xref:System.Diagnostics.Debug.Assert%2A> instruction qui interrompt toujours l’exécution dans la version de débogage, procédez comme suit :

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Une autre solution consiste à utiliser la <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> méthode :

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](debugger-security.md)
- [Types de projets C#, F# et Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Débogage du code managé](debugging-managed-code.md)
