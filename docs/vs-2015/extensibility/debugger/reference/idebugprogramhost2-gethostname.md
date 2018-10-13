---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
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
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f18a0c5531489e8050e20a31b12adc01f77ef06
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292147"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le titre, le nom convivial ou le nom de fichier du processus d’hébergement de ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Une valeur comprise entre le [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) énumération.  
  
 `pbstrHostName`  
 [out] Retourne le nom du processus d’hébergement demandé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Dans une implémentation classique de cette méthode, le `dwType` paramètre est ignoré et un nom convivial de l’ordinateur hôte est retourné. Une autre implémentation possible consiste à passer le `dwType` paramètre à un appel à la [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) méthode pour obtenir le nom.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

