---
title: IDebugProgramNode2::DetachDebugger_V7 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
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
ms.openlocfilehash: ea8843a824eb5e1cd0c7bcd658908d7cdaac98ce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
DÉCONSEILLÉE. N’UTILISEZ PAS.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Une implémentation doit toujours retourner `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]
>  En tant que de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], cette méthode n’est plus utilisée et doit toujours renvoyer `E_NOTIMPL`.  
  
 Cette méthode est appelée lorsque le débogueur se ferme de façon inattendue. Lorsque cette méthode est appelée, le DE doit reprendre le programme comme si l’utilisateur détachée à partir de celui-ci. Plus aucun événement de débogage doit être envoyé. Le programme doit être dans un état où il pouvant être attachée à partir d’une autre instance du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
