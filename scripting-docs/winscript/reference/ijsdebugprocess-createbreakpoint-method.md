---
title: "IJsDebugProcess::CreateBreakPoint, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess::CreateBreakPoint, m&#233;thode
Définit le point d'arrêt à la position spécifiée de document.  
  
## Syntaxe  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### Paramètres  
 `documentId`  
 \[in\] Pointeur vers IDebugDocumentText.  
  
 `characterOffset`  
 \[in\] Décalage des caractères par rapport au début du fichier.  
  
 `characterCount`  
 \[in\] Longueur du texte du document dans lequel le point d'arrêt doit être inséré.  
  
 `isEnabled`  
 \[in\] Spécifie si le point d'arrêt est activé.  
  
 `ppDebugBreakPoint`  
 \[out\] Objet représentant le point d'arrêt créé.  
  
## Valeur de retour  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugProcess, interface](../../winscript/reference/ijsdebugprocess-interface.md)