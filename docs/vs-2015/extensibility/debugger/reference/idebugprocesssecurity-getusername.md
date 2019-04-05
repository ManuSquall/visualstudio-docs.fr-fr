---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953058"
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
 [out] Chaîne contenant le nom d’utilisateur.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne `S_OK`. Sinon, elle retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 `GetUserName` Retourne le nom d’utilisateur qui s’affiche dans le **nom d’utilisateur** colonne de la **attacher au processus** boîte de dialogue. Pour afficher le **attacher au processus** boîte de dialogue, cliquez sur **attacher au processus** sur le **outils** menu dans le [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
