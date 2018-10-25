---
title: IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5bbb00efe88bda530d7760baa690ce42cb278c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846926"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Cette méthode retourne un `GUID` représentant la langue de ce processus en tant que jeu par un appel à [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostingProcessLanguage(  
   GUID* pguidLang  
);  
```  
  
```csharp  
int GetHostingProcessLanguage(  
   out Guid pguidLang  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pguidLang`  
 [out] Le `GUID` de la langue de ce processus. `GUID_NULL` (C++) ou `Guid.Empty` (c#) signifie que la langue n’est pas définie.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)