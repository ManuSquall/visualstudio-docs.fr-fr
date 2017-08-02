---
title: "D&#233;boguer les styles CSS avec l’explorateur DOM | Microsoft Docs"
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
helpviewer_keywords: 
  - "styles CSS [applications Windows Store], débogage"
  - "règles CSS [applications Windows Store], débogage"
  - "débogage CSS [applications Windows Store]"
  - "débogage, règles CSS [applications Windows Store]"
  - "débogage HTML [applications Windows Store]"
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# D&#233;boguer les styles CSS avec l’explorateur DOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique à Windows et Windows Phone](~/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Quand vous déboguez des applications Windows Store, des applications Windows Phone Store et des applications créées avec Visual Studio Tools pour Apache Cordova, vous pouvez afficher et modifier les règles CSS pour les éléments DOM sélectionnés et leurs éléments enfants.  
  
 Les onglets **Styles** et **Calculé** de l’explorateur DOM affichent les règles CSS qui s’appliquent à un élément sélectionné. Les règles s’affichent dans l’ordre de leur spécificité en fonction des règles de priorité CSS. Dans un onglet, les règles situées en haut d’un sélecteur ou d’un style \(les règles les plus spécifiques\) sont les dernières appliquées à l’élément sélectionné, alors que celles situées en bas sont les premières à être appliquées. Quand les règles sont appliquées, elles remplacent celles précédemment appliquées.  
  
 Les onglets **Styles**, **Calculé** et **Modifications** fournissent différentes vues des informations de style.  
  
-   Utilisez l’onglet **Styles** pour afficher les règles organisées par nom de sélecteur CSS, comme `html, body`. Vous pouvez également utiliser cet onglet pour activer ou désactiver des styles spécifiques, modifier manuellement des valeurs, et observer les résultats immédiats de ces modifications.  
  
-   Utilisez l’onglet **Calculé** pour afficher les valeurs calculées d’un style. Par exemple, si vous définissez une taille à 1em, la valeur calculée par Internet Explorer peut être 16px. Les styles de cet onglet sont organisés par nom de style, comme `height`. Vous pouvez également utiliser cet onglet pour activer ou désactiver des styles spécifiques, modifier manuellement des valeurs, et observer les résultats immédiats de ces modifications.  
  
    > [!NOTE]
    >  Dans Visual Studio 2013 Update 2, les informations fournies sous l’onglet **Suivi** ont été fusionnées avec celles de l’onglet **Calculé** et l’onglet **Suivi** a été supprimé.  
  
-   Utilisez l’onglet **Modifications** \(applications Windows Store et Windows Phone Store uniquement\) pour identifier et suivre les styles CSS modifiés au cours d’une session de débogage.  
  
> [!TIP]
>  Les modifications que vous effectuez sous les onglets **Styles** et **Calculé** ne sont pas définitives. Elles ne sont pas conservées quand vous arrêtez le débogage. Pour modifier le code source et recharger les pages sans arrêter ni redémarrer le débogueur, actualisez votre application à l’aide du bouton ![Bouton d'actualisation de l'application Windows](~/debugger/media/js_refresh.png "JS\_Refresh") \(**Actualiser l’application Windows**\) dans la barre d’outils **Déboguer** \(applications Windows Store et Windows Phone Store uniquement\). Pour plus d’informations, consultez [Actualiser une application \(JavaScript\)](../debugger/refresh-an-app-javascript.md).  
  
## Exemple de définition d’une règle CSS  
 Cet exemple montre comment examiner les règles CSS et déboguer un problème de style. Pour cet exemple, supposons que vous souhaitez modifier la couleur d’une police utilisée pour afficher les titres de groupe dans le modèle Application partagée [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].  
  
> [!NOTE]
>  Cet exemple illustre une application Windows Store, mais toutes les fonctionnalités de l’explorateur DOM présentées s’appliquent également à une application Windows Phone Store et, à l’exception de l’onglet Modifications, à une application créée avec Visual Studio Tools pour Apache Cordova.  
  
