---
title: IDebugProcessSecurity::GetUserName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 909c4b4e47bdc9de60b9761974843b370c7400e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtient le nom d’utilisateur du fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="remarks"></a>Remarques  
 `GetUserName`Retourne le nom d’utilisateur qui s’affiche dans le **nom d’utilisateur** colonne de la **attacher au processus** boîte de dialogue. Pour afficher le **attacher au processus** boîte de dialogue, cliquez sur **attacher au processus** sur la **outils** menu dans le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)