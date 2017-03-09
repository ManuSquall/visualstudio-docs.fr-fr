---
title: "Proc&#233;dure pas &#224; pas&#160;: am&#233;lioration de la r&#233;activit&#233; de l&#39;interface utilisateur (HTML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "outils d'analyse des performances, HTML [applications du Windows Store]"
  - "outils d'analyse des performances, JavaScript [applications du Windows Store]"
  - "performances, HTML [applications du Windows Store]"
  - "performances, JavaScript [applications du Windows Store]"
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: am&#233;lioration de la r&#233;activit&#233; de l&#39;interface utilisateur (HTML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique à Windows et Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Cette procédure pas à pas vous guide dans le processus d'identification et de résolution d'un problème de performance à l'aide du [profileur de réactivité de l'interface utilisateur XAML](../profiling/html-ui-responsiveness.md). Le profileur est disponible dans Visual Studio pour les applications Windows Store générées pour Windows en JavaScript. Dans ce scénario, vous créez une application de test de performance qui met à jour les éléments DOM trop fréquemment et vous utilisez le profileur pour identifier et résoudre ce problème.  
  
### Création et exécution de l'application de test de performance  
  
1.  Dans Visual Studio, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans le volet gauche, sélectionnez **JavaScript**, puis **Windows**, **Windows 8**, puis **Universelles** ou **Windows Phone**.  
  
    > [!IMPORTANT]
    >  Les résultats du diagnostic présentés dans cette rubrique sont testés par rapport à une application Windows 8.  
  
3.  Dans le volet central, sélectionnez l'un des modèles de projet vide, comme **Application vide**.  
  
4.  Dans la zone **Nom**, spécifiez un nom, par exemple `JS_Perf_Tester`, puis choisissez **OK**.  
  
