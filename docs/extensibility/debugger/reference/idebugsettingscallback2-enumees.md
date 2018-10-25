---
title: IDebugSettingsCallback2::EnumEEs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe4d3d2f2a3d76bbaec8c92c8053bac07e352389
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812086"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Énumère les évaluateurs d’expression disponible étant données les identificateurs de langue et le fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```csharp  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celtBuffer`  
 [in] Nombre d’éléments dans le `pceltEEs` mémoire tampon.  
  
 `rgguidLang`  
 [in, out] Identificateur unique pour le langage de programmation.  
  
 `rgguidVendor`  
 [in, out] Identificateur unique pour le fournisseur.  
  
 `pceltEEs`  
 [in, out] Tableau des évaluateurs d’expression.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)