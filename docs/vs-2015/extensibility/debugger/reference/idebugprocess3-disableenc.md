---
title: IDebugProcess3::DisableENC | Microsoft Docs
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
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b14019d94f322f8822825477e18d60c0a54490c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192138"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode explicitement désactive Modifier & Continuer sur ce processus (et tous les programmes qu’il contient). Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `reason`  
 [in] Une valeur comprise entre le [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
> [!NOTE]
>  Un fournisseur de port personnalisé doit toujours retourner `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
 Une fois modifier et continuer est désactivée pour un processus, il peut être réactivée uniquement en redémarrant le processus.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

