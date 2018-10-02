---
title: IDebugPortSupplierLocale2::SetLocale | Microsoft Docs
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
- IDebugPortSupplierLocale2::SetLocale
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a43fe4473cdfb47c5fd8c8435c3e3a7e136c335
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503183"
---
# <a name="idebugportsupplierlocale2setlocale"></a>IDebugPortSupplierLocale2::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugPortSupplierLocale2::SetLocale](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplierlocale2-setlocale).  
  
Définit les paramètres régionaux pour le fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetLocale(  
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wLangID`  
 Identificateur de paramètres régionaux à définir.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplierLocale2](../../../extensibility/debugger/reference/idebugportsupplierlocale2.md)

