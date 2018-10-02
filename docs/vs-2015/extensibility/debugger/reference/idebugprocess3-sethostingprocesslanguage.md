---
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
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
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f9b849f2da8c834a807286d251cafab8a4c4c27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508796"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProcess3::SetHostingProcessLanguage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage).  
  
Cette méthode définit la langue dans laquelle le processus sera hébergé sous. Ce langage peut ensuite être utilisé par le moteur de débogage (dé) pour charger l’évaluateur d’expression appropriée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHostingProcessLanguage(  
   REFGUID guidLang  
);  
```  
  
```csharp  
int SetHostingProcessLanguage(  
   ref Guid guidLang  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidLang`  
 [in] `GUID` de la langue que l’Allemagne doit utiliser. Spécifiez `GUID_NULL` (C++) ou `Guid.Empty` (c#) pour faire en sorte que l’Allemagne utilisent la langue par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) peut être utilisé pour récupérer le paramètre de langue actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)

