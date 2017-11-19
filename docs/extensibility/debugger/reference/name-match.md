---
title: NAME_MATCH | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NAME_MATCH
helpviewer_keywords: NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce68a98df224ddf3195dda2501210a54920ebb69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="namematch"></a>NAME_MATCH
Sélectionne l’option de casse pour les noms correspondants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
} NAME_MATCH;  
```  
  
```csharp  
public enum NameMatchOptions {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
}  
```  
  
## <a name="members"></a>Membres  
 nmNone  
 Aucune option n'est spécifiée.  
  
 nmCaseSensitive  
 Indique que les noms à mettre en correspondance respectent la casse.  
  
 nmCaseInsensitive  
 Indique que les noms à mettre en correspondance ne respectent pas la casse.  
  
## <a name="remarks"></a>Remarques  
 Passé en tant qu’argument pour les méthodes suivantes :  
  
-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)  
  
-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)  
  
-   [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)  
  
-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)