---
title: IDebugErrorEvent2::GetErrorMessage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dffd06c7342b77f1e4293d50217a0c6a468bf18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110222"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Retourne des informations qui permet la construction d’un message d’erreur explicite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMessageType`  
 [out] Retourne une valeur de la [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) énumération décrivant le type de message.  
  
 `pbstrErrorFormat`  
 [out] Le format du message à l’utilisateur final (voir la section « Notes »).  
  
 `hrErrorReason`  
 [out] Le code d’erreur le message concerne.  
  
 `pdwType`  
 [out] Gravité de l’erreur (utiliser l’une des constantes pour MB_XXX `MessageBox`; par exemple, `MB_EXCLAMATION` ou `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Chemin d’accès à un fichier d’aide (défini à une valeur null s’il n’existe aucun fichier d’aide).  
  
 `pdwHelpId`  
 [out] ID de la rubrique d’aide à afficher (défini à 0 s’il n’existe aucune rubrique d’aide).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le message d’erreur doit être mis en forme le long des lignes de `"What I was doing.  %1"`. Le `"%1"` aurait ensuite été remplacé par l’appelant par le message d’erreur dérivé le code d’erreur (laquelle est retournée dans `hrErrorReason`). Le `pMessageType` paramètre indique comment le dernier message d’erreur doit être affiché à l’appelant.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)