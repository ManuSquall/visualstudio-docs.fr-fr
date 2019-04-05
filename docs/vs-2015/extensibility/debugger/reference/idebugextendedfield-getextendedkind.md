---
title: IDebugExtendedField::GetExtendedKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe3289652dd7880bd902f397e0c76584fdcda0ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952730"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère le type de champ étendues spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```csharp  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwKind`  
 [in, out] Valeur à partir de la [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) énumération qui définit le type de champ.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
