---
title: "IDebugTypeFieldBuilder::CreatePrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePrimitive"
  - "IDebugTypeFieldBuilder::CreatePrimitive"
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugTypeFieldBuilder::CreatePrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un objet qui représente un type primitif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CreatePrimitive (  
   DWORD          dwElementType,  
   IDebugField ** pTypeField  
);  
```  
  
```c#  
int CreatePrimitive (  
   uint            dwElementType,  
   out IDebugField pTypeField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwElementType`  
 [in] Valeur de la [CorElementType, énumération](CorElementType%20Enumeration.xml) qui représente le type primitif.  
  
 `pTypeField`  
 [out] Retourne l’interface IDebugField pour le nouveau type.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)