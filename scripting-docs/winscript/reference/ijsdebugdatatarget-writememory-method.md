---
title: "IJsDebugDataTarget::WriteMemory, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::WriteMemory, m&#233;thode
Lit la mémoire du processus cible.  
  
## Syntaxe  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### Paramètres  
 `address`  
 \[in\] Adresse de base à partir de laquelle écrire la mémoire du processus cible.  
  
 `pMemory`  
 \[in\] Données à écrire dans l'espace d'adressage du processus spécifié.  
  
 `size`  
 \[in\] Nombre d'octets à écrire dans le processus.  
  
## Valeur de retour  
  
## Notes  
 Avant que le transfert de données se produise, le système vérifie que toutes les données de l'adresse de base et que la mémoire de la taille spécifiée est accessible en écriture et, si tel n'est pas le cas, la fonction génère une erreur E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)