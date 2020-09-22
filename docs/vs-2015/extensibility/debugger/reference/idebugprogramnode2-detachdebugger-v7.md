---
title: IDebugProgramNode2 ::D etachDebugger_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839718"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Déconseillé. N’UTILISEZ PAS.  
  
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
 Une implémentation doit toujours retourner `E_NOTIMPL` .  
  
## <a name="remarks"></a>Remarques  
  
> [!WARNING]
> À partir de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL` .  
  
 Cette méthode est appelée lorsque le débogueur se ferme de manière inattendue. Lorsque cette méthode est appelée, le DE doit reprendre le programme comme si l’utilisateur l’avait détaché. Aucun autre événement de débogage ne doit être envoyé. Le programme doit être dans un État où il peut être attaché à partir d’une autre instance du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
