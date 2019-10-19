---
title: IDebugDocumentHelper ::D efineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576981"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indique à l’application d’assistance qu’une plage de caractères particulière est un bloc de script qui est géré par le moteur de script donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulCharOffset`  
 dans Emplacement du début du bloc de script.  
  
 `cChars`  
 dans Nombre de caractères dans le bloc de script.  
  
 `pas`  
 dans Moteur de script pour ce bloc de script.  
  
 `fScriptlet`  
 dans Indicateur qui signale si le bloc de script est un scriptlet.  
  
 `pdwSourceContext`  
 à Contexte source pour le bloc de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un hôte actif peut utiliser cette méthode lorsque ses documents contiennent des blocs de script incorporés. Un moteur de langage peut utiliser cette méthode lorsque son code contient des scripts incorporés pour d’autres langages.  
  
 Le moteur de script est responsable de toutes les recherches de coloration de syntaxe et de contexte de code dans le bloc de script.  
  
 La méthode `DefineScriptBlock` doit être appelée une fois que le texte a été ajouté (par exemple, à l’aide de la méthode `IDebugDocumentHelper::AddDBCSText`) mais avant que le bloc de script ait été analysé (par exemple, à l’aide de la méthode `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper :: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)