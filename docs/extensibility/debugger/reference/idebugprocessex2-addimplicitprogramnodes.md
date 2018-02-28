---
title: IDebugProcessEx2::AddImplicitProgramNodes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: adc3f54188e57bd5453703c0aa68fe281fd2ca5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Cette méthode ajoute un nœud de programme pour chaque moteur de débogage (DE) spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidLaunchingEngine`  
 [in] Le `GUID` d’un type de données DE qui doit être utilisé pour lancer des programmes (et est supposé pour ajouter des nœuds de son propre programme).  
  
 `rgguidSpecificEngines`  
 [in] Tableau de `GUID`s DEs nœuds seront ajoutés pour le programme.  
  
 `celtSpecificEngines`  
 [in] Le nombre de `GUID`s dans le `rgguidSpecificEngines` tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 [Programmer des nœuds](../../../extensibility/debugger/program-nodes.md) sera ajouté pour chaque DE répertoriées dans `rgguidSpecificEngines`: à l’exception du moteur de lancement (selon les indications dans `guidLaunchingEngine`), qui est censé pour ajouter son propre nœud de programme dans le lancement d’un programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nœuds de programme](../../../extensibility/debugger/program-nodes.md)