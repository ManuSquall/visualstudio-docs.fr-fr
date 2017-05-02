---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
Retourne le chemin d'accès du fichier d'aide et de l'ID de contexte de la rubrique qui décrit l'erreur, si possible.  
  
## Syntaxe  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### Paramètres  
 `pbstrFileName`  
 \[out\]  chaîne contenant le chemin qualifié complet du fichier d'aide.  S'il n'existe aucun fichier d'aide ou une erreur se produit, la valeur de retour est NULL.  
  
 `pdwContext`  
 \[out\]  l'ID de contexte d'aide pour l'erreur.  S'il n'existe aucun fichier d'aide \(si `pbstrFileName` est NULL\), ce paramètre n'a aucune signification.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Une erreur spécifique au fournisseur produite.|  
|`E_INVALIDARG`|`pbstrFileName` ou `pdwContext` est NULL.|  
|`E_OUTOFMEMORY`|Le fournisseur n'a pas pu allouer suffisamment de mémoire dans lequel retourner le chemin d'accès de fichier d'aide.|  
  
## Notes  
 Cette méthode retourne le chemin d'accès du fichier d'aide et de l'ID de contexte de la rubrique qui décrit l'erreur, si possible.  
  
> [!NOTE]
>  Cette méthode n'est pas implémentée.  
  
## Voir aussi  
 [IDispError, interface](../../winscript/reference/idisperror-interface.md)