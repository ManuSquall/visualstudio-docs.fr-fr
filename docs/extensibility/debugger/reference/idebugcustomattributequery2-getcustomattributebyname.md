---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bc1b59d4f13029a765f11dfd4fe3dbe12778d00c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtient les octets d’attributs personnalisés étant donnés le nom de l’attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
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
 [dans, out] Spécifie le nombre maximal d’octets à renvoyer dans le `ppBlob` du tableau et retourne le nombre d’octets effectivement écrits dans le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou S_FALSE si l’attribut personnalisé n’existe pas. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Définir le `ppBlob` paramètre une valeur null pour retourner le nombre d’attributs octets disponibles. Allouez un tableau, puis passer ce tableau dans pour la `ppBlob` paramètre.  
  
 Les octets d’attribut représentent les données brutes de l’attribut personnalisé.  
  
 Si le `ppBlob` et `pdwLen` paramètres sont définis sur une valeur null, cette méthode peut être utilisée pour déterminer s’il existe simplement l’attribut personnalisé. Une alternative plus simple, cependant, consiste à appeler le [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
