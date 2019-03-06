---
title: IDispError::GetHelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c2c8ae3a3cff2485c50901bb94ced83098e6000
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087488"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Retourne le chemin d’accès du fichier d’aide et l’ID de contexte de la rubrique qui explique l’erreur, si possible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Une erreur spécifique au fournisseur s’est produite.|  
|`E_INVALIDARG`|`pbstrFileName` ou `pdwContext` était NULL.|  
|`E_OUTOFMEMORY`|Le fournisseur n’a pas pu allouer suffisamment de mémoire dans lequel retourner le chemin de fichier d’aide.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le chemin d’accès du fichier d’aide et l’ID de contexte de la rubrique qui explique l’erreur, si possible.  
  
> [!NOTE]
>  Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)