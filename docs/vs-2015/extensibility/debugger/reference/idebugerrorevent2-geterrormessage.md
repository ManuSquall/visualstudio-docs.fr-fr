---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
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
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 516119fbe944b0aeeaa50516cf76a7745a5343f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505590"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugErrorEvent2::GetErrorMessage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugerrorevent2-geterrormessage).  
  
Retourne des informations qui permet la construction d’un message d’erreur explicite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [out] Retourne une valeur de la [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) énumération, qui décrit le type de message.  
  
 `pbstrErrorFormat`  
 [out] Le format du message à l’utilisateur final (consultez « Remarques » pour plus d’informations).  
  
 `hrErrorReason`  
 [out] Le code d’erreur le message concerne.  
  
 `pdwType`  
 [out] Gravité de l’erreur (utiliser les constantes MB_XXX pour `MessageBox`; par exemple, `MB_EXCLAMATION` ou `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Chemin d’accès à un fichier d’aide (défini à une valeur null s’il n’existe aucun fichier d’aide).  
  
 `pdwHelpId`  
 [out] ID de la rubrique d’aide à afficher (défini à 0 s’il n’existe aucune rubrique d’aide).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le message d’erreur doit être mis en forme le long des lignes de `"What I was doing.  %1"`. Le `"%1"` aurait ensuite été remplacé par l’appelant avec le message d’erreur dérivé le code d’erreur (qui est retournée dans `hrErrorReason`). Le `pMessageType` paramètre indique comment le message d’erreur finale doit être affiché à l’appelant.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
