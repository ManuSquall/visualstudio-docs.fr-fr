---
description: Vous avez tenté d’appeler la méthode Boolean. prototype. toString ou Boolean. prototype. valueOf sur un objet d’un type autre que Boolean.
title: Valeur booléenne attendue | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571439"
---
# <a name="boolean-expected"></a>Booléen attendu
Vous avez tenté d’appeler la méthode **Boolean. prototype. ToString** ou **Boolean. prototype. valueOf** sur un objet d’un type autre que `Boolean` . L’objet de ce type d’appel doit être de type `Boolean` . Par exemple :

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Appelez uniquement les méthodes **Boolean. prototype. ToString** ou **Boolean. prototype. valueOf** sur les objets de type **Boolean.**

## <a name="see-also"></a>Voir aussi

- [Objet Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Data types](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Contrôle du flux de programme](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Copie, passage et comparaison de données](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
