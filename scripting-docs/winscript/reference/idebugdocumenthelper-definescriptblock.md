---
title: IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs
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
ms.openlocfilehash: 2a320e4e43a983ace4decbaa68de0b1a7df7d457
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783022"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indique à l’application d’assistance qu’une plage spécifique de caractères est un bloc de script qui est géré par le moteur de script donné.  
  
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
 [in] Emplacement du début du bloc de script.  
  
 `cChars`  
 [in] Nombre de caractères dans le bloc de script.  
  
 `pas`  
 [in] Le moteur de script pour ce bloc de script.  
  
 `fScriptlet`  
 [in] Indicateur qui indique si le bloc de script est un scriptlet.  
  
 `pdwSourceContext`  
 [out] Le contexte de la source pour le bloc de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un hôte intelligent peut utiliser cette méthode lorsque ses documents contiennent des blocs de script incorporés. Un moteur de langage peut utiliser cette méthode lors de son code contient des scripts incorporés pour d’autres langages.  
  
 Le moteur de script est responsable de tous les syntaxe coloration du code contexte recherches et dans le bloc de script.  
  
 Le `DefineScriptBlock` méthode doit être appelée une fois que le texte a été ajouté (par exemple, à l’aide de la `IDebugDocumentHelper::AddDBCSText` (méthode)) mais avant le script de bloc a été analysé (par exemple, à l’aide de la `IActiveScriptParse ::ParseScriptText` (méthode)).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)