---
title: "IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetPathName"
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetPathName
Retourne le chemin d'accès complet et le nom de fichier du document.  
  
## Syntaxe  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### Paramètres  
 `pbstrLongName`  
 \[out\]  Chaîne contenant le chemin d'accès complet et le nom de fichier.  
  
 `pfIsOriginalFile`  
 \[out\]  Valeur booléenne qui indique si le chemin d'accès et le nom de fichier font référence au document d'origine.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Le fichier source ne peut pas être créé ou déterminé.|  
  
## Notes  
 Cette méthode retourne le chemin d'accès complet et le nom de fichier du document.  
  
 Si `pfIsOriginalFile` est FAUX, le chemin d'accès et le nom de fichier dans `pbstrLongName` font référence à un fichier temporaire nouvellement créée.  
  
## Voir aussi  
 [IDebugDocumentTextExternalAuthor, interface](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)