---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ec078650446d3511ed9c5bdc8ee3ec0191487d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951458"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vérifie qu’un fournisseur de port peut ajouter de nouveaux ports.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si le port peut être ajouté, retourne `S_OK`; sinon, retourne `S_FALSE` pour indiquer aucune ports ne peuvent être ajoutés à ce fournisseur de port.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode avant d’appeler le [ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) (méthode), car cette dernière méthode crée le port ainsi que l’ajout, qui pourrait être une opération longue.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
