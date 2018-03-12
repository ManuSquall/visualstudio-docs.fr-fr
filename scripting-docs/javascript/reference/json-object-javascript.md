---
title: "L’objet JSON (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JSON object
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5310132368f665c6734c469a67636d33a08858d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="json-object-javascript"></a>JSON, objet (JavaScript)
Objet intrinsèque qui fournit des fonctions de conversion de valeurs [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] au format JSON (JavaScript Object Notation) et à partir de ce dernier. La fonction `JSON.stringify` sérialise une valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en texte JSON. La fonction `JSON.parse` désérialise du texte JSON pour produire une valeur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
JSON.[method]  
  
```  
  
## <a name="parameters"></a>Paramètres  
 `Method`  
 Requis. Nom de l'une des méthodes de l'objet `JSON`.  
  
## <a name="remarks"></a>Remarques  
 Vous ne pouvez pas créer un objet `JSON` à l'aide de l'opérateur `new`. Une erreur se produit si vous tentez d'effectuer cette opération. Toutefois, vous pouvez remplacer ou modifier l'objet `JSON`.  
  
 Le moteur de script crée l'objet `JSON` lorsque le moteur est chargé. Ses méthodes sont accessibles à votre script à tout moment.  
  
 Pour utiliser l'objet `JSON` intrinsèque, veillez à ne pas le remplacer par un autre objet `JSON` défini dans votre script. Vous devrez peut-être modifier les instructions de script existantes qui détectent la présence d'un objet `JSON` car ces instructions évaluent différemment. Cela est illustré par l'exemple suivant.  
  
```JavaScript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 Dans l'exemple précédent, `!this.JSON` prend la valeur false dans [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)]. Par conséquent, le code contenu dans l'instruction `if` ne s'exécute pas.  
  
## <a name="functions"></a>Fonctions  
 [Fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md)  
  
 [Fonction JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [toJSON, méthode (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Objets JavaScript](../../javascript/reference/javascript-objects.md)   
 [Application exemple de modèle hub (Windows Store)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)