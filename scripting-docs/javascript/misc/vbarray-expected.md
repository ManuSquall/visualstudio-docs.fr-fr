---
title: VBArray ATTENDU | Microsoft Docs
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
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572503"
---
# <a name="vbarray-expected"></a>VBArray attendu
Vous avez fourni un objet qui n’était pas un Visual Basic safeArray, alors qu’il était attendu.  
  
```js
new VBArray(safeArray);  
```  
  
 Les objets VBArray sont en lecture seule et ne peuvent pas être créés directement. L’argument safeArray est une valeur VBArray et doit avoir obtenu une valeur VBArray avant d’être passée au constructeur `VBArray`. Cela n’est possible qu’en récupérant la valeur à partir d’un objet ActiveX ou autre existant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Veillez à transmettre uniquement les objets **VBArray** au constructeur **VBArray** .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)    
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)