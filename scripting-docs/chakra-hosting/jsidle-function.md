---
title: JsIdle, fonction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsIdle
helpviewer_keywords: JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsidle-function"></a>JsIdle, fonction
Indique au runtime d'effectuer le traitement des temps d'inactivité nécessaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nextIdleTick`  
 Prochain cycle du système à partir duquel du travail inactif supplémentaire est à effectuer. Peuvent avoir la valeur null. Retourne le nombre maximal de cycles si aucun travail inactif supplémentaire n'est prévu.  
  
## <a name="return-value"></a>Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## <a name="remarks"></a>Remarques  
 Si le traitement des temps d'inactivité a été activé pour le runtime actuel, l'appel de `JsIdle` informe le runtime actuel que l'hôte est inactif et qu'il peut effectuer des tâches de nettoyage de mémoire.  
  
 `JsIdle` peut également retourner le nombre de cycles du système avant que le runtime n'ait du travail inactif supplémentaire à effectuer. L'appel de `JsIdle` avant que ce nombre de cycles n'ait été atteint ne fonctionne pas.  
  
 Nécessite un contexte de script actif.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)