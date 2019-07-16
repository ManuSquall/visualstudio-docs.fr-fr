---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d774cc0bf6bca1278423249960bbc5233aa6ad37
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203011"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Déplace le pointeur de lecture dans le flux de code machine un nombre donné d’instructions par rapport à une position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSeekStart`  
 [in] Une valeur comprise entre le [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) énumération qui spécifie la position relative pour commencer le processus de recherche.  
  
 `pCodeContext`  
 [in] Le [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet représentant le contexte de code que l’opération de recherche est relatif. Ce paramètre est utilisé uniquement si `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; sinon, ce paramètre est ignoré et peut être une valeur null.  
  
 `uCodeLocationId`  
 [in] L’identificateur d’emplacement de code auquel l’opération de recherche est associée. Ce paramètre est utilisé si `dwSeekStart`  =  `SEEK_START_CODELOCID`; sinon, ce paramètre est ignoré et peut être défini sur 0. Consultez la section Notes pour la [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) méthode pour obtenir une description d’un identificateur d’emplacement de code.  
  
 `iInstructions`  
 [in] Le nombre d’instructions pour déplacer par rapport à la position spécifiée dans `dwSeekStart`. Cette valeur peut être négative pour le déplacer vers l’arrière.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la position de recherche a été au-delà de la liste des instructions disponibles. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Si la recherche a été vers une position avant le début de la liste, la position de lecture est définie à la première instruction dans la liste. Si vous le consultez consistait à une position après la fin de la liste, la position de lecture est définie à la dernière instruction dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
