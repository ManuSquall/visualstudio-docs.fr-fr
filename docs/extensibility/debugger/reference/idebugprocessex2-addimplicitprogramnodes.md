---
title: IDebugProcessEx2::AddImplicitProgramNodes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117018"
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