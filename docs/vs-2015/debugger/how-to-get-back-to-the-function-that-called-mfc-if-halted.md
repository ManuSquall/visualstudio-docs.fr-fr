---
title: 'Procédure : Revenir à la fonction qui a appelé MFC en cas d’arrêt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c19cbf6e892ba8b35f2b92ad9b86aa0b74a64810
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685885"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procédure : Retourner à la fonction qui a appelé MFC en cas d’arrêt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si vous avez utilisé la commande **Arrêter** du menu **Déboguer** pour arrêter le programme, que vous vous trouvez dans la bibliothèque MFC et que vous êtes certain que le problème se trouve dans votre code, vous pouvez utiliser la fenêtre Pile des appels pour revenir à votre fonction. Pour plus d'informations, voir [Procédure : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).  
  
 Il peut arriver que votre code se trouve dans la pompe de messages. Dans ce cas, il n'y a aucun code utilisateur dans la pile des appels. Pour éviter ce problème, vous pouvez utiliser des points d’arrêt (avec des conditions et des nombres d’accès, éventuellement) au lieu de la commande **Arrêter**. Pour plus d’informations, consultez [des points d’arrêt et points de trace](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Pour naviguer vers la fonction à partir de laquelle la bibliothèque MFC a été appelée  
  
- Utilisez la fenêtre **Pile des appels**.  
  
## <a name="see-also"></a>Voir aussi  
 [Questions fréquentes (FAQ) sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
