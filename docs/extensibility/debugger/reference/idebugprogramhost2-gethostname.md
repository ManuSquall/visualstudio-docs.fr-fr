---
title: IDebugProgramHost2::GetHostName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramHost2::GetHostName
helpviewer_keywords: IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17cb56589f9f045b2f478626c47857d5c951494c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtient le titre, le nom convivial ou le nom de fichier du processus d’hébergement de ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwType`  
 [in] Une valeur à partir de la [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) énumération.  
  
 `pbstrHostName`  
 [out] Retourne le nom demandé du processus d’hébergement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Dans une implémentation standard de cette méthode, le `dwType` paramètre est ignoré et un nom convivial de l’ordinateur hôte est retourné. Une autre implémentation possible consiste à passer le `dwType` paramètre à un appel à la [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) méthode pour obtenir le nom.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)