---
title: Référence circulaire dans l’argument de valeur non pris en charge | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: a31b56b4b2d568b3bc3fd59f876f5052b9f6faff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063996"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Référence circulaire dans l’argument de valeur non prise en charge
Une tentative a été effectuée pour appeler `JSON.stringify` avec une valeur qui n’est pas valide. Le `value` argument, un tableau ou un objet, contient une référence circulaire.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimer la référence circulaire de l’argument.  
  
## <a name="example"></a>Exemple  
 Le code dans cet exemple génère une erreur d’exécution, car `john` a une référence à `mary` et `mary` a une référence à `john`. Pour supprimer la référence circulaire, soit supprimer ou annuler la définition la propriété `brother` à partir de la `mary` objet ou le `sister` propriété à partir de la `john` objet.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet JSON](../../javascript/reference/json-object-javascript.md)   
 [Fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Erreurs d’exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)