---
title: IDispError::GetHelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446909"
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
> Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)