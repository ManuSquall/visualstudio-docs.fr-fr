---
description: Soit vous avez tenté d’appeler l’une des méthodes de prototype de fonction sur un objet qui n’était pas un objet de fonction, soit vous avez utilisé un objet dans un contexte d’appel de fonction.
title: Fonction attendue | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99e354118844d7e57f708cf3f2d5653ee1c0fc65
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622606"
---
# <a name="function-expected"></a>Fonction attendue
Soit vous avez tenté d’appeler l’une des méthodes de **prototype de fonction** sur un objet qui n’était pas un `Function` objet, soit vous avez utilisé un objet dans un contexte d’appel de fonction. Par exemple, le code suivant génère cette erreur, car l' **exemple** n’est pas une fonction.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez uniquement les méthodes de **prototype de fonction** sur les `Function` objets.  
  
- Veillez à utiliser l’opérateur d’appel `()` de fonction pour appeler des fonctions uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Propriété prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
