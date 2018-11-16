---
title: IDebugWindowsComputerPort2::GetComputerInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb7c2085059bf3d85ff431116881d09bec13bb5c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736111"
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère des informations sur l’ordinateur sur lequel le débogueur dans en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

