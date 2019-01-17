---
title: Argument de remplacement non valide | Microsoft Docs
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
ms.openlocfilehash: 0f144e733bf115cc98bf61b23a2ed3e4e3cda1e0
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346213"
---
# <a name="invalid-replacer-argument"></a>Argument de remplacement incorrect
Une tentative a été effectuée pour appeler `JSON.stringify` avec un argument qui n’est pas valide. Le `replacer` argument doit être une fonction ou un tableau.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Modifier le `replacer` argument à une fonction ou un tableau.  
  
## <a name="example"></a>Exemple  
 Le code dans cet exemple génère une erreur d’exécution, car `memberfilter` est un objet au lieu d’une fonction ou un tableau.  
  
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
 [Objet JSON](../../javascript/reference/json-object-javascript.md)   
 [Fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Erreurs d’exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)