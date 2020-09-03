---
title: 'IDebugDocumentPositionOffset2 :: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200234"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère la plage pour la position actuelle du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in, out] Décalage de la position de début de la plage. Affectez à ce paramètre une valeur null si ces informations ne sont pas nécessaires.  
  
 `pdwEndOffset`  
 [in, out] Décalage de la position de fin de la plage. Affectez à ce paramètre une valeur null si ces informations ne sont pas nécessaires.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La plage spécifiée dans une position de document pour un point d’arrêt d’emplacement est utilisée par le moteur de débogage (DE) pour rechercher une instruction qui contribue en fait au code. Considérons par exemple le code suivant :  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La ligne 5 n’apporte aucun code au programme en cours de débogage. Si le débogueur qui définit le point d’arrêt à la ligne 5 souhaite que le DE recherche transfère un certain montant pour la première ligne qui contribue au code, le débogueur spécifie une plage qui comprend des lignes de candidats supplémentaires où un point d’arrêt peut être placé correctement. La fonction DE recherche ensuite dans ces lignes jusqu’à ce qu’elle ait trouvé une ligne pouvant accepter un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
