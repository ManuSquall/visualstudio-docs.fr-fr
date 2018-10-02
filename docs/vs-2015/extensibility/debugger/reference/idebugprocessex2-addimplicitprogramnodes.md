---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
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
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2552731cf9150e4e86a7ef4bf6d927aaac33cc7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504662"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProcessEx2::AddImplicitProgramNodes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes).  
  
Cette méthode ajoute un nœud de programme pour chaque moteur de débogage (dé) spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Le `GUID` d’un type de données DE qui doit être utilisée pour lancer des programmes (et est supposé pour ajouter des nœuds de son propre programme).  
  
 `rgguidSpecificEngines`  
 [in] Tableau de `GUID`s DEs quel programme nœuds seront ajoutés.  
  
 `celtSpecificEngines`  
 [in] Le nombre de `GUID`s dans le `rgguidSpecificEngines` tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 [Programmer des nœuds](../../../extensibility/debugger/program-nodes.md) sera ajouté pour chaque dé répertoriées dans `rgguidSpecificEngines`, à l’exclusion du moteur de lancement (selon les indications dans `guidLaunchingEngine`), qui est censé pour ajouter son propre nœud de programme lors du lancement d’un programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nœuds de programme](../../../extensibility/debugger/program-nodes.md)

