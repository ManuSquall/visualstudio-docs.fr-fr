---
title: IDebugProgram2::GetEngineInfo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e242a0d2fa414e4f735d5964d65308a68b58d774
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505901"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProgram2::GetEngineInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getengineinfo).  
  
Obtient le nom et le GUID du moteur de débogage (dé) ce programme en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrEngine`  
 [out] Retourne le nom de la DE ce programme en cours d’exécution.  
  
 `pguidEngine`  
 [out] Retourne le GUID de la DE ce programme en cours d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque dé définit son propre GUID pour l’identification.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

