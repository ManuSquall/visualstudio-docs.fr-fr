---
title: 'IDebugAlias2 :: GetAppDomainId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79f6a71376d410f6eb0b524a309f5f6dffcdf614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197921"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère l’identificateur pour le domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pappDomainId`  
 à Retourne l’identificateur de domaine d’application.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 L’identificateur de domaine d’application est modifié chaque fois que l’application est redémarrée et qu’un nouveau domaine d’application est créé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
