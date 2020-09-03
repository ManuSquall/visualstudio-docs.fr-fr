---
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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817669"
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

- [Objet Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Data types](../../javascript/data-types-javascript.md)
- [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)
- [Copie, passage et comparaison de données](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)