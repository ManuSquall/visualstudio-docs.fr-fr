---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5bb2ed0b869a400629123687451da61a9355daa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283437"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Construit une instance du champ étant donnée un tableau d’arguments de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cArgs`  
 [in] Nombre d’arguments dans le `ppArgs` tableau.  
  
 `ppArgs`  
 [in] Tableau qui contient les arguments de type. Les arguments de type doivent être de types fermés (génériques non générique ou entièrement instanciés).  
  
 `ppConstructedField`  
 [out] Retourne le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface qui représente le nouveau champ.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les contraintes ne sont pas vérifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

