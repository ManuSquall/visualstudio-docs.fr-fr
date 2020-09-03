---
title: 'IDebugDisassemblyStream2 :: Seek | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203011"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Déplace le pointeur de lecture dans le flux de code machine un nombre d’instructions donné par rapport à une position spécifiée.  
  
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
 dans Valeur de l’énumération [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) qui spécifie la position relative pour commencer le processus de recherche.  
  
 `pCodeContext`  
 dans Objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente le contexte de code auquel l’opération de recherche est relative. Ce paramètre est utilisé uniquement si `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; sinon, ce paramètre est ignoré et peut être une valeur null.  
  
 `uCodeLocationId`  
 dans Identificateur de l’emplacement du code auquel l’opération de recherche est relative. Ce paramètre est utilisé si `dwSeekStart`  =  `SEEK_START_CODELOCID` ; sinon, ce paramètre est ignoré et peut avoir la valeur 0. Consultez la section Notes pour la méthode [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) pour obtenir une description d’un identificateur d’emplacement du code.  
  
 `iInstructions`  
 dans Nombre d’instructions à déplacer par rapport à la position spécifiée dans `dwSeekStart` . Cette valeur peut être négative pour revenir en arrière.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la position de la recherche était à un point au-delà de la liste des instructions disponibles. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Si la recherche était à une position avant le début de la liste, la position de lecture est définie sur la première instruction de la liste. Si le s’affiche à une position après la fin de la liste, la position de lecture est définie sur la dernière instruction de la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
