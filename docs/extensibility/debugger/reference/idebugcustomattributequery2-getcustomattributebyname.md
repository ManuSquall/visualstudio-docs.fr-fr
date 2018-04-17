---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61cb7304f6fed3e2f3da55b94450c58bfc53334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtient les octets d’attributs personnalisés selon le nom de l’attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszCustomAttributeName`  
 [in] Chaîne contenant le nom de l’attribut personnalisé à rechercher.  
  
 `ppBlob`  
 [dans, out] Tableau qui contient les octets de l’attribut personnalisé.  
  
 `pdwLen`  
 [dans, out] Spécifie le nombre maximal d’octets à renvoyer dans le `ppBlob` de tableau et retourne le nombre d’octets réellement écrits dans le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE si l’attribut personnalisé n’existe pas. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Définir le `ppBlob` paramètre à une valeur null pour retourner le nombre d’attributs octets disponibles. Allouez un tableau, puis passer ce tableau dans pour la `ppBlob` paramètre.  
  
 Les octets de l’attribut représentent les données brutes de l’attribut personnalisé.  
  
 Si le `ppBlob` et `pdwLen` paramètres sont définis sur une valeur null, cette méthode peut être utilisée pour déterminer si l’attribut personnalisé existe simplement. Une alternative plus simple, toutefois, consiste à appeler la [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)