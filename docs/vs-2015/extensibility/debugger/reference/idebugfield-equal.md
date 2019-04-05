---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952170"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode compare ce champ avec le champ spécifié pour l’égalité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pField`  
 [in] Champ à comparer à celui-ci.  
  
## <a name="return-value"></a>Valeur de retour  
 Si les champs sont identiques, retourne `S_OK`. Si les champs sont différents, retourne `S_FALSE.` sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
