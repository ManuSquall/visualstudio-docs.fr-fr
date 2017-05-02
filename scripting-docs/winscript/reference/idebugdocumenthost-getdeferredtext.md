---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
Retourne une plage de caractères qui ont été ajoutés à l'aide de la méthode d' `IDebugDocumentHelper::AddDeferredText` , dans le document d'hôte d'origine.  
  
## Syntaxe  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Paramètres  
 `dwTextStartCookie`  
 \[in\]  cookie hôte défini qui représente la position de départ du texte.  
  
 `pcharText`  
 \[in, out\]  Une mémoire tampon de caractères.  Cette méthode ne retourne pas de caractères si ce paramètre est `NULL`.  
  
 `pstaTextAttr`  
 \[in, out\]  une mémoire tampon d'attribut de caractère.  Cette méthode ne retourne pas d'attributs si ce paramètre est `NULL`.  
  
 `pcNumChars`  
 \[in, out\]  Indique le nombre réel de characters\/d'attributs retournés.  Ce paramètre doit avoir la valeur zéro avant d'appeler cette méthode.  
  
 `cMaxChars`  
 \[in\]  le nombre maximal de caractères à retourner.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|  
  
## Notes  
 Cette méthode peut retourner `E_NOTIMPL`, si l'hôte n'appelle pas `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Cette méthode retourne le texte du document d'origine.  L'hôte ne contient pas les modifications apportées ou d'autres modifications au document.  
  
## Voir aussi  
 [IDebugDocumentHost, interface](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR, énumération](../../winscript/reference/source-text-attr-enumeration.md)