5.  Dans l'**Explorateur de solutions**, ouvrez default.html et collez le code suivant entre les balises \<body\> :  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6.  Ouvrez default.css et ajoutez le code CSS suivant :  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7.  Ouvrez default.js et remplacez l'ensemble du code par le code suivant :  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var content;  
        var wrapper;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
  
                    content = document.getElementById("content");  
                    wrapper = document.querySelector(".wrapper");  
  
                    content.addEventListener("click", handler);  
  
                } else {  
                }  
  
                args.setPromise(WinJS.UI.processAll());  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var idx = 0;  
        var count = 0;  
        var max = 5000;  
        var text = ["what", "is", "the", "Matrix?"];  
        var color = ["red", "crimson", "maroon", "purple"];  
  
        function increment() {  
  
            setTimeout(function () {  
  
                idx++;  
                count++;  
  
                if (idx > 3) { idx = 0; }  
                if (count < max) { increment(); }  
  
            }, 1000);  
        }  
  
        function setValues() {  
  
            content = document.getElementById("content");  
            content.removeNode(true);  
  
            var newNode = document.createElement("button");  
            newNode.id = "content";  
            newNode.textContent = text[idx];  
            //newNode.textContent = getData();  
            newNode.style.backgroundColor = color[idx];  
            //newNode.style.animationName = "move";  
            //count++;  
  
            wrapper.appendChild(newNode);  
  
        }  
  
        function update() {  
  
            setTimeout(function () {  
  
                setValues();  
                if (count < max) { update(); }  
            });  
        }  
  
        function handler(args) {  
  
            content.textContent = "eenie";  
            increment();  
            update();  
        }  
  
    })();  
  
    ```  
  
8.  Appuyez sur la touche F5 pour démarrer le débogage. Vérifiez que le bouton **En attente de valeurs** apparaît dans la page.  
  
9. Choisissez **En attente de valeurs** et vérifiez que le texte et la couleur du bouton sont mis à jour toutes les secondes. Ceci est normal.  
  
10. Basculez à nouveau vers Visual Studio \(Alt\+Tab\) et appuyez sur Maj\+F5 pour arrêter le débogage.  
  
     Maintenant que vous avez vérifié que l'application s'exécute, vous pouvez examiner ses performances à l'aide du profileur.  
  
### Analyse des données de performance  
  
1.  Dans la barre d'outils **Déboguer**, dans la liste **Démarrer le débogage**, sélectionnez l'un des émulateurs Windows Phone ou **Simulateur**.  
  
    > [!TIP]
    >  Dans une application du Windows Store, vous pouvez également sélectionner **Ordinateur local** ou **Ordinateur distant** dans cette liste. Toutefois, l'avantage d'utiliser l'émulateur ou le simulateur est que vous pouvez le placer en regard de Visual Studio et basculer facilement entre l'application en cours d'exécution et le profileur de réactivité de l'interface utilisateur HTML. Pour plus d'informations, consultez [Exécuter des applications à partir de Visual Studio](../debugger/run-store-apps-from-visual-studio.md) et [Exécuter des applications du Windows Store sur un ordinateur distant](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2.  Dans le menu **Déboguer**, sélectionnez **Performances et diagnostics**.  
  
3.  Dans **Outils disponibles**, choisissez **Réactivité de l'interface utilisateur HTML**, puis **Démarrer**.  
  
     Dans ce didacticiel, vous allez attacher le profileur au projet de démarrage. Pour plus d'informations sur les autres options, comme l'attachement du profileur à une application installée, consultez [Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md).  
  
     Lorsque vous démarrez le profileur, un message de contrôle de compte d'utilisateur peut demander votre autorisation pour exécuter VsEtwCollector.exe. Cliquez sur **Oui**.  
  
4.  Dans l'application en cours d'exécution, sélectionnez **En attente de valeurs** et patientez environ dix secondes. Vérifiez que le texte et la couleur du bouton sont mis à jour toutes les secondes.  
  
5.  À partir de l'application en cours d'exécution, basculez vers Visual Studio \(Alt\+Tab\).  
  
6.  Choisissez **Arrêter la collecte**.  
  
     Le profileur affiche des informations sous un nouvel onglet dans Visual Studio. Lorsque vous examinez l'utilisation de l'UC et les données de débit visuel \(i\/s\), vous pouvez facilement identifier quelques tendances :  
  
    -   L'utilisation de l'UC augmente considérablement après environ trois secondes \(quand vous avez appuyé sur le bouton **En attente de valeurs**\) et affiche alors un modèle précis des événements \(une combinaison cohérente d'événements de script, de style et de rendu\).  
  
    -   Le débit visuel n'est pas affecté et la valeur d'i\/s reste à 60 tout au long du processus \(autrement dit, aucune image n'est supprimée\).  
  
     Regardons une section standard du graphique d'utilisation de l'UC pour découvrir ce que fait l'application durant cette période de forte activité.  
  
7.  Sélectionnez une seconde partie un\-à\-deux au milieu du graphique d'utilisation de l'UC \(cliquez et faites glisser ou utilisez les touches de tabulation et les touches fléchées\). L'illustration suivante montre le graphique d'utilisation de l'UC lorsqu'une sélection a été effectuée. La zone non grisée correspond à la sélection.  
  
     ![Graphique d'utilisation de l'UC](../profiling/media/js_htmlviz_app_cpu.png "JS\_HTMLViz\_App\_CPU")  
  
8.  Choisissez **Zoom avant**.  
  
     Le graphique change et affiche la période sélectionnée plus en détail. L'illustration suivante montre le graphique d'utilisation de l'UC après avoir effectué un zoom avant. \(Les données spécifiques peuvent varier, mais le modèle général reste le même.\)  
  
     ![Vue avec zoom avant](../profiling/media/js_htmlviz_app_zoom.png "JS\_HTMLViz\_App\_Zoom")  
  
     Les détails de la chronologie dans le volet inférieur présentent un exemple de détails pour la période sélectionnée.  
  
     ![Détails de chronologie](../profiling/media/js_htmlviz_app_details.png "JS\_HTMLViz\_App\_Details")  
  
     Les événements dans les détails de la chronologie confirment les tendances visibles montrées par le graphique d'utilisation de l'UC : de nombreux événements se produisent sur de courtes périodes. La vue Détails de la chronologie indique les événements `Timer`, `Layout` et `Paint`.  
  
9. Utilisez le menu contextuel \(ou cliquez avec le bouton droit\) pour sélectionner l'un des événements `Timer` dans le volet inférieur, puis sélectionnez **Filtrer jusqu'à l'événement**. L'illustration suivante présente un exemple de détails standard pour l'un des événements `Timer` dans cette application de test.  
  
     ![Événement de minuteur](../profiling/media/js_htmlviz_app_timer.png "JS\_HTMLViz\_App\_Timer")  
  
     Différentes informations peuvent être déduites des données. Par exemple :  
  
    -   Chaque événement `Timer`, coloré pour être identifié comme un événement de script, comprend un appel à `document.createElement`, suivi d'un calcul de style et d'un appel à `style.backgroundColor` et `appendChild()`.  
  
    -   Dans le bref intervalle de temps sélectionné \(environ une à deux secondes\), un grand nombre d'événements `Timer`, `Layout` et `Paint` se produisent. Les événements `Timer` se produisent beaucoup plus souvent que ce qui apparaît de la mise à jour effectuée toutes les secondes après le lancement de l'application et l'utilisation du bouton **En attente de valeurs**.  
  
10. Pour lancer une analyse, cliquez sur le lien vers la fonction anonyme pour l'un des événements `Timer` situés dans la partie inférieure gauche du volet. La fonction suivante s'ouvre dans default.js :  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Cette fonction récursive installe une boucle qui appelle la fonction `setValues()`, qui met à jour le bouton dans l'interface utilisateur. En examinant les différents événements de la minuterie dans le profileur, vous découvrez que la plupart ou la totalité des événements de la minuterie découlent de ce code, qui s'exécute trop fréquemment. Le problème semble donc provenir de là.  
  
### Résoudre le problème de performance  
  
1.  Remplacez la fonction `update()` par le code suivant :  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Cette version corrigée du code inclut un délai de 1000 millisecondes qui était absent dans la version antérieure du code, provoquant l'utilisation d'une valeur de délai par défaut. D'après les données du profileur, il semble que la valeur par défaut soit égale à zéro milliseconde, d'où une exécution trop fréquente de la fonction `setValues()`.  
  
2.  Réexécutez le profileur de réactivité de l'interface utilisateur HTML et consultez le graphique d'utilisation de l'UC. Vous constaterez que les événements excessifs ont disparu et que l'utilisation de l'UC s'approche de zéro. Problème résolu \!  
  
## Voir aussi  
 [Réactivité de l’interface utilisateur HTML](../profiling/html-ui-responsiveness.md)