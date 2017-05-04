---
title: "IJsDebugFrame::GetStackRange, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetStackRange, m&#233;thode
Retourne la plage d'adresses absolue du frame de pile JavaScript logique.  
  
## Syntaxe  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### Paramètres  
 `pStart`  
 \[out\] Pointeur de pile le plus bas du frame.  
  
 `pEnd`  
 \[out\] Pointeur de pile le plus haut du frame.  
  
## Valeur de retour  
  
## Notes  
 Cette méthode est utile pour rassembler des traces de la pile entrelacées issues de plusieurs runtimes.  Les pointeurs de pile de début et de fin peuvent comprendre plusieurs frames de pile de machine physique \(pour les frames d'exécution JavaScript interprétés\), démarrer et se terminer au fur et à mesure que la pile passe de l'adresse haute à l'adresse basse.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugFrame, interface](../../winscript/reference/ijsdebugframe-interface.md)