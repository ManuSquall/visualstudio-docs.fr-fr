---
title: IDebugDocumentPositionOffset2::GetRange | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 09b415e01b6c768f471bdf9ad2e595d1a910d582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Récupère la plage pour la position actuelle du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwBegOffset`  
 [dans, out] Décalage de la position de début de la plage. Définissez ce paramètre sur une valeur null si cette information n’est pas nécessaire.  
  
 `pdwEndOffset`  
 [dans, out] Décalage de la position de fin de la plage. Définissez ce paramètre sur une valeur null si cette information n’est pas nécessaire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La plage spécifiée dans un emplacement de document pour un point d’arrêt d’emplacement est utilisée par le moteur de débogage (DE) pour rechercher directement une instruction qui apporte réellement le code. Considérons par exemple le code suivant :  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La ligne 5 ne contribue aucun code pour le programme en cours de débogage. Si le débogueur qui définit le point d’arrêt à la ligne 5 veut le DE pour une recherche à une certaine quantité de la première ligne qui contribue le code, le débogueur spécifiez une plage qui comprend des lignes de candidat supplémentaire dans lequel un point d’arrêt peut être placé correctement. Le DE puis recherche vers l’avant à travers les lignes jusqu'à ce qu’il trouve une ligne qui peut accepter un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)