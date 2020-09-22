---
title: Déboguer un contrôle WebView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f2da5b3122bd97fcbef0db7124049372c21983f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839902"
---
# <a name="debug-a-webview-control"></a>Déboguer un contrôle WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)  
  
 Pour inspecter et déboguer des contrôles `WebView` dans une application Windows Runtime, vous pouvez configurer Visual Studio de sorte à attacher le débogueur de scripts au démarrage de l'application. Quand vous démarrez Visual Studio 2013 Update 2, vous avez deux moyens d'interagir avec les contrôles `WebView` à l'aide du débogueur :  
  
- Ouvrez l’[Explorateur DOM](../debugger/quickstart-debug-html-and-css.md) pour une instance `WebView` et inspectez les éléments DOM, examinez les problèmes de style CSS et testez de manière dynamique les modifications de rendu des styles.  
  
- Sélectionnez la page web ou l’`iFrame` affiché dans l’instance `WebView` en tant que cible dans la fenêtre de la [console JavaScript](../debugger/javascript-console-commands.md), puis interagissez avec la page web à l’aide des commandes de la console. La console fournit un accès au contexte actuel d'exécution du script.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Attacher le débogueur (C#, Visual Basic, C++)  
  
1. Dans Visual Studio, ajoutez un contrôle `WebView` à votre application Windows Runtime.  
  
2. Dans l’Explorateur de solutions, ouvrez les propriétés du projet en choisissant **Propriétés** dans le menu contextuel du projet.  
  
3. Sélectionnez **Déboguer**. Dans la liste **Processus d’application**, choisissez **Script**.  
  
     ![Attacher le débogueur de scripts](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4. Facultatif Pour les versions non Express de Visual Studio, désactivez le débogage juste-à-temps (JIT) en choisissant **Outils**, **options**, **débogage**, **juste-à-temps**, puis en désactivant le débogage juste-à-temps pour le script.  
  
    > [!NOTE]
    > En désactivant le débogage juste-à-temps, vous pouvez masquer les boîtes de dialogue pour les exceptions non prises en charge qui se produisent sur certaines pages web. Dans Visual Studio Express, le débogage juste-à-temps est toujours désactivé.  
  
5. Appuyez sur F5 pour démarrer le débogage.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Utiliser l'Explorateur DOM pour inspecter et déboguer un contrôle WebView  
  
1. (C#, Visual Basic, C++) Attachez le débogueur de script à votre application. Voir la première section pour des instructions.  
  
2. Si vous ne l'avez pas déjà fait, ajoutez un contrôle `WebView` à votre application et appuyez sur F5 pour commencer le débogage.  
  
3. Naviguez jusqu'à la page contenant le ou les contrôles `Webview`.  
  
4. Ouvrez la fenêtre de l’Explorateur DOM pour le contrôle `WebView` en choisissant **Déboguer**, **Windows**, **Explorateur DOM**, puis choisissez l’URL du `WebView` que vous voulez inspecter.  
  
     ![Ouverture de l'explorateur DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     L'Explorateur DOM associé au `WebView` apparaît sous forme d'un nouvel onglet dans Visual Studio.  
  
5. Affichez et modifiez les éléments DOM en direct et les styles CSS, comme décrit dans [déboguer les styles CSS à l’aide de l’Explorateur DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Utiliser la fenêtre de la console JavaScript pour inspecter et déboguer un contrôle WebView  
  
1. (C#, Visual Basic, C++) Attachez le débogueur de script à votre application. Voir la première section pour des instructions.  
  
2. Si vous ne l'avez pas déjà fait, ajoutez un contrôle `WebView` à votre application et appuyez sur F5 pour commencer le débogage.  
  
3. Ouvrez la fenêtre de la console JavaScript pour le contrôle `WebView` en choisissant **Déboguer**, **Windows**, **Console JavaScript**.  
  
     La fenêtre de la console JavaScript s'ouvre.  
  
4. Naviguez jusqu'à la page contenant le ou les contrôles `Webview`.  
  
5. Dans la fenêtre de la console, sélectionnez la page web ou un `iFrame` affiché par le contrôle `WebView` dans la liste **Cible**.  
  
     ![Sélection cible dans la fenêtre de la console JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    > À l'aide de la console, vous pouvez interagir avec un seul `WebView`, `iFrame`, contrat de partage ou traitement web à la fois. Chaque élément requiert une instance distincte de l'hôte de plateforme web (WWAHost.exe). Vous pouvez interagir avec un seul hôte à la fois.  
  
6. Affichez et modifiez les variables dans votre application ou utilisez les commandes de la console, comme décrit dans [démarrage rapide : déboguer](../debugger/quickstart-debug-javascript-using-the-console.md) les commandes de la console JavaScript et [JavaScript](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)
