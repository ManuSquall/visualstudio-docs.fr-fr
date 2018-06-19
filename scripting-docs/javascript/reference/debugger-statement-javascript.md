---
title: débogueur, instruction (JavaScript) | Documents Microsoft
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
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636199"
---
# <a name="debugger-statement-javascript"></a>debugger, instruction (JavaScript)
Suspend l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez placer `debugger` instructions n’importe où dans les procédures pour suspendre l’exécution. À l’aide de la `debugger` instruction est similaire à la configuration d’un point d’arrêt dans le code.  
  
 La `debugger` instruction suspend l’exécution, mais ne pas fermer tous les fichiers ou effacer toutes les variables.  
  
> [!NOTE]
>  La `debugger` instruction n’a aucun effet à moins que le script est en cours de débogage.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `debugger` instruction pour suspendre l’exécution à chaque itération du `for` boucle.  
  
> [!NOTE]
>  Pour exécuter cet exemple, vous devez disposer d’un débogueur de script installé et que le script doit être exécuté en mode débogage.  
>   
>  Internet Explorer 8 comprend les [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] débogueur. Si vous utilisez une version antérieure d’Internet Explorer, consultez [Procédure : activation et démarrage du débogage des scripts à partir d’Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [JavaScript, instructions](../../javascript/reference/javascript-statements.md)   
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)