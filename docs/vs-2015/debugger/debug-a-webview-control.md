---
title: Déboguer un contrôle WebView | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f8a4dcc64903b97e3b469fb962777e3b90f84ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729050"
---
# <a name="debug-a-webview-control"></a>Déboguer un contrôle WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)  
  
 Pour inspecter et déboguer des contrôles `WebView` dans une application Windows Runtime, vous pouvez configurer Visual Studio de sorte à attacher le débogueur de scripts au démarrage de l'application. Quand vous démarrez Visual Studio 2013 Update 2, vous avez deux moyens d'interagir avec les contrôles `WebView` à l'aide du débogueur :  
  
-   Ouvrez le [Explorateur DOM](../debugger/quickstart-debug-html-and-css.md) pour un `WebView` instance et inspecter les éléments DOM et étudier les problèmes de style CSS restituée de façon dynamique des modifications aux styles de test.  
  
-   Sélectionnez la page Web ou `iFrame` affiché dans le `WebView` instance en tant que cible dans le [JavaScript Console](../debugger/javascript-console-commands.md) fenêtre et pour interagir avec la page Web à l’aide des commandes de la console. La console fournit un accès au contexte actuel d'exécution du script.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Attacher le débogueur (C#, Visual Basic, C++)  
  
1.  Dans Visual Studio, ajoutez un contrôle `WebView` à votre application Windows Runtime.  
  
2.  Dans l’Explorateur de solutions, ouvrez les propriétés pour le projet en choisissant **propriétés** dans le menu contextuel du projet.  
  
3.  Choisissez **déboguer**. Dans le **processus d’Application** , choisissez **Script**.  
  
     ![Attacher le débogueur de script](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Facultatif) Pour les versions non Express de Visual Studio, désactiver le débogage juste-à-temps (JIT) en choisissant **outils**, **Options**, **débogage**, **juste-à-temps**, et puis désactivant le débogage juste pour le Script.  
  
    > [!NOTE]
    >  En désactivant le débogage juste-à-temps, vous pouvez masquer les boîtes de dialogue pour les exceptions non prises en charge qui se produisent sur certaines pages web. Dans Visual Studio Express, le débogage juste-à-temps est toujours désactivé.  
  
5.  Appuyez sur F5 pour démarrer le débogage.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Utiliser l'Explorateur DOM pour inspecter et déboguer un contrôle WebView  
  
1.  (C#, Visual Basic, C++) Attachez le débogueur de script à votre application. Voir la première section pour des instructions.  
  
2.  Si vous ne l'avez pas déjà fait, ajoutez un contrôle `WebView` à votre application et appuyez sur F5 pour commencer le débogage.  
  
3.  Naviguez jusqu'à la page contenant le ou les contrôles `Webview`.  
  
4.  Ouvrez la fenêtre de l’Explorateur DOM pour le `WebView` contrôle en choisissant **déboguer**, **Windows**, **Explorateur DOM**, puis choisissez l’URL de la `WebView` que vous avez vous voulez inspecter.  
  
     ![Ouverture de l’Explorateur DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     L'Explorateur DOM associé au `WebView` apparaît sous forme d'un nouvel onglet dans Visual Studio.  
  
5.  Afficher et modifier des éléments DOM en direct et les styles CSS, comme décrit dans [styles CSS déboguer à l’aide de l’Explorateur DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Utiliser la fenêtre de la console JavaScript pour inspecter et déboguer un contrôle WebView  
  
1.  (C#, Visual Basic, C++) Attachez le débogueur de script à votre application. Voir la première section pour des instructions.  
  
2.  Si vous ne l'avez pas déjà fait, ajoutez un contrôle `WebView` à votre application et appuyez sur F5 pour commencer le débogage.  
  
3.  Ouvrez la fenêtre de JavaScript Console pour le `WebView` contrôle en choisissant **déboguer**, **Windows**, **JavaScript Console**.  
  
     La fenêtre de la console JavaScript s'ouvre.  
  
4.  Naviguez jusqu'à la page contenant le ou les contrôles `Webview`.  
  
5.  Dans la fenêtre de Console, sélectionnez la page Web ou un `iFrame` affiché par le `WebView` dans contrôler le **cible** liste.  
  
     ![Cibler la sélection dans la fenêtre de console JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  À l'aide de la console, vous pouvez interagir avec un seul `WebView`, `iFrame`, contrat de partage ou traitement web à la fois. Chaque élément requiert une instance distincte de l'hôte de plateforme web (WWAHost.exe). Vous pouvez interagir avec un seul hôte à la fois.  
  
6.  Afficher et modifier les variables dans votre application ou utilisez les commandes de la console, comme décrit dans [Guide de démarrage rapide : déboguer le JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) et [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)