#### Pour afficher et modifier les règles CSS  
  
1.  Dans Visual Studio, créez une application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] avec JavaScript et HTML dans le modèle de projet Application partagée.  
  
2.  Dans l’**Explorateur de solutions**, ouvrez items.css, qui se trouve dans le dossier Pages.  
  
3.  Remplacez le code CSS suivant :  
  
    ```css  
    .itemspage .itemslist .item { -ms-grid-columns: 1fr; -ms-grid-rows: 1fr 90px; display: -ms-grid; height: 250px; width: 250px; }  
    ```  
  
     par le code :  
  
    ```css  
    .itemspage .itemslist .item { -ms-grid-columns: 1fr; -ms-grid-rows: 1fr 90px; display: -ms-grid; height: 250px; width: 250px; color: #ff6a00; }  
    ```  
  
     Cela ajoute un style qui spécifie la couleur \#ff6a00 \(orange\) pour chaque élément de la liste. Le sélecteur CSS, `.itemspage .itemslist .item`, indique un ensemble de noms de classe pour les éléments DIV dans items.html, qui apparaissent sous forme d’éléments imbriqués dans le modèle DOM en direct. L’élément DIV `item` spécifie les éléments de la liste.  
  
4.  Sélectionnez **Simulateur** dans la liste déroulante de la barre d’outils **Déboguer** \(**Ordinateur local** est la valeur par défaut\).  
  
     ![Sélectionner la liste cible de débogage](../debugger/media/js_select_target.png "JS\_Select\_Target")  
  
5.  Appuyez sur F5 pour exécuter l’application en mode débogage.  
  
     Lorsque le chargement de l’application est terminé, examinez les en\-têtes des éléments de la liste, tels que **Titre de groupe : 1**. La couleur est inchangée, donc la tentative d’application de la couleur orange aux titres n’a pas fonctionné. Nous identifierons le problème et le résoudrons à l’aide des onglets CSS de l’explorateur DOM.  
  
    > [!TIP]
    >  Une fois que l’application s’affiche dans le simulateur, positionnez le simulateur en regard de la fenêtre Visual Studio afin de pouvoir afficher immédiatement les résultats de vos sélections et des modifications que vous apportez aux styles CSS.  
  
6.  Passez dans Visual Studio et cliquez sur **Sélectionner un élément** dans l’explorateur DOM \(ou appuyez sur Ctrl\+B\). Le mode de sélection est alors modifié pour vous permettre de sélectionner un élément en cliquant dessus, et l’application est mise au premier plan. Le mode est restauré à la suite d’un seul clic. Le bouton **Sélectionner un élément** se présente comme suit :![Bouton Sélection d'un élément dans l'explorateur DOM](../debugger/media/js_dom_select_element_button.png "JS\_DOM\_Select\_Element\_Button")  
  
    > [!TIP]
    >  Vous pouvez également sélectionner des éléments HTML directement dans l’explorateur DOM. Pour plus d’informations sur la sélection des éléments, consultez [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7.  Dans le simulateur, amenez le pointeur au\-dessus du titre du premier élément dans la liste, **Titre de groupe : 1**, dans le volet gauche de la page d’accueil. Le titre est mis en surbrillance, comme illustré ci\-après :  
  
     ![Utilisation du bouton Sélection d'un élément](../debugger/media/js_css_select_element.png "JS\_CSS\_Select\_Element")  
  
    > [!NOTE]
    >  L’émulateur Windows Phone ne prend en charge que partiellement la mise en surbrillance des éléments par pointage.  
  
8.  Cliquez sur le titre encadré. L’explorateur DOM sélectionne automatiquement l’élément HTML correspondant, qui ressemble à ce qui suit.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Quand vous sélectionnez l’élément H4 dans l’explorateur DOM, les onglets de l’explorateur DOM affichent désormais les règles associées à ce même élément. L’onglet **Calculé** est illustré ici, avec la propriété `color` ouverte :  
  
     ![Onglet Suivre les styles dans l'explorateur DOM](../debugger/media/js_css_styles.png "JS\_CSS\_Styles")  
  
     Cette vue fournit des informations utiles sur les règles associées au style `color`, notamment :  
  
    -   Le sélecteur CSS que nous avons modifié dans items.css, `.itemspage .itemslist .item`, n’est pas utilisé dans le calcul final de style \(il s’affiche en texte barré\). Plusieurs autres occurrences du style `color` ne sont pas non plus utilisées.  
  
        > [!TIP]
        >  Pour les noms de sélecteur plus longs, le nom complet s’affiche dans une info\-bulle.  
  
    -   La valeur CSS finale calculée, `rgba(255, 255, 255, 0.87)`, est définie spécifiquement pour le sélecteur CSS suivant : `.itemspage .itemslist .item .item-overlay .item-title`, qui est également défini dans items.css.  
  
        > [!TIP]
        >  Maintenant que nous savons où la couleur de titre est définie, nous savons également où nous pouvons la modifier. Toutefois, nous pouvons également tester des modifications dans l’explorateur DOM sans actualiser l’application, comme illustré dans les étapes restantes.  
  
9. Décochez la case de la première occurrence du style `color`, qui se rapporte au sélecteur `.itemspage .itemslist .item .item-overlay .item-title`. Désormais, dans le simulateur, vous constatez que la couleur de tous les titres des éléments devient orange, comme nous le souhaitions, et que le sélecteur que nous avons modifié dans CSS, `.itemspage .itemslist .item`, n’est plus remplacé \(autrement dit, son texte n’est plus barré\). Voici l’onglet **Calculé** une fois la case décochée.  
  
     ![Onglet Calculé après la mise à jour du style CSS](~/debugger/media/js_css_styles_fixed.png "JS\_CSS\_Styles\_Fixed")  
  
10. Sélectionnez l’onglet **Modifications**.  
  
     Utilisez l’onglet **Modifications** pour identifier et suivre les modifications de style effectuées au cours d’une session de débogage. L’illustration suivante présente le sélecteur `.itemspage .itemslist .item .item-overlay .item-title` sous l’onglet **Modifications**, qui est à présent remplacé.  
  
     ![Onglet Modifications de l'explorateur DOM](~/debugger/media/js_css_styles_changes.png "JS\_CSS\_Styles\_Changes")  
  
11. Vous pouvez également modifier manuellement des valeurs de style CSS et voir le résultat immédiat obtenu à l’aide de l’onglet **Styles**.  
  
12. Sélectionnez l’onglet **Styles**.  
  
13. Ouvrez le sélecteur de style `.itemspage .itemslist .item .item-overlay .item-title`.  
  
14. Sélectionnez la première occurrence du style `color`, puis double\-cliquez sur la valeur de propriété `rgb(255, 255, 255, 0.87)`.  
  
15. Utilisez le clavier pour modifier cette valeur. Remplacez\-la par `rgb(255, 255, 0, 0.87)` et appuyez sur Entrée. Les couleurs des titres des éléments dans le simulateur deviennent jaunes.  
  
16. Pour modifier le fichier CSS source, cliquez sur le lien **items.css** sous l’onglet **Styles**. Vous ouvrez ainsi items.css, dans lequel vous pouvez modifier la valeur du style `color` de votre code d’application. Pour actualiser l’application sans arrêter ni redémarrer le débogueur, cliquez sur le bouton ![Bouton d'actualisation de l'application Windows](~/debugger/media/js_refresh.png "JS\_Refresh") \(**Actualiser l’application Windows**\) dans la barre d’outils **Déboguer**.  
  
## Voir aussi  
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Déboguer la disposition avec l’Explorateur DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Afficher les écouteurs d'événements DOM](../debugger/view-dom-event-listeners.md)   
 [Support technique et accessibilité](http://go.microsoft.com/fwlink/?LinkId=253502)