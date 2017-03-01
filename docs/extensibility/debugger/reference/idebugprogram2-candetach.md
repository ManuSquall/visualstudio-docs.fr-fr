---
title: IDebugProgram2::CanDetach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fba40d6cb4d2e9fc3a26b6df34f5d18cdb0401b6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Détermine si un moteur de débogage (DE) permettre détacher du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si pouvez le détacher, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `S_FALSE` si le programme ne peut pas détacher le DE.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
