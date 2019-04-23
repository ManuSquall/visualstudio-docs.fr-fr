---
title: Déboguer la disposition à l’aide de l’Explorateur DOM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e9292464ee117cf79a249c1c1a0636edb931c1d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063230"
---
# <a name="debug-layout-using-dom-explorer"></a>Déboguer la disposition avec l’Explorateur DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)  
  
 L’onglet **Disposition** de l’Explorateur DOM affiche le [modèle de boîte CSS](http://go.microsoft.com/fwlink/?LinkID=238778) pour l’élément sélectionné dans une application [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , une application du Windows Phone Store ou une application créée à l’aide de Visual Studio Tools pour Apache Cordova. Vous pouvez utiliser cette représentation visuelle du modèle de boîte pour identifier et modifier les valeurs relatives à la disposition qui affectent l’apparence des éléments.  
  
> [!TIP]
>  Les modifications que vous effectuez dans l’onglet **Disposition** ne sont pas définitives. Vous pouvez apporter des modifications permanentes à votre code source, puis actualiser votre application à l’aide du bouton **Actualiser l’application Windows** (applications du Windows Store et Windows Phone Store uniquement) de la barre d’outils Déboguer. Ainsi, vous pouvez éviter de redémarrer le débogueur.  
  
 Pour utiliser l’Explorateur DOM pour modifier les aspects de la disposition qui ne sont pas visibles dans le modèle de boîte, consultez [Guide de démarrage rapide : Déboguer le code HTML et CSS](../debugger/quickstart-debug-html-and-css.md) et [styles CSS déboguer à l’aide de l’Explorateur DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Exemple de résolution d’un problème de disposition  
 Cet exemple montre comment sélectionner un élément de liste dans le modèle Hub/Pivot, interpréter les valeurs du modèle de boîte qui figurent dans l’onglet **Disposition** , puis modifier l’une des valeurs de propriété pour résoudre un problème de disposition.  
  
#### <a name="to-fix-the-layout-issue"></a>Pour résoudre le problème de disposition  
  
1. Dans Visual Studio, créez une application de Store qui utilise le modèle de projet Hub/Pivot.  
  
2. Dans le dossier partagé pages\hub, ouvrez hub.css.  
  
3. Remplacez le code CSS suivant :  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     par le code CSS suivant :  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. Sélectionnez le projet appName.WindowsPhone ou appName.Windows dans l’Explorateur de solutions, puis choisissez **Définir comme projet de démarrage** dans le menu contextuel du projet.  
  
5. Selon votre projet de démarrage, sélectionnez **Emulator 8.1 WVGA 4 pouces 512 Mo** ou **Simulateur** dans la liste déroulante de la barre d’outils Déboguer (**Ordinateur local** est la valeur par défaut).  
  
     ![Sélection d’une cible de débogage](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. Appuyez sur F5 pour exécuter l’application en mode débogage.  
  
7. Ouvrez Section 4 en faisant défiler ou glisser l’écran.  
  
    > [!TIP]
    >  Placez le simulateur ou l’émulateur Windows Phone juste à côté de la fenêtre Visual Studio afin de voir immédiatement les résultats de vos sélections et des modifications que vous apportez aux styles CSS.  
  
     Lors du chargement de Section 4, vous constatez que les images inférieures ne s’affichent pas correctement. Chaque image d’élément apparaît divisée en deux (la moitié gauche étant manquante).  
  
8. Basculez vers Visual Studio et choisissez **Sélectionner un élément** dans l’explorateur DOM (ou appuyez sur Ctrl+B). Le mode de sélection est alors modifié pour vous permettre de sélectionner un élément en cliquant dessus, et l’application est mise en premier plan. Le mode est restauré à la suite d’un seul clic.  
  
    > [!TIP]
    >  Vous pouvez aussi utiliser les touches de direction ou d’autres méthodes pour sélectionner directement les éléments HTML dans l’explorateur DOM. Pour plus d’informations sur la sélection d’éléments, consultez [Guide de démarrage rapide : Déboguer le code HTML et CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. Dans le simulateur ou l’émulateur Windows Phone, sélectionnez la moitié droite grisée des images coupées en deux. La mise en surbrillance apparaît autour de l’élément sélectionné, comme illustré ici dans l’émulateur Windows Phone :  
  
     ![Sélection d’un élément DOM](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    >  Le simulateur accepte que vous pointiez sur les éléments pour afficher la mise en surbrillance de la zone autour des éléments DOM avant que vous n’en sélectionniez un. L’émulateur Windows Phone ne prend pas en charge cette option.  
  
     Lorsque vous sélectionnez un élément DOM, l’explorateur DOM sélectionne automatiquement l’élément IMG correspondant dans Visual Studio. L’élément sélectionné dans l’Explorateur DOM se présente comme suit :  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Cliquez sur l’onglet **Disposition** . Cet onglet montre le modèle de boîte de l’élément sélectionné, comme illustré ici dans l’émulateur Windows Phone.  
  
     ![Onglet Disposition de l’Explorateur DOM](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Cette vue fournit des informations utiles sur l’élément :  
  
    - Les couleurs correspondent à la mise en surbrillance de zone qui apparaît dans le simulateur lorsque vous pointez sur des éléments. La couleur bleu représente le \<img > dimensions de l’élément. La couleur brun tanné représente les valeurs de marge.  
  
    - La marge de gauche (margin-left) est définie, ce qui donne une indication sur la cause du problème, car elle correspond au symptôme (couleur noire dans la partie gauche des images).  
  
    - Les zones qui affichent des valeurs de 0 pixels (par exemple, Remplissage, Bordure et Marge) laissent penser que les propriétés CSS correspondantes ne sont probablement pas définies.  
  
11. Pour voir comment la règle margin-left est appliquée, sélectionnez l’onglet **Calculé** et regardez sous la règle margin-left. Vous pouvez voir que la règle est définie avec une valeur 5em, mais la valeur calculée est égale à 66.66px ou 146.66px, en fonction de votre périphérique cible.  
  
    > [!TIP]
    >  Le **calculé** onglet montre que la règle margin-left est définie dans le `..hubpage .hub. section4 .sub-image-row img` sélecteur CSS, se trouve dans hub.css. Dans cette application de démonstration, c’est là que vous devez apporter la correction.  
  
     Vous pouvez également utiliser l’onglet **Disposition** pour tester des modifications apportées aux valeurs de disposition.  
  
12. Dans l’onglet **Disposition** , sélectionnez **66.66** ou **146.66**, qui apparaît dans la zone **Marge** , à gauche de la zone.  
  
13. Tapez `0` et appuyez sur Entrée. (Vous pouvez également utiliser les touches haut et bas pour modifier la valeur.)  
  
14. Sélectionnez l’autre \<img > éléments dans l’Explorateur DOM et modifiez des valeurs de leur marge de gauche sur 0.  
  
15. Basculez vers le simulateur ou l’émulateur Windows Phone. Les valeurs margin-left mises à jour ont été appliquées aux images de Section 4. Ces valeurs sont aussi mises à jour dans l’onglet **Calculé** sous la règle margin-left.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Déboguer les styles CSS à l’aide de l’Explorateur DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Afficher les écouteurs d’événements DOM](../debugger/view-dom-event-listeners.md)
