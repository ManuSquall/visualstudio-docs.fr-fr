---
title: IDispError::GetHelpInfo | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Retourne le chemin d’accès du fichier d’aide et l’ID de contexte de la rubrique qui décrit l’erreur, si possible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrFileName`  
 [out] Chaîne contenant le chemin d’accès qualifié complet du fichier d’aide. S’il n’existe aucun fichier d’aide ou une erreur se produit, la valeur de retour est NULL.  
  
 `pdwContext`  
 [out] L’ID de contexte d’aide pour l’erreur. S’il n’existe aucun fichier d’aide (si `pbstrFileName` a la valeur NULL), ce paramètre n’a aucune signification.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Une erreur spécifique au fournisseur s’est produite.|  
|`E_INVALIDARG`|`pbstrFileName`ou `pdwContext` était NULL.|  
|`E_OUTOFMEMORY`|Le fournisseur n’a pas pu allouer suffisamment de mémoire dans lequel retourner le chemin de fichier d’aide.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne le chemin d’accès du fichier d’aide et l’ID de contexte de la rubrique qui décrit l’erreur, si possible.  
  
> [!NOTE]
>  Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)