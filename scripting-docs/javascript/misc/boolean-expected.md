---
title: Booléen attendu | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868090"
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