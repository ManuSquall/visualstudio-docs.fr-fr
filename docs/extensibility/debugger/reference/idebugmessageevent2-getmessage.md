---
title: IDebugMessageEvent2::GetMessage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 190d4dab907e1c0934cb91f7fef6f87989569cad
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

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
 [out] Retourne le type du message, en utilisant les conventions de Win32 `MessageBox` (fonction). Consultez le [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) (fonction) pour plus d’informations.  
  
 `pbstrHelpFileName`  
 [dans, out] Retourne le nom de fichier. Peut-être une valeur null (C++) ou une valeur vide (c#) s’il n’existe aucun fichier d’aide.  
  
 `pdwHelpId`  
 [dans, out] Retourne l’identificateur d’aide. Peut être 0 si aucune aide n’est associé au message.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)
