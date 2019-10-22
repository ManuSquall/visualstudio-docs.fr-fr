---
title: Valeur booléenne attendue | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576058"
---
# <a name="boolean-expected"></a>Booléen attendu
Vous avez tenté d’appeler la méthode **Boolean. prototype. ToString** ou **Boolean. prototype. valueOf** sur un objet d’un type autre que `Boolean`. L’objet de ce type d’appel doit être de type `Boolean`. Exemple :

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Appelez uniquement les méthodes **Boolean. prototype. ToString** ou **Boolean. prototype. valueOf** sur les objets de type **Boolean.**

## <a name="see-also"></a>Voir aussi

- [Objet booléen](../../javascript/reference/boolean-object-javascript.md)
- [Types de données](../../javascript/data-types-javascript.md)
- [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)
- [Copie, passage et comparaison de données](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)