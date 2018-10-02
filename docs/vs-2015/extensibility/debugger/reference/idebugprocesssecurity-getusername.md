---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0dee5cd71cc41c8377914ade5800976d9e7ff57
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508073"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProcessSecurity::GetUserName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity-getusername).  
  
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

