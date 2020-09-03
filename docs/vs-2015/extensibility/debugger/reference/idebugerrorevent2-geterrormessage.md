---
title: 'IDebugErrorEvent2 :: GetErrorMessage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4b25e040fe391b0bfbd05159779096e6bad9951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183519"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne des informations qui autorisent la construction d’un message d’erreur explicite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMessageType`  
 à Retourne une valeur de l’énumération [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , décrivant le type de message.  
  
 `pbstrErrorFormat`  
 à Format du message final à l’utilisateur (pour plus d’informations, consultez « Remarques »).  
  
 `hrErrorReason`  
 à Code d’erreur du message.  
  
 `pdwType`  
 à Gravité de l’erreur (utilisez les constantes MB_XXX pour `MessageBox` , par exemple, `MB_EXCLAMATION` ou `MB_WARNING` ).  
  
 `pbstrHelpFileName`  
 à Chemin d’accès à un fichier d’aide (défini sur une valeur null s’il n’y a aucun fichier d’aide).  
  
 `pdwHelpId`  
 à ID de la rubrique d’aide à afficher (défini à 0 s’il n’y a aucune rubrique d’aide).  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Le message d’erreur doit être mis en forme le long des lignes de `"What I was doing.  %1"` . Le `"%1"` serait ensuite remplacé par l’appelant par le message d’erreur dérivé du code d’erreur (qui est retourné dans `hrErrorReason` ). Le `pMessageType` paramètre indique à l’appelant comment le dernier message d’erreur doit être affiché.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
