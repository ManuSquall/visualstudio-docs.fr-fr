---
title: "IJsDebugDataTarget::ReadNullTerminatedString, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadNullTerminatedString, m&#233;thode
Lit le nombre de caractères spécifié à partir de la cible.  
  
## Syntaxe  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### Paramètres  
 `address`  
 \[in\] Adresse à partir de laquelle lire.  
  
 `characterSize`  
 \[in\] taille de chaque caractère de la chaîne  
  
 `maxCharacters`  
 \[in\] Nombre maximal de caractères à lire. Les maxCharacters doivent être raisonnables.  Toute demande de plus de 128 Mo de mémoire échouera.  Si la chaîne est supérieure à maxCharacters, la chaîne de résultat est tronquée après maxCharacters.  
  
 `pString`  
 \[out\] Données BSTR lues dans la cible.  
  
## Valeur de retour  
  
## Notes  
 Retourne S\_FALSE s'il est tronqué.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)