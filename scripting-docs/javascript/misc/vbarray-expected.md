---
description: Vous avez fourni un objet qui n’était pas un Visual Basic safeArray, alors qu’il était attendu.
title: VBArray ATTENDU | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: e344e24b3fbef7b7f119a36513c222e085328072
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572076"
---
# <a name="vbarray-expected"></a>VBArray attendu
Vous avez fourni un objet qui n’était pas un Visual Basic safeArray, alors qu’il était attendu.  
  
```js
new VBArray(safeArray);  
```  
  
 Les objets VBArray sont en lecture seule et ne peuvent pas être créés directement. L’argument safeArray est une valeur VBArray et doit avoir obtenu une valeur VBArray avant d’être passée au `VBArray` constructeur. Cela n’est possible qu’en récupérant la valeur à partir d’un objet ActiveX ou autre existant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Veillez à transmettre uniquement les objets **VBArray** au constructeur **VBArray** .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet VBArray](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Utilisation de tableaux](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
