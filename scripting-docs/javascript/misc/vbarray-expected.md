---
title: VBArray attendu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064941"
---
# <a name="vbarray-expected"></a>VBArray attendu
Vous avez fourni un objet qui n’était pas un safeArray de Visual Basic, lorsqu’une seule était attendue.  
  
```js
new VBArray(safeArray);  
```  
  
 Les objets VBArray sont en lecture seule et ne peuvent pas être créés directement. L’argument safeArray est une valeur VBArray et doit avoir obtenu une valeur VBArray avant d’être passée à la `VBArray` constructeur. Cela n’est possible qu’en récupérant la valeur à partir d’un objet ActiveX ou autre existant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous de vous transmettre uniquement **VBArray** des objets sur le **VBArray** constructeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)