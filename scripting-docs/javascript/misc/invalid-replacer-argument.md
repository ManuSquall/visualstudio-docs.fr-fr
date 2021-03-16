---
description: Une tentative a été effectuée pour appeler JSON. stringify avec un argument qui n’est pas valide.
title: Argument de remplacement non valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570893"
---
# <a name="invalid-replacer-argument"></a>Argument de remplacement incorrect
Une tentative a été effectuée pour appeler `JSON.stringify` avec un argument qui n’est pas valide. L' `replacer` argument doit être une fonction ou un tableau.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Remplacez l' `replacer` argument par une fonction ou un tableau.  
  
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
 [Objet JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse, fonction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Erreurs d’exécution JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
