---
title: Référence circulaire dans l’argument de valeur non prise en charge | Microsoft Docs
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
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572339"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Référence circulaire dans l’argument de valeur non prise en charge
Une tentative a été effectuée pour appeler `JSON.stringify` avec une valeur qui n’est pas valide. L’argument `value`, un tableau ou un objet, contient une référence circulaire.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez la référence circulaire de l’argument.  
  
## <a name="example"></a>Exemple  
 Le code de cet exemple provoque une erreur d’exécution, car `john` a une référence à `mary` et `mary` a une référence à `john`. pour supprimer la référence circulaire, supprimez ou annulez la `brother` de la propriété de l’objet `mary` ou de la propriété `sister` de l’objet `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 d' [objets JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 de la [fonction JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [Erreurs d’exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)