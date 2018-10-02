---
title: IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cb408d0dab0f4f08fd9c905179849f17920d6b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495324"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugSettingsCallback2::GetEEMetricGuid](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid).  
  
Récupère l’identificateur unique pour une métrique d’évaluateur d’expression étant donnée son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```csharp  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidLang`  
 [in] Identificateur unique du langage de programmation.  
  
 `guidVendor`  
 [in] Identificateur unique du fournisseur.  
  
 `pszMetric`  
 [in] Nom de la mesure.  
  
 `pguidValue`  
 [out] Retourne l’identificateur unique de la mesure.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

