---
title: NAME_MATCH | Microsoft Docs
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
- NAME_MATCH
helpviewer_keywords:
- NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2fc955631712dc02f78d920987f1ffb89c836b24
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252575"
---
# <a name="namematch"></a>NAME_MATCH
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sélectionne l’option de casse pour les noms correspondants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument aux méthodes suivantes :  
  
-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)  
  
-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)  
  
-   [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)  
  
-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)

