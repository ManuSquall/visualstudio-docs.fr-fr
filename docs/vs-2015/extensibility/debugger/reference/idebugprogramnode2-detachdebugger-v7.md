---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 756af9cbe89a84ed892fb229fcba01daa8984e1e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780384"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

DÉCONSEILLÉ. N’UTILISEZ PAS.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Une implémentation doit toujours retourner `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]
>  En tant que de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL`.  
  
 Cette méthode est appelée lorsque le débogueur se ferme de façon inattendue. Lorsque cette méthode est appelée, l’Allemagne doit reprendre le programme comme si l’utilisateur détachée à partir de celui-ci. Aucun autre événement de débogage ne doit être envoyé. Le programme doit être dans un état où il pouvant être attachée à partir d’une autre instance du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

