---
title: IDebugProcess2::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 557a6f32a6d9b353db1567887e0308e7ba8cac2e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274090"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le titre, le nom convivial ou le nom de fichier du processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `gnType`  
 [in] Une valeur comprise entre le [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) énumération qui spécifie le type de nom à retourner.  
  
 `pbstrName`  
 [out] Retourne le nom du processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)

