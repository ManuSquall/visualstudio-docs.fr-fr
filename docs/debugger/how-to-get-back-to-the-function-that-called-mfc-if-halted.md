---
title: Revenir à la fonction qui a appelé MFC en cas d’arrêt | Microsoft Docs
description: Découvrez comment revenir à la fonction qui a appelé MFC en cas d’arrêt de l’exécution dans le débogueur Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31bbb064aad5a43738b2f345cf31a20767c55e69
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384679"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Comment : retourner à la fonction qui a appelé l'application MFC en cas d'arrêt

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Si vous avez utilisé la commande **Arrêter** du menu **Déboguer** pour arrêter le programme, que vous vous trouvez dans la bibliothèque MFC et que vous êtes certain que le problème se trouve dans votre code, vous pouvez utiliser la fenêtre Pile des appels pour revenir à votre fonction. Pour plus d’informations, consultez [Comment : utiliser la fenêtre pile des appels](../debugger/how-to-use-the-call-stack-window.md).

Il peut arriver que votre code se trouve dans la pompe de messages. Dans ce cas, il n'y a aucun code utilisateur dans la pile des appels. Pour éviter ce problème, vous pouvez utiliser des points d’arrêt (avec des conditions et des nombres d’accès, éventuellement) au lieu de la commande **Arrêter**. Pour plus d'informations, consultez [Breakpoints and Tracepoints](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Naviguer jusqu’à la fonction à partir de laquelle MFC a été appelé

- Utilisez la fenêtre **pile des appels** .

## <a name="see-also"></a>Voir aussi

- [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)