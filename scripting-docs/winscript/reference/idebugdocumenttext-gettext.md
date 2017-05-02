---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
Récupère les caractères et\/ou les attributs de caractère associés à un intervalle de caractère\- position.  
  
## Syntaxe  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Paramètres  
 `cCharacterPosition`  
 \[in\]  Position de départ de la plage de la position du caractère.  
  
 `pcharText`  
 \[in, out\]  Une mémoire tampon de caractères.  La mémoire tampon doit être suffisamment grande pour contenir des caractères d' `cMaxChars` .  Si ce paramètre est NULL, la méthode ne retourne pas de caractères.  
  
 `pstaTextAttr`  
 \[in, out\]  une mémoire tampon d'attribut de caractère.  La mémoire tampon doit être suffisamment grande pour contenir des caractères d' `cMaxChars` .  Si ce paramètre est NULL, la méthode ne retourne pas d'attributs.  
  
 `pcNumChars`  
 \[in, out\]  le nombre de caractères\/d'attributs retournés.  Ce paramètre doit avoir la valeur zéro avant d'appeler cette méthode.  
  
 `cMaxChars`  
 \[in\]  Nombre de caractères de la plage de la position du caractère.  Spécifie également le nombre maximal de caractères pour retourner.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode récupère les caractères et\/ou les attributs de caractère associés à une caractère\- position s'étendre.  La plage de la position de caractère est spécifié par une caractère\- position et un certain nombre de caractères.  
  
## Voir aussi  
 [IDebugDocumentText, interface](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE\_TEXT\_ATTR, énumération](../../winscript/reference/source-text-attr-enumeration.md)