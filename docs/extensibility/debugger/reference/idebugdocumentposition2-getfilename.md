---
title: IDebugDocumentPosition2::GetFileName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentPosition2::GetFileName
helpviewer_keywords: IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c6f6088eb2b61f3923037b07200425ad879b8ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Obtient le nom de fichier du fichier source qui contient la position du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```csharp  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrFileName`  
 [out] Retourne le nom de fichier du fichier source.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un fichier source ne dispose pas toujours un nom de fichier (le fichier source n’existe pas sur le disque, par exemple).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)