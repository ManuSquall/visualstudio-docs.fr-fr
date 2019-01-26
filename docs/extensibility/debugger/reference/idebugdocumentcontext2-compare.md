---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06fe3b1c2acffa47f7c47f5f9426fb1d07bbf288
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937832"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compare ce contexte de document dans un tableau des contextes de document donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `compare`  
 [in] Une valeur comprise entre le [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) énumération qui spécifie le type de comparaison.  
  
 `rgpDocContextSet`  
 [in] Un tableau de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objets qui représentent les contextes de document en cours de comparaison.  
  
 `dwDocContextSetLen`  
 [in] La longueur du tableau de contextes de document à comparer.  
  
 `pdwDocContext`  
 [out] Retourne l’index dans le `rgpDocContextSet` tableau du premier contexte de document qui satisfait à la comparaison.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` si une correspondance a été trouvée. Retourne `S_FALSE` si aucune correspondance n’a été trouvée. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objets qui sont passés dans le tableau doivent être implémentées par le même moteur de débogage qui implémente le `IDebugDocumentContext2` de l’objet qui est appelée ; sinon, la comparaison n’est pas valide.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)