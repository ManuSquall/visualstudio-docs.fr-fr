---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74a89fafd8d163bfb03be8d29f58eb036be68f82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838567"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Obtient le message à afficher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMessageType`  
 [out] Retourne une valeur de la [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) énumération qui décrit le type du message.  
  
 `pbstrMessage`  
 [out] Retourne le message.  
  
 `pdwType`  
 [out] Retourne le type du message, en utilisant les conventions de Win32 `MessageBox` (fonction). Consultez le [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) (fonction) pour plus d’informations.  
  
 `pbstrHelpFileName`  
 [in, out] Retourne le nom de fichier. Peut-être une valeur null (C++) ou une valeur vide (c#) s’il n’existe aucun fichier d’aide.  
  
 `pdwHelpId`  
 [in, out] Retourne l’identificateur d’aide. Peut être 0 si aucune aide n’est associé au message.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)