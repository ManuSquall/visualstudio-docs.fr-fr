---
title: Promise, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61e5611dd0d455c7e7b704777cc2341ca43a2404
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="promise-object-javascript"></a>Promise, objet (JavaScript)
Fournit un mécanisme permettant de planifier le travail à effectuer sur une valeur qui n'a pas encore été calculée. Il s'agit d'une abstraction pour la gestion des interactions avec des API asynchrones.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### <a name="parameters"></a>Paramètres  
 `promise`  
 Obligatoire. Nom de la variable à laquelle la promesse est assignée.  
  
 `resolve`  
 Obligatoire. Fonction qui s'exécute pour indiquer que la promesse a correctement été réalisée.  
  
 `reject`  
 Facultatif. Fonction qui s'exécute pour indiquer que la promesse a été rejetée avec une erreur.  
  
## <a name="remarks"></a>Remarques  
 Une promesse doit être réalisée avec une valeur ou rejetée avec une raison. La méthode `then` de l'objet Promise s'exécute quand la promesse est réalisée ou rejetée, selon ce qui se produit en premier. Si la promesse est réalisée avec succès, la fonction de gestionnaire des réalisations de la méthode `then` s'exécute. Si la promesse est rejetée, la fonction de gestionnaire d'erreurs de la méthode `then` (ou la méthode `catch` ) s'exécute.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment appeler une fonction (`timeout`) qui retourne une promesse. Le gestionnaire des réalisations de la méthode `then` s'exécute après l'expiration du délai d'attente de 5 000 ms.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="example"></a>Exemple  
 Vous pouvez également chaîner des appels à la méthode `then` comme illustré dans le code suivant. Chaque gestionnaire d'achèvement doit retourner une promesse pour prendre en charge le chaînage. Dans ce code, qui appelle la même fonction `timeout`, le premier appel au délai d'attente est retourné après 1 000 ms. Le premier gestionnaire d'achèvement appelle `timeout` une nouvelle fois et cette promesse est retournée après 2 000 ms. Son gestionnaire d'achèvement génère alors une erreur. Le gestionnaire d'erreurs appelle `Promise.all`, qui retourne une valeur uniquement quand les deux appels au délai d'attente sont réalisés ou rejetés.  
  
```JavaScript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant décrit les fonctions de l'objet `Promise`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Promise.All, fonction](../../javascript/reference/promise-all-function-promise.md)|Joint plusieurs promesses et retourne une valeur uniquement quand toutes les promesses spécifiées ont été réalisées ou rejetées.|  
|[Promise.race, fonction](../../javascript/reference/promise-race-function-promise.md)|Crée une promesse à résoudre ou rejeter avec la même valeur de résultat que la première promesse à résoudre ou rejeter parmi les arguments transmis.|  
|[Promise.Reject, fonction](../../javascript/reference/promise-reject-function-promise.md)|Crée une promesse rejetée avec un résultat égal à l’argument transmis.|  
|[Promise.Resolve, fonction](../../javascript/reference/promise-resolve-function-promise.md)|Crée une promesse résolue avec un résultat égal à son argument.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant décrit les méthodes de l'objet `Promise`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode catch](../../javascript/reference/catch-method-promise.md)|Vous permet de spécifier le travail à effectuer sur le rejet d'une promesse.|  
|[Méthode Then](../../javascript/reference/then-method-promise.md)|Vous permet de spécifier le travail à effectuer sur la réalisation d'une promesse.|