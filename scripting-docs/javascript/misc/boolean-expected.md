---
title: Booléen attendu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
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
ms.openlocfilehash: 82123fe2a38b3de1d6e6c015f47bc5f7edd02791
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840516"
---
# <a name="boolean-expected"></a>Booléen attendu
Vous avez tenté d’appeler le **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** méthode sur un objet d’un type autre que `Boolean`. L’objet de ce type d’appel doit être de type `Boolean`. Exemple :

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Appelez le **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** méthodes sur des objets de type **booléenne.**

## <a name="see-also"></a>Voir aussi

- [Objet Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Types de données](../../javascript/data-types-javascript.md)
- [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)
- [Copie, passage et comparaison de données](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)