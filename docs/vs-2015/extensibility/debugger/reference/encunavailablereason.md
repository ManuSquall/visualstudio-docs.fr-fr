---
title: EncUnavailableReason | Microsoft Docs
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
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ec7c652fd2a35aa927cb5c634fea3cdf9b19ee3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784011"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Représente les raisons qui **Modifier & Continuer** n’est pas disponible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 ENCUN_NONE  
 Aucune raison spécifique pourquoi Modifier & Continuer n’est pas disponible.  
  
 ENCUN_INTEROP  
 Modifier & Continuer n’est pas disponible pendant un appel InterOp.  
  
 ENCUN_SQLCLR  
 Modifier & Continuer n’est pas disponible pendant un appel de procédure SQL qui utilise le Common Language Runtime (CLR).  
  
 ENCUN_MINIDUMP  
 Modifier & Continuer n’est pas disponible lors du traitement d’un minidump.  
  
 ENCUN_EMBEDDED  
 Modifier & Continuer n’est pas disponible lors du traitement du code incorporé.  
  
 ENCUN_ATTACH  
 Modifier & Continuer n’est pas disponible, car la session a été attachée à, pas lancé par le débogueur.  
  
 ENCUN_WIN64  
 Modifier & Continuer n’est pas disponible lors du traitement du code de Windows 64 bits.  
  
## <a name="remarks"></a>Notes  
 Cette énumération est par rapport à un usage interne uniquement par [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Le [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) et [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) méthodes implémenté par un fournisseur de port personnalisé doivent toujours retourner `E_NOTIMPL`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.idl  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

