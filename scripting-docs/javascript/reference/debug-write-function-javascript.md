---
title: Debug.Write, fonction (JavaScript) | Documents Microsoft
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
- Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636299"
---
# <a name="debugwrite-function-javascript"></a>Debug.write, fonction (JavaScript)
Envoie les chaînes au débogueur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 *str1, str2,..., strN*  
 Facultatif. Chaînes à envoyer au débogueur de script.  
  
## <a name="remarks"></a>Remarques  
 Le `Debug.write` fonction envoie les chaînes dans la fenêtre exécution d’un débogueur de script en cours d’exécution. Si le script n’est pas en cours de débogage, le `Debug.write` fonction n’a aucun effet.  
  
 Le `Debug.write` fonction est presque identique à la `Debug.writeln` (fonction). La seule différence est que le `Debug.writeln` fonction envoie un caractère de saut de ligne après l’envoi des chaînes.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `Debug.write` fonction pour afficher la valeur de la variable dans la fenêtre exécution du débogueur de script.  
  
> [!NOTE]
>  Pour exécuter cet exemple, vous devez disposer d’un débogueur de script installé et que le script doit être exécuté en mode débogage.  
>   
>  Internet Explorer 8 comprend les [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] débogueur. Si vous utilisez une version antérieure d’Internet Explorer, consultez [Procédure : activation et démarrage du débogage des scripts à partir d’Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet Debug](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)