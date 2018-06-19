---
title: Affichage du texte dans une page web (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569259"
---
# <a name="displaying-text-in-a-webpage-javascript"></a>Affichage du texte dans une page Web (JavaScript)
Il existe plusieurs façons d'afficher un texte dans une page web. Chacune a ses avantages et ses inconvénients, et prend en charge les utilisations spécifiques.  
  
## <a name="displaying-text"></a>Affichage du texte  
  
-   La méthode recommandée pour afficher du texte consiste à créer un élément et à écrire dans sa propriété textContent.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     Dans cet exemple, la valeur de `text` est « my text ». Toutefois, la valeur résultant de l'obtention ou de la définition de la propriété `textContent` sur un nœud parent peut inclure le contenu texte des enfants du nœud. L'exemple suivant indique que le `textContent` défini sur un nœud enfant est inclus dans la valeur `textContent` du nœud parent :  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     Dans cet exemple, la valeur de `text` est « [nested] ».  
  
-   Vous pouvez également créer un élément et écrire dans sa propriété [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) ou [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx). La définition de ces propriétés n'affecte que le texte de l'élément lui-même, pas de ses enfants. Toutefois, ces propriétés présentent également des inconvénients :  
  
    -   La propriété [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) ne fonctionne pas dans tous les navigateurs. Pour des raisons de compatibilité, il peut être préférable de l’éviter.  
  
    -   La propriété [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) est affectée par les styles CSS et n’apparaît pas si l’élément est masqué.  
  
    -   La propriété [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) obtient et définit les nœuds imbriqués et le texte. Si elle n'est pas sécurisée, elle peut être utilisée pour des attaques d'injection de script. En outre, le fait de la définir sur du texte sans balise HTML supprime tous les nœuds précédemment définis.  
  
-   Vous pouvez utiliser la méthode `document.write` sans avoir à créer un élément. Toutefois, cette méthode efface l'ensemble de la page web entière, ce qui n'est peut-être pas ce que vous souhaitez.  
  
     L'exemple suivant montre l'un des inconvénients de l'utilisation de `document.write`. Le script est destiné à afficher l'heure toutes les 5 secondes, mais il affiche l'heure uniquement deux fois. D'ici à ce que `document.write` soit appelé la deuxième fois, la page a terminé son chargement, et `document.write` désactive ensuite la page entière (appel de `document.open`). À ce stade, la fonction `ShowTime` n'existe plus.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Pour réparer le code précédent, supprimez la ligne de code contenant `document.write` et supprimez le commentaire des deux lignes de code commentées qui suivent.  
  
-   Vous pouvez également utiliser une fonction `alert``prompt` ou `confirm` qui affiche un message dans une fenêtre indépendante. Dans la plupart des cas, il n'est pas recommandé d'utiliser une fenêtre indépendante dans un navigateur web. Les paramètres de la plupart des navigateurs actuels bloquent automatiquement les fenêtres indépendantes, empêchant l'affichage de votre message. De plus, il est possible d'entrer dans une boucle infinie lorsque vous utilisez des fenêtres indépendantes, ce qui empêche l'utilisateur de fermer la page web normalement.