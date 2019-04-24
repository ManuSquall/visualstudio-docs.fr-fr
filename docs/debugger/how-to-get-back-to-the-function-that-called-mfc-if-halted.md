---
title: Revenir à la fonction qui a appelé MFC en cas d’arrêt | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f846b636d2790839de6d05d048fc7e24d0bc6253
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114884"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procédure : Retourner à la fonction qui a appelé MFC en cas d’arrêt

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Si vous avez utilisé la commande **Arrêter** du menu **Déboguer** pour arrêter le programme, que vous vous trouvez dans la bibliothèque MFC et que vous êtes certain que le problème se trouve dans votre code, vous pouvez utiliser la fenêtre Pile des appels pour revenir à votre fonction. Pour plus d'informations, voir [Procédure : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).

Il peut arriver que votre code se trouve dans la pompe de messages. Dans ce cas, il n'y a aucun code utilisateur dans la pile des appels. Pour éviter ce problème, vous pouvez utiliser des points d’arrêt (avec des conditions et des nombres d’accès, éventuellement) au lieu de la commande **Arrêter**. Pour plus d'informations, consultez [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Accédez à la fonction à partir de laquelle MFC a été appelée

- Utilisez la fenêtre **Pile des appels**.

## <a name="see-also"></a>Voir aussi

- [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)