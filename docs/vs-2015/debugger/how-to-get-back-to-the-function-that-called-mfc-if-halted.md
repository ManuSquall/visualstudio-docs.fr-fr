---
title: 'Comment : revenir à la fonction qui a appelé MFC en cas d’arrêt | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9148fb0f3431f7edc0d4b69fdf83ef4b629789f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503416"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Comment : retourner à la fonction qui a appelé l'application MFC en cas d'arrêt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : revenir à la fonction qu’appelé MFC si interrompue](https://docs.microsoft.com/visualstudio/debugger/how-to-get-back-to-the-function-that-called-mfc-if-halted).  
  
REMARQUE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si vous avez utilisé le **rompre** commande sur le **déboguer** menu pour arrêter le programme retrouve dans MFC, et vous êtes sûr que le problème se trouve dans votre code, vous pouvez utiliser la fenêtre Pile des appels pour revenir à votre fonction. Pour plus d’informations, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).  
  
 Il peut arriver que votre code se trouve dans la pompe de messages. Dans ce cas, il n'y a aucun code utilisateur dans la pile des appels. Pour éviter ce problème, vous pouvez utiliser des points d’arrêt (éventuellement avec des conditions et des nombres d’accès) au lieu du **rompre** commande. Pour plus d’informations, consultez [des points d’arrêt et points de trace](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Pour naviguer vers la fonction à partir de laquelle la bibliothèque MFC a été appelée  
  
-   Utilisez le **pile des appels** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)



