---
title: Argument de remplacement non valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573807"
---
# <a name="invalid-replacer-argument"></a>Argument de remplacement incorrect
Une tentative a été effectuée pour appeler `JSON.stringify` avec un argument qui n’est pas valide. L’argument `replacer` doit être une fonction ou un tableau.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Remplacez l’argument `replacer` par une fonction ou un tableau.  
  
## <a name="example"></a>Exemple  
 Le code de cet exemple provoque une erreur d’exécution, car `memberfilter` est un objet au lieu d’une fonction ou d’un tableau.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 d' [objets JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 de la [fonction JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [Erreurs d’exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)