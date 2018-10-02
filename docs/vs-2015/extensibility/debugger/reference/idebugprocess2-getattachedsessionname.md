---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ba2ad04d96f8970ca43c4f1a136d2676ed70fad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508678"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProcess2::GetAttachedSessionName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-getattachedsessionname).  
  
Obtient le nom de la session qui est le débogage de ce processus. Un IDE peut afficher ces informations à un utilisateur qui est un processus particulier sur un ordinateur particulier de débogage.  
  
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
 Cette méthode doit toujours retourner `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

