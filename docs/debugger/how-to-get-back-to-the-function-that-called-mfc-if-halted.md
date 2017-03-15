---
title: "Comment&#160;: retourner &#224; la fonction qui a appel&#233; l&#39;application MFC en cas d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Break (commande)"
  - "déboguer (MFC), fonctions"
  - "déboguer (MFC), revenir à la fonction appelante"
  - "appels de fonction, revenir à la fonction appelante"
  - "fonctions (C++), débogage"
  - "fonctions (débogueur)"
  - "programmes, arrêter"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Comment&#160;: retourner &#224; la fonction qui a appel&#233; l&#39;application MFC en cas d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si vous avez utilisé la commande **Arrêter** du menu **Déboguer** pour arrêter le programme, que vous vous trouvez dans la bibliothèque MFC et que vous êtes certain que le problème se trouve dans votre code, vous pouvez utiliser la fenêtre Pile des appels pour revenir à votre fonction.  Pour plus d'informations, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).  
  
 Il peut arriver que votre code se trouve dans la pompe de messages.  Dans ce cas, il n'y a aucun code utilisateur dans la pile des appels.  Pour éviter ce problème, vous pouvez utiliser des points d'arrêt \(avec des conditions et des nombres d'accès, éventuellement\) au lieu de la commande **Arrêter**.  Pour plus d'informations, consultez [Breakpoints and Tracepoints](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### Pour naviguer vers la fonction à partir de laquelle la bibliothèque MFC a été appelée  
  
-   Utilisez la fenêtre **Pile des appels**.  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)