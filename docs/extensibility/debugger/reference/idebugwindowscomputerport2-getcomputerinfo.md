---
title: IDebugWindowsComputerPort2::GetComputerInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e222eda1553e5fc608f1d34ab34d27da97cd650
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912946"
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
Récupère des informations sur l’ordinateur sur lequel le débogueur dans en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetComputerInfo(  
   COMPUTER_INFO * pInfo  
);  
```  
  
```csharp  
public int GetComputerInfo(  
   out COMPUTER_INFO[] pInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pInfo`  
 [out] Référence à une structure qui contient les informations de l’ordinateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)   
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)