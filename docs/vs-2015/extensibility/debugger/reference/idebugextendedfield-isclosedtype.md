---
title: IDebugExtendedField::IsClosedType | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a566f5dc7d498a9b07d132abe35b279cbc83155d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495267"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugExtendedField::IsClosedType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugextendedfield-isclosedtype).  
  
Détermine si le champ représente un type fermé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si le champ est un type fermé, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

