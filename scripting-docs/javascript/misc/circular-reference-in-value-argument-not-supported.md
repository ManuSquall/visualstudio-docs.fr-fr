---
description: Une tentative a été effectuée pour appeler JSON. stringify avec une valeur qui n’est pas valide.
title: Référence circulaire dans l’argument de valeur non prise en charge | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88e4ead99f8c59a1300d018bff9d3e81b0874b51
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571140"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Référence circulaire dans l’argument de valeur non prise en charge
Une tentative a été effectuée pour appeler `JSON.stringify` avec une valeur qui n’est pas valide. L' `value` argument, un tableau ou un objet, contient une référence circulaire.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez la référence circulaire de l’argument.  
  
## <a name="example"></a>Exemple  
 Le code de cet exemple provoque une erreur d’exécution, car `john` a une référence à `mary` et `mary` a une référence à `john` . pour supprimer la référence circulaire, supprimez ou annulez la propriété `brother` de l' `mary` objet ou de la `sister` propriété de l' `john` objet.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse, fonction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Erreurs d’exécution JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
