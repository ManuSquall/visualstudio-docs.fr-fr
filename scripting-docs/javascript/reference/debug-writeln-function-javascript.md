---
title: Debug.writeln, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln, fonction (JavaScript)
Envoie les chaînes au débogueur de script, suivi d’un caractère de saut de ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 *str1, str2,..., strN*  
 Facultatif. Chaînes à envoyer au débogueur de script.  
  
## <a name="remarks"></a>Remarques  
 Le `Debug.writeln` fonction envoie des chaînes, suivi par un caractère de saut de ligne, dans la fenêtre exécution du débogueur Microsoft Script en cours d’exécution. Si le script n’est pas en cours de débogage, le `Debug.writeln` fonction n’a aucun effet.  
  
 Le `Debug.writeln` fonction est presque identique à la `Debug.write` (fonction). La seule différence est que le `Debug.write` fonction n’envoie pas un caractère de saut de ligne après l’envoi des chaînes.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `Debug.writeln` fonction pour afficher la valeur de la variable dans la fenêtre exécution du débogueur de Script Microsoft.  
  
> [!NOTE]
>  Pour exécuter cet exemple, vous devez disposer d’un débogueur de script installé et que le script doit être exécuté en mode débogage.  
>   
>  Internet Explorer 8 comprend les [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] débogueur. Si vous utilisez une version antérieure d’Internet Explorer, consultez [Procédure : activation et démarrage du débogage des scripts à partir d’Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet Debug](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Debug.write](../../javascript/reference/debug-write-function-javascript.md)