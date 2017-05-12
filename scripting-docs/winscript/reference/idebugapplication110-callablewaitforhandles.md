---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
Attend que les handles spécifiés l'un des rapports à tout en fournissant des appels de fibres transversale à publier sur ce thread.  Cette méthode doit être appelée à partir de le thread du débogueur.  
  
> [!IMPORTANT]
>  [IDebugApplication110 \(interface\)](../../winscript/reference/idebugapplication110-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### Paramètres  
 `handleCount`  
 Le nombre de handles d'attente.  
  
 `pHandles`  
 L'ensemble des handles d'attente.  
  
 `pIndex`  
 Lorsque la valeur HRESULT est S\_OK, l'index dans `pHandles` pour le handle qui a été signalé.  
  
## Voir aussi  
 [IDebugApplication110 \(interface\)](../../winscript/reference/idebugapplication110-interface.md)