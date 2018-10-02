---
title: Afficher les écouteurs d’événements DOM | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eeca4964df8e89511b1a077cace83484c35f44d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494233"
---
# <a name="view-dom-event-listeners"></a>Afficher les écouteurs d'événements DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [écouteurs d’événements DOM de la vue](https://docs.microsoft.com/visualstudio/debugger/view-dom-event-listeners).  
  
S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)  
  
 Le **événements** onglet de l’Explorateur DOM affiche les événements qui sont associés à un élément DOM. Chaque nœud supérieur dans le **événements** onglet représente un événement qui a des abonnés actifs. Le nœud supérieur contient des sous-nœuds qui représentent les écouteurs d'événements inscrits pour l'événement spécifique. En outre, pour afficher les écouteurs d'événements, vous pouvez utiliser cet onglet pour accéder à l'emplacement de l'écouteur d'événements dans le code JavaScript. Les informations contenues dans cette rubrique s'appliquent aux applications de Store conçues à l'aide de HTML et de JavaScript.  
  
 La liste sur le **événements** onglet est dynamique. Si vous ajoutez un écouteur d'événements lorsque l'application est en cours d'exécution, le nouvel écouteur apparaît dans la liste. Pour plus d’informations sur l’ajout et suppression d’écouteurs d’événements, consultez [conseils pour résoudre les problèmes liés aux écouteurs d’événements](#Tips) dans cette rubrique.  
  
> [!NOTE]
>  Écouteurs d’événements pour les éléments de code qui ne sont pas des éléments DOM, tel que `xhr`, n’apparaissent pas sur le **événements** onglet.  
  
## <a name="view-event-listeners-for-dom-elements"></a>Afficher les écouteurs d'événements pour les éléments DOM  
 Cet exemple affiche une application du Windows Phone Store. Les fonctionnalités de l'explorateur DOM décrites ici sont également prises en charge pour les applications du Windows Store.  
  
#### <a name="to-view-event-listeners"></a>Pour afficher les écouteurs d'événements  
  
1.  Dans Visual Studio, créez une application JavaScript qui utilise le modèle de projet Application Pivot Windows Phone.  
  
2.  Avec le modèle est ouvert dans Visual Studio, sélectionnez **Emulator 8.1 WVGA 4 pouces 512 Mo** dans la liste déroulante dans la barre d’outils de débogage dans le débogueur :  
  
     ![Sélection d’une cible de débogage](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
3.  Appuyez sur F5 pour exécuter l'application en mode débogage.  
  
4.  Dans l’application en cours d’exécution, accédez à la **Section 3** élément de tableau croisé dynamique.  
  
5.  Passez dans Visual Studio (Alt+Tab ou F12).  
  
6.  Dans l'explorateur DOM, sélectionnez `Find` dans le coin supérieur droit.  
  
7.  Type `ListView`, puis appuyez sur ENTRÉE.  
  
8.  Si nécessaire, choisissez le **suivant** bouton pour rechercher le `DIV` élément qui représente le `ListView` contrôle (cet élément a un `data-win-control` valeur `WinJS.UI.ListView`).  
  
     L'élément `DIV` doit maintenant être sélectionné dans l'Explorateur DOM.  
  
9. Choisissez le **événements** onglet dans le volet situé à droite de l’Explorateur DOM.  
  
     Vous pouvez maintenant voir les événements contenant des abonnés actifs pour l'élément `DIV`, comme illustré ici.  
  
     ![Onglet événements de l’Explorateur DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")  
  
10. Pour localiser les écouteurs de ces événements, sélectionnez les liens associés du fichier JavaScript.  
  
11. Pour identifier rapidement les écouteurs d'événement des éléments parents dans la hiérarchie DOM, sélectionnez un élément parent dans la liste hiérarchique en bas de l'explorateur DOM.  
  
     ![Sélection d’éléments parents dans la hiérarchie du DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")  
  
     Le **événements** onglet affiche les écouteurs d’événements pour n’importe quel élément que vous choisissez dans la liste hiérarchique.  
  
###  <a name="Tips"></a> Conseils pour résoudre les problèmes liés aux écouteurs d’événements  
 Dans certains scénarios d’application, les écouteurs d’événements doivent être explicitement supprimés à l’aide de [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Utilisez le **événements** onglet dans l’Explorateur DOM pour tester si les écouteurs d’événements ont été supprimés à partir d’éléments DOM lors de l’exécution de code. Voici quelques conseils qui vous aideront à résoudre ces types de problèmes :  
  
-   Pour les applications qui utilisent le modèle de navigation de page unique implémentée dans Visual Studio [modèles de projet](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx), il est généralement pas nécessaire supprimer des écouteurs d’événements inscrits pour les objets, tels que les éléments DOM, qui font partie d’une page. Dans ce scénario, un élément DOM et ses écouteurs d'événements associés ont la même durée de vie et peuvent être récupérés par le garbage collector.  
  
-   Si la durée de vie de l'objet ou de l'élément DOM est différente de l'écouteur d'événements associé, il se peut que vous deviez appeler la méthode `removeEventListener`. Par exemple, si vous utilisez l'événement `window.onresize`, vous devrez peut-être supprimer l'écouteur d'événements si vous quittez la page où vous gérez l'événement.  
  
-   Si `removeEventListener` ne réussit pas à supprimer l'écouteur spécifié, il se peut qu'il soit appelé sur une autre instance de l'objet. Vous pouvez utiliser la [bind, méthode (Function)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) méthode pour résoudre ce problème lorsque vous ajoutez l’écouteur.  
  
-   Pour supprimer un écouteur d’événements qui a été ajouté à l’aide [bind, méthode (Function)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) ou en utilisant une fonction anonyme, stockez une instance de la fonction lorsque vous ajoutez l’écouteur. Voici une seule façon d’utiliser ce modèle sans risque :  
  
    ```javascript  
    // You could use the following code within the constructor function of an object, or  
    // in the ready function of a PageControl object (Store app).  
    this.storedHandler = this._handlerFunc.bind(this);  
    elem.addEventListener('mouseup', this.storedHandler);  
  
    // In this example, add the following code in the PageControl object's unload function.  
    elem.removeEventListener('mouseup', this.storedHandler);  
  
    ```  
  
     Si vous utilisez le code suivant au lieu de stocker une référence à la fonction liée, vous ne pourrez pas supprimer l'écouteur d'événements explicitement :  
  
    ```javascript  
    // Avoid this pattern. No reference to the bound function is available.  
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));  
    ```  
  
-   Vous ne pouvez pas supprimer un écouteur d'événements en utilisant `removeEventListener` si vous l'avez ajouté à l'aide de l'attribut `obj.on<eventname>`, tel que `window.onresize = handlerFunc`.  
  
-   Utiliser l’Analyseur de mémoire JavaScript à [mémoire JavaScript](../profiling/javascript-memory.md) dans votre application. Les écouteurs d'événements qui doivent être explicitement supprimés peuvent apparaître comme une fuite de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide : Déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Déboguer les styles CSS à l’aide de l’Explorateur DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Déboguer la disposition avec l’Explorateur DOM](../debugger/debug-layout-using-dom-explorer.md)



