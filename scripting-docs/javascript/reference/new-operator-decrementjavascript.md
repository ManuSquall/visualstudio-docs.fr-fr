---
title: "New, opérateur (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>new, opérateur (JavaScript)
Crée un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Paramètres  
 `constructor`  
 Obligatoire. Le constructeur de l’objet. Les parenthèses peuvent être omises si le constructeur n’accepte aucun argument.  
  
 `arguments`  
 Facultatif. Tous les arguments à passer au constructeur du nouvel objet.  
  
## <a name="remarks"></a>Remarques  
 Le `new` opérateur effectue les tâches suivantes :  
  
-   Il crée un objet sans membres.  
  
-   Il appelle le constructeur de cet objet, en passant un pointeur vers l’objet qui vient d’être créé en tant que le `this` pointeur.  
  
-   Le constructeur initialise ensuite l’objet selon les arguments passés au constructeur.  
  
 Voici des exemples d’utilisations valides de le **nouveau** opérateur.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction function](../../javascript/reference/function-statement-javascript.md)