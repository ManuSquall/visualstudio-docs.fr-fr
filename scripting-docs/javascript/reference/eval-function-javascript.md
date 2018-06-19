---
title: Eval, fonction (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636439"
---
# <a name="eval-function-javascript"></a>eval, fonction (JavaScript)
Prend la valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de code et l’exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Paramètres  
 `codeString`  
 Obligatoire. A `String` valeur contenant valide [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code.  
  
## <a name="remarks"></a>Remarques  
 Le `eval` fonction permet l’exécution dynamique de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] le code source.  
  
 Le `codeString` chaîne est analysée par le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] analyseur et exécuté.  
  
 Le code passé à la `eval` fonction est exécutée dans le même contexte que l’appel à la `eval` (fonction).  
  
 Si possible, utilisez le [fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md) désérialiser texte JavaScript Objet Notation (JSON). Le `JSON.parse` fonction est plus sûre et s’exécute plus vite que le `eval` (fonction).  
  
## <a name="example"></a>Exemple  
 Le code suivant initialise la variable `myDate` à une date de test.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet String](../../javascript/reference/string-object-javascript.md)