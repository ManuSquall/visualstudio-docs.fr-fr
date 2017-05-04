---
title: "JsIdle, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIdle"
helpviewer_keywords: 
  - "JsIdle (fonction)"
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsIdle, fonction
Indique au runtime d'effectuer le traitement des temps d'inactivité nécessaire.  
  
## Syntaxe  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### Paramètres  
 `nextIdleTick`  
 Prochain cycle du système à partir duquel du travail inactif supplémentaire est à effectuer.  Peuvent avoir la valeur null.  Retourne le nombre maximal de cycles si aucun travail inactif supplémentaire n'est prévu.  
  
## Valeur de retour  
 Le code `JsNoError` si l'opération a réussi, sinon un code d'échec.  
  
## Notes  
 Si le traitement des temps d'inactivité a été activé pour le runtime actuel, l'appel de `JsIdle` informe le runtime actuel que l'hôte est inactif et qu'il peut effectuer des tâches de nettoyage de mémoire.  
  
 `JsIdle` peut également retourner le nombre de cycles du système avant que le runtime n'ait du travail inactif supplémentaire à effectuer.  L'appel de `JsIdle` avant que ce nombre de cycles n'ait été atteint ne fonctionne pas.  
  
 Nécessite un contexte de script actif.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)