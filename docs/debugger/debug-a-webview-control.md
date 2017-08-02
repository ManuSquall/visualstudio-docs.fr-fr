---
title: "D&#233;boguer un contr&#244;le WebView | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# D&#233;boguer un contr&#244;le WebView
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique à Windows et Windows Phone](~/docs/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Pour inspecter et déboguer des contrôles `WebView` dans une application Windows Runtime, vous pouvez configurer Visual Studio de sorte à attacher le débogueur de scripts au démarrage de l'application.  Quand vous démarrez Visual Studio 2013 Update 2, vous avez deux moyens d'interagir avec les contrôles `WebView` à l'aide du débogueur :  
  
-   Ouvrez l'[Explorateur DOM](../debugger/quickstart-debug-html-and-css.md) pour une instance `WebView` et inspectez les éléments DOM, examinez les problèmes de style CSS et testez de manière dynamique les modifications de rendu des styles.  
  
-   Sélectionnez la page web ou l'`iFrame` affiché dans l'instance `WebView` en tant que cible dans la fenêtre de la [console JavaScript](../debugger/javascript-console-commands.md), puis interagissez avec la page web à l'aide des commandes de la console.  La console fournit un accès au contexte actuel d'exécution du script.  
  
### Attacher le débogueur \(C\#, Visual Basic, C\+\+\)  
  
1.  Dans Visual Studio, ajoutez un contrôle `WebView` à votre application Windows Runtime.  
  
2.  Dans l'Explorateur de solutions, ouvrez les propriétés du projet en choisissant **Propriétés** dans le menu contextuel du projet.  
  
3.  Sélectionnez **Déboguer**.  Dans la liste **Processus d'application**, choisissez **Script**.  
  
     ![Attacher le débogueur de scripts](../debugger/media/js_dom_webview_script_debugger.png "JS\_DOM\_WebView\_Script\_Debugger")  
  
4.  \(Facultatif\) Pour les versions non Express de Visual Studio, désactivez le débogage juste\-à\-temps en choisissant **Outils**, **Options**, **Débogage**, **Juste\-à\-temps**, puis en désactivant le débogage juste\-à\-temps pour le script.  
  
    > [!NOTE]
    >  En désactivant le débogage juste\-à\-temps, vous pouvez masquer les boîtes de dialogue pour les exceptions non prises en charge qui se produisent sur certaines pages web.  Dans Visual Studio Express, le débogage juste\-à\-temps est toujours désactivé.  
  
5.  Appuyez sur F5 pour démarrer le débogage.  
  
### Utiliser l'Explorateur DOM pour inspecter et déboguer un contrôle WebView  
  
1.  \(C\#, Visual Basic, C\+\+\) Attachez le débogueur de script à votre application.  Voir la première section pour des instructions.  
  
2.  Si vous ne l'avez pas déjà fait, ajoutez un contrôle `WebView` à votre application et appuyez sur F5 pour commencer le débogage.  
  
3.  Naviguez jusqu'à la page contenant le ou les contrôles `Webview`.  
  
4.  Ouvrez la fenêtre de l'Explorateur DOM pour le contrôle `WebView` en choisissant **Déboguer**, **Windows**, **Explorateur DOM**, puis choisissez l'URL du `WebView` que vous voulez inspecter.  
  
     ![Ouverture de l'explorateur DOM](../debugger/media/js_dom_webview.png "JS\_DOM\_WebView")  
  
     L'Explorateur DOM associé au `WebView` apparaît sous forme d'un nouvel onglet dans Visual Studio.  
  
5.  Affichez et modifiez les éléments DOM et les styles CSS actifs comme décrit dans la section [Déboguer les styles CSS avec l’explorateur DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### Utiliser la fenêtre de la console JavaScript pour inspecter et déboguer un contrôle WebView  
  
1.  \(C\#, Visual Basic, C\+\+\) Attachez le débogueur de script à votre application.  Voir la première section pour des instructions.  
  
2.  Si vous ne l'avez pas déjà fait, ajoutez un contrôle `WebView` à votre application et appuyez sur F5 pour commencer le débogage.  
  
3.  Ouvrez la fenêtre de la console JavaScript pour le contrôle `WebView` en choisissant **Déboguer**, **Windows**, **Console JavaScript**.  
  
     La fenêtre de la console JavaScript s'ouvre.  
  
4.  Naviguez jusqu'à la page contenant le ou les contrôles `Webview`.  
  
5.  Dans la fenêtre de la console, sélectionnez la page web ou un `iFrame` affiché par le contrôle `WebView` dans la liste **Cible**.  
  
     ![Sélection cible dans la fenêtre de la console JavaScript](~/docs/debugger/media/js_console_target.png "JS\_Console\_Target")  
  
    > [!NOTE]
    >  À l'aide de la console, vous pouvez interagir avec un seul `WebView`, `iFrame`, contrat de partage ou traitement web à la fois.  Chaque élément requiert une instance distincte de l'hôte de plateforme web \(WWAHost.exe\).  Vous pouvez interagir avec un seul hôte à la fois.  
  
6.  Affichez et modifiez des variables dans votre application ou utilisez les commandes de la console, comme décrit dans les sections [Démarrage rapide : déboguer du code JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) et [Commandes de la console JavaScript](../debugger/javascript-console-commands.md).  
  
## Voir aussi  
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)