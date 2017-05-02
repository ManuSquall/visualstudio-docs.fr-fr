---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
Retourne un énumérateur des frames de pile du thread actuel.  
  
## Syntaxe  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Paramètres  
 `dwSpMin`  
 \[in\]  la limite inférieure d'adresse pour énumérer des frames de pile.  
  
 `ppedsf`  
 \[out\]  Énumérateur des frames de pile du thread actuel.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 L'énumérateur du frame de pile retourne les frames de départ en haut de la pile, avec le frame récemment enfoncé.  L'énumérateur contient uniquement des frames de pile avec des adresses supérieur ou égal à `dwSpMin`.  
  
## Voir aussi  
 [IDebugStackFrameSnifferEx, interface](../../winscript/reference/idebugstackframesnifferex-interface.md)