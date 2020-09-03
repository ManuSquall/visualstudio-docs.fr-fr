---
title: 'IDebugProcessSecurity :: GetUserName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202788"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le nom d’utilisateur du fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrUserName`  
 à Chaîne contenant le nom d’utilisateur.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Si la méthode réussit, retourne `S_OK`. Sinon, elle retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 `GetUserName` retourne le nom d’utilisateur affiché dans la colonne **nom d’utilisateur** de la boîte de dialogue **attacher au processus** . Pour afficher la boîte de dialogue **attacher au processus** , cliquez sur **attacher au processus** dans le menu **Outils** de l' [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] environnement de développement intégré (IDE).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
