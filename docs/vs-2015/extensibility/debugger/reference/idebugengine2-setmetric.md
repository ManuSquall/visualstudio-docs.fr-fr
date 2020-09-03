---
title: 'IDebugEngine2 :: SetMetric | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3371925894a32bfe954979d1554d96d3d5bbb140
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182243"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode définit une valeur de Registre appelée métrique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszMetric`  
 dans Nom de la mesure.  
  
 `varValue`  
 dans Spécifie la valeur de la métrique.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Une métrique est une valeur de Registre utilisée pour modifier le comportement d’un moteur de débogage ou pour annoncer les fonctionnalités prises en charge. Cette méthode peut transférer l’appel à la forme appropriée des [applications auxiliaires du kit de développement logiciel (SDK) pour](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) la fonction de débogage `SetMetric` .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
