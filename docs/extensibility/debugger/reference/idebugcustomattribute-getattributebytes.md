---
title: IDebugCustomAttribute::GetAttributeBytes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords: IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1258b2b7fdc1c91eaaa6265ce74a3891deda8ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Obtient les informations d’attribut comme un objet blob d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppBlob`  
 [dans, out] Tableau qui est rempli avec les octets d’attributs.  
  
 `pdwLen`  
 [dans, out] Spécifie le nombre maximal d’octets à renvoyer dans le `ppBlob` de tableau et retourne le nombre d’octets réellement écrits dans le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Définir le `ppBlob` paramètre à une valeur null pour retourner le nombre d’attributs octets disponibles. Allouez un tableau, puis passer ce tableau dans pour la `ppBlob` paramètre.  
  
 Les octets de l’attribut représentent les données brutes de l’attribut personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)