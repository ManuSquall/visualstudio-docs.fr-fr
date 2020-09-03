---
title: 'IDebugSettingsCallback2 :: enums | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cca998c4cdae8cc5e543a24a5cdfe18369e51b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155209"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Énumère les évaluateurs d’expressions disponibles en fonction des identificateurs de langue et de fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 dans Nombre d’éléments dans la `pceltEEs` mémoire tampon.  
  
 `rgguidLang`  
 [in, out] Identificateur unique du langage de programmation.  
  
 `rgguidVendor`  
 [in, out] Identificateur unique du fournisseur.  
  
 `pceltEEs`  
 [in, out] Tableau d’évaluateurs d’expression.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
