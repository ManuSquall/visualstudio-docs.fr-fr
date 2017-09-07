---
title: IDebugSettingsCallback2::GetMetricString | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f45e062029f7cb7045b71c61cc122bd8f2cdb864
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
Récupère la chaîne de valeur de la métrique de fonction de son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszType`  
 [in] Type de la mesure.  
  
 `guidSection`  
 [in] Identificateur unique de la section.  
  
 `pszMetric`  
 [in] Nom de la mesure.  
  
 `pbstrValue`  
 [out] Retourne la chaîne de valeur de la mesure.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
