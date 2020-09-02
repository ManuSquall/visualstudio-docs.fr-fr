---
title: 'Démarrage rapide : déboguer du code JavaScript à l’aide de la console | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
ms.assetid: ea7adb71-52b6-4a5a-9346-98ca94b06bd7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2256dfde39c761258ffb63ec6bbd9473e1be385
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687584"
---
# <a name="quickstart-debug-javascript-using-the-console"></a>Démarrage rapide : déboguer du code JavaScript à l’aide de la console
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)  
  
 Vous pouvez utiliser la fenêtre de la console JavaScript pour interagir avec les applications du Store développées en JavaScript. Ces fonctionnalités sont prises en charge par les applications du [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , les applications du Windows Phone Store et les applications créées à l’aide de Visual Studio Tools pour Apache Cordova. Pour obtenir la référence des commandes de la console, voir [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
 La fenêtre de la console JavaScript permet les actions suivantes :  
  
- Envoyer des objets, valeurs et messages depuis votre application vers la fenêtre de la console.  
  
- Afficher et modifier les valeurs des variables locales ou globales de l’application en cours d’exécution.  
  
- Afficher les visualiseurs d’objets.  
  
- Exécuter le code JavaScript qui s’exécute au sein du contexte de script actif.  
  
- Afficher les erreurs et les exceptions JavaScript, en plus des exceptions du modèle DOM et Windows Runtime.  
  
- Effectuer d’autres tâches, telles que l’effacement de l’écran. Consultez [JavaScript Console commands](../debugger/javascript-console-commands.md) pour obtenir la liste complète des commandes.  
  
  Dans cette rubrique :  
  
- [Débogage à l’aide de la fenêtre de la console JavaScript](#InteractiveConsole)  
  
- [Débogage interactif et mode arrêt](#InteractiveDebuggingBreakMode)  
  
- [Mode à ligne simple et mode multiligne dans la fenêtre de la console JavaScript](#SinglelineMultilineMode)  
  
- [Basculement du contexte d’exécution du script](#Switching)  
  
> [!TIP]
> Si la fenêtre de la console JavaScript est fermée, choisissez **Déboguer**la > **Windows**  >  **console Windows JavaScript** pour la rouvrir. La fenêtre s’ouvre uniquement pendant une session de débogage de script.  
  
 À l’aide de la fenêtre de la console JavaScript, vous pouvez interagir avec votre application sans interrompre et redémarrer le débogueur. Pour plus d’informations, consultez [actualiser une application (JavaScript)](../debugger/refresh-an-app-javascript.md). Pour plus d’informations sur d’autres fonctionnalités de débogage JavaScript, telles que l’utilisation de l’Explorateur DOM et la définition de points d’arrêt, consultez [démarrage rapide : déboguer des applications HTML et CSS](../debugger/quickstart-debug-html-and-css.md) et [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="debug-by-using-the-javascript-console-window"></a><a name="InteractiveConsole"></a> Déboguer à l’aide de la fenêtre de la console JavaScript  
 La procédure suivante crée une application `FlipView` et montre comment déboguer interactivement une erreur de codage JavaScript.  
  
> [!CAUTION]
> L’exemple utilisé ici est une application du Windows Store. Toutefois, les fonctionnalités de la console décrites ici s’appliquent également aux applications créées à l’aide de Visual Studio Tools pour Apache Cordova.  
  
#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Pour déboguer le code JavaScript dans l’application FlipView  
  
1. Créez une nouvelle solution dans Visual Studio en choisissant **fichier**  >  **nouveau projet**.  
  
2. Choisissez **JavaScript**applications du  >  Windows**Store**JavaScript, applications **Windows** ou **applications Windows Phone**, puis **application vide**.  
  
3. Tapez un nom pour le projet, comme `FlipViewApp`, puis choisissez **OK** pour créer l’application.  
  
4. Dans l’élément BODY de default.html, remplacez le code HTML existant par le code suivant :  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5. Ouvrez default.css et ajoutez le code CSS du sélecteur `#fView` :  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 500px;  
        margin: 25px;  
    }  
    ```  
  
6. Ouvrez default.js et remplacez le code par le code JavaScript suivant :  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var myData = [];  
        for (var x = 0; x < 4; x++) {  
            myData[x] = { flipImg: "/images/logo.png" }  
        };  
  
        var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !==  
                activation.ApplicationExecutionState.terminated) {  
                    // TODO: . . .  
                } else {  
                    // TODO: . . .  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                updateImages();  
            }  
        };  
  
        function updateImages() {  
  
            pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
            pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
            pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var publicMembers = {  
            items: pages  
        };  
  
        WinJS.Namespace.define("Data", publicMembers);  
  
    })();  
    ```  
  
7. Si une cible de débogage n’est pas déjà sélectionnée, sélectionnez **Simulateur** ou, pour Windows Phone, **Emulator 8.1 WVGA 4 pouces 512 Mo** dans la liste déroulante en regard du bouton **Périphérique** de la barre d’outils **Déboguer** :  
  
     ![Sélectionner la liste cible de débogage](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Appuyez sur F5 pour démarrer le débogueur.  
  
     L’application fonctionne mais les images sont absentes. Les erreurs APPHOST dans la fenêtre de console JavaScript indiquent que les images sont absentes.  
  
9. Une fois l' `FlipView` application en cours d’exécution dans le simulateur ou l’émulateur Windows Phone, tapez `Data.items` dans l’invite d’entrée de la fenêtre de la console (à côté du symbole « >> ») et appuyez sur entrée.  
  
     Un visualiseur pour l’objet `items` apparaît dans la fenêtre de la console. Cela indique que l’objet `items` a été instancié et qu’il est disponible dans le contexte de script actif. Dans la fenêtre de la console, cliquez sur les nœuds d’un objet pour afficher les valeurs des propriétés (ou utilisez les touches de direction). Si vous cliquez sur l’objet `items._data` , comme le montre l’illustration suivante, vous pouvez noter que les références à la source de l’image sont incorrectes, comme prévu. Les images par défaut (logo.png) sont encore présentes dans l’objet, et des images manquantes sont intercalées avec des images attendues.  
  
     ![Fenêtre de la console JavaScript](../debugger/media/js-console-window.png "JS_Console_Window")  
  
     Remarquez aussi que l’objet `items._data` comporte bien plus d’éléments que vous ne pouviez le prévoir.  
  
10. À l’invite, tapez `Data.items.push` et appuyez sur Entrée. La fenêtre de console affiche un visualiseur pour la fonction `push` , implémentée dans un fichier projet [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] . Dans cette application, nous utilisons `push` pour ajouter les éléments corrects. Avec un examen peu approfondi avec IntelliSense, nous découvrons qu’il faut utiliser `setAt` pour remplacer les images par défaut.  
  
11. Pour résoudre ce problème en mode interactif sans arrêter la session de débogage, ouvrez default.js et sélectionnez le code suivant dans la fonction `updateImages` :  
  
    ```javascript  
    pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
     Copiez et collez ce code dans l’invite d’entrée de la console JavaScript.  
  
    > [!TIP]
    > Lorsque vous collez plusieurs lignes de code dans l’invite d’entrée de la console JavaScript, l’invite passe automatiquement en mode multiligne. Appuyez sur Ctrl+Alt+M pour activer ou désactiver le mode multiligne. Pour exécuter un script en mode multiligne, appuyez sur Ctrl+Entrée ou sélectionnez le symbole représentant une flèche dans l’angle inférieur droit de la fenêtre. Pour plus d’informations, consultez [Mode à ligne simple et mode multiligne dans la fenêtre de la console JavaScript](#SinglelineMultilineMode).  
  
12. Corrigez les appels de fonction `push` dans l’invite en remplaçant `pages.push` par `Data.items.setAt`. Le code corrigé doit se présenter comme suit :  
  
    ```javascript  
    Data.items.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    Data.items.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    Data.items.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
    > [!TIP]
    > Si vous voulez utiliser l’objet `pages` à la place de `Data.items`, vous devez définir un point d’arrêt dans votre code pour conserver l’objet `pages` dans la portée.  
  
13. Pour exécuter le script, sélectionnez la flèche verte.  
  
14. Appuyez sur Ctrl+Alt+M pour passer l’invite d’entrée de la console en mode à ligne simple, puis sélectionnez **Effacer l’entrée** (le « X » rouge) pour supprimer le code de l’invite d’entrée.  
  
15. Tapez `Data.items.length = 3` à l’invite et appuyez sur Entrée. Cela supprime les éléments étrangers des données.  
  
16. Vérifiez de nouveau le simulateur ou l’émulateur Windows Phone et vous verrez que les images correctes se trouvent sur les pages `FlipView` appropriées.  
  
17. Dans l’explorateur DOM, vous pouvez voir l’élément DIV mis à jour et naviguer dans la sous-arborescence pour rechercher les éléments IMG attendus.  
  
18. Arrêtez le débogage en sélectionnant **Déboguer**  >  **arrêter** le débogage ou en appuyant sur Maj + F5, puis corrigez le code source.  
  
     Pour la page default.html complète contenant l’exemple de code corrigé, consultez [Déboguer un exemple de code HTML, CSS et JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md).  
  
## <a name="interactive-debugging-and-break-mode"></a><a name="InteractiveDebuggingBreakMode"></a> Débogage interactif et mode arrêt  
 Utilisez des points d’arrêt et effectuez une exécution pas-à-pas du code pendant que vous utilisez les outils de débogage JavaScript comme la fenêtre de la console JavaScript. Lorsqu’un programme en cours d’exécution dans le débogueur rencontre un point d’arrêt, le débogueur suspend provisoirement l’exécution du programme. Lorsque l’exécution est suspendue, votre programme passe du mode exécution au mode arrêt. Vous pouvez reprendre manuellement l’exécution à tout moment.  
  
 Lorsqu’un programme est en mode arrêt, vous pouvez utiliser la fenêtre de la console JavaScript pour exécuter les scripts et les commandes valides dans le contexte actif d’exécution du script. Dans cette procédure, nous utiliserons la version corrigée de l’application `FlipView` que vous avez créée précédemment pour illustrer l’utilisation du mode arrêt.  
  
#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Pour définir un point d’arrêt et déboguer l’application  
  
1. Dans le fichier default.html de l' `FlipView` application que vous avez créée précédemment, ouvrez le menu contextuel de la `updateImages()` fonction, puis choisissez **point d’arrêt**  >  **Insérer un point d’arrêt**.  
  
2. Choisissez **Ordinateur local** ou **Emulator 8.1 WVGA 4 pouces 512 Mo** dans la liste déroulante en regard du bouton **Démarrer le débogage** de la barre d’outils **Déboguer** .  
  
3. Choisissez **Déboguer**  >  **Démarrer le débogage**ou appuyez sur F5.  
  
     L’application passe en mode arrêt lorsque l’exécution atteint la fonction `updateImages()` , et la ligne en cours du programme d’exécution est mise en surbrillance en jaune.  
  
     ![Utilisation du mode arrêt avec la console JavaScript](../debugger/media/js-breakmode.png "JS_BreakMode")  
  
     Modifiez les valeurs des variables pour changer immédiatement l’état du programme sans mettre fin à la session de débogage en cours.  
  
4. Tapez `updateImages` à l’invite et appuyez sur Entrée. Un visualiseur pour la fonction apparaît dans la fenêtre de la console.  
  
5. Sélectionnez la fonction dans la fenêtre de la console pour afficher l’implémentation de la fonction.  
  
     L’illustration suivante présente la fenêtre de la console à ce stade.  
  
     ![Fenêtre Console JavaScript affichant un visualiseur](../debugger/media/js-console-function-visualizer.png "JS_Console_Function_Visualizer")  
  
6. Copiez une ligne de la fonction depuis la fenêtre de sortie dans l’invite d’entrée, puis remplacez la valeur d’index par 3 :  
  
    ```javascript  
    pages.setAt(3, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
7. Appuyez sur Entrée pour exécuter la ligne de code.  
  
     Si vous souhaitez parcourir le code ligne par ligne, appuyez sur F11 ou sur F5 pour continuer l’exécution du programme.  
  
8. Appuyez sur F5 pour poursuivre l’exécution du programme. L’application `FlipView` s’affiche, et désormais les quatre pages affichent l’une des images non définies par défaut.  
  
     Pour revenir à Visual Studio, appuyez sur F12 ou Alt+Tab.  
  
## <a name="single-line-mode-and-multiline-mode-in-the-javascript-console-window"></a><a name="SinglelineMultilineMode"></a> Mode à ligne simple et mode multiligne dans la fenêtre de la console JavaScript  
 L’invite d’entrée de la fenêtre de la console JavaScript prend en charge le mode à ligne simple et le mode multiligne. La procédure de débogage interactif de cette rubrique fournit un exemple d’utilisation de ces deux modes. Appuyez sur Ctrl+Alt+M pour basculer entre les modes.  
  
 Le mode à ligne simple fournit l’historique des entrées. Naviguez dans l’historique des entrées à l’aide des touches Haut et Bas. Le mode à ligne simple efface la ligne d’invite d’entrée lorsque vous exécutez les scripts. Pour exécuter un script en mode à ligne simple, appuyez sur Entrée.  
  
 Le mode multiligne n’efface pas l’invite d’entrée lorsque vous exécutez des scripts. Lorsque vous basculez en mode à ligne simple à partir du mode multiligne, vous pouvez effacer la ligne d’entrée en appuyant sur **Effacer l’entrée** (le « X » rouge). Pour exécuter un script en mode multiligne, appuyez sur Ctrl+Entrée ou sélectionnez le symbole représentant une flèche dans l’angle inférieur droit de la fenêtre.  
  
## <a name="switching-the-script-execution-context"></a><a name="Switching"></a> Basculement du contexte d’exécution du script  
 La fenêtre de la console JavaScript vous permet d’interagir avec un seul contexte d’exécution, lequel représente une seule instance de l’hôte de la plateforme web (WWAHost.exe), à la fois. Dans certains scénarios, votre application peut démarrer une autre instance de l’hôte, comme lorsque vous utilisez un `iframe`, un contrat de partage, un traitement web ou un contrôle `WebView` . Si une autre instance de l’hôte est en cours d’exécution, vous pouvez sélectionner un autre contexte d’exécution tout en exécutant l’application en sélectionnant le contexte d’exécution dans la liste **Cible** .  
  
 L’illustration suivante montre la liste Cible dans la fenêtre de la console JavaScript.  
  
 ![Sélection cible dans la fenêtre de la console JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
 Vous pouvez aussi basculer le contexte d’exécution à l’aide de la commande `cd` , mais vous devez connaître le nom de l’autre contexte d’exécution et la référence que vous devez utiliser dans la portée. La liste **Cible** offre le meilleur accès aux autres contextes d’exécution.  
  
## <a name="browser-and-platform-support"></a><a name="BrowserSupport"></a> Navigateurs et plateformes pris en charge  
 La fenêtre de la console JavaScript est prise en charge sur les plateformes suivantes :  
  
- Applications[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] et Windows Phone Store en JavaScript et HTML  
  
- Internet Explorer 11 s’exécutant sur [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Internet Explorer 10 s’exécutant sur [!INCLUDE[win8](../includes/win8-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer des applications dans Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Commandes de la console JavaScript](../debugger/javascript-console-commands.md)   
 [Actualiser une application (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Raccourcis clavier](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Déboguer un exemple de code HTML, CSS et JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Déboguer un contrôle WebView](../debugger/debug-a-webview-control.md)   
 [Support technique et accessibilité](https://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)
