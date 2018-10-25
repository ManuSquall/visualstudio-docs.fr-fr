---
title: GETNAME_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40ee5cb4bf552b04683c4c2119a8c43a595b2105
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900304"
---
# <a name="getnametype"></a>GETNAME_TYPE
Spécifie le type de nom des fichiers à récupérer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Membres  
 GN_NAME  
 Spécifie un nom convivial du document ou de contexte.  
  
 GN_FILENAME  
 Spécifie le chemin d’accès complet du document ou de contexte.  
  
 GN_BASENAME  
 Spécifie un nom de fichier de base au lieu d’un chemin d’accès complet du document ou de contexte.  
  
 GN_MONIKERNAME  
 Spécifie un nom unique du document ou de contexte sous la forme d’un moniker.  
  
 GN_URL  
 Spécifie un nom de l’URL du document ou de contexte.  
  
 GN_TITLE  
 Spécifie un titre du document, le cas échéant.  
  
 GN_STARTPAGEURL  
 Obtient l’URL de page de démarrage pour les processus.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont passées en tant que paramètres à la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), et [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) méthodes pour spécifier le type de nom à retourner.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)