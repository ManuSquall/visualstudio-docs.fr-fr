---
title: Déboguer un exemple de code HTML et CSS | Microsoft Docs
description: Recherchez l’exemple de code HTML et CSS utilisé avec un article de débogage de démarrage rapide. Les erreurs qui sont présentes par la conception dans le Guide de démarrage rapide sont corrigées dans cet article.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 14d071d4ab47efd60aa31ecbffe1d7cb873ac6fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865603"
---
# <a name="debug-html-and-css-sample-code"></a>Déboguer des exemples de code HTML et CSS

Le code de cette rubrique est l’exemple de fichier pour le [démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md). Les erreurs présentes par conception dans le guide de démarrage rapide sont résolues dans cette version du code.

## <a name="sample-code"></a>Exemple de code
Le code HTML suivant est utilisé dans la \<body> balise dans le démarrage rapide.

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

Le code CSS suivant montre les ajouts effectués à default.css.

```css
#fView {
    background-color:#0094ff;
    height: 500px;
    margin: 25px;
}
```

L'exemple de code suivant affiche le code JavaScript complet dans default.js. Les références aux espaces de noms WinJS pour ce code se trouvent dans le fichier default.html du modèle.

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
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

        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
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

## <a name="see-also"></a>Voir aussi
- [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)
