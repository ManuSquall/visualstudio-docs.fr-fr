---
title: IDebugProcess2::GetAttachedSessionName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34e404fe33858c1db7d9dfb103df7b4e0bb9fb91
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123105"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtient le nom de la session qui est déboguer ce processus. Un IDE peut afficher ces informations à un utilisateur de débogage d’un processus particulier sur un ordinateur particulier.  
  
> [!NOTE]
>  Cette méthode est déconseillée, et son implémentation doit toujours retourner `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode doit toujours renvoyer `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)