---
title: IDebugDocumentHelper::DefineScriptBlock | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indique à l’application d’assistance qu’une plage particulière de caractères est un bloc de script qui est géré par le moteur de script donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Emplacement de début du bloc de script.  
  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Un hôte actif peut utiliser cette méthode lorsque ses documents contiennent des blocs de script intégrés. Un moteur de langage peut utiliser cette méthode lors de son code contient des scripts incorporés pour d’autres langues.  
  
 Le moteur de script est chargé de tous les syntaxe coloration du code contexte recherches et dans le bloc de script.  
  
 Le `DefineScriptBlock` méthode doit être appelée une fois que le texte a été ajouté (par exemple, à l’aide de la `IDebugDocumentHelper::AddDBCSText` (méthode)) mais avant le script de bloc a été analysé (par exemple, à l’aide de la `IActiveScriptParse ::ParseScriptText` (méthode)).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper (Interface)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)