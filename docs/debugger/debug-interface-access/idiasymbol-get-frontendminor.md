---
title: "IDiaSymbol::get_frontEndMinor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_frontEndMinor (méthode)"
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le numéro de version secondaire de front-end.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le numéro de version secondaire front.end.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; Sinon, retourne `S_FALSE` ou code d’erreur.  
  
> [!NOTE]
>  Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Un compilateur est généralement constitué de deux éléments principaux : le serveur frontal (analyseur), qui gère l’analyse du code source dans un formulaire intermédiaire, et un serveur principal (Générateur de code), qui convertit le formulaire intermédiaire en assembly. Il n’est pas rare pour le serveur frontal d’avoir une version différente de celle du serveur principal.  
  
 Un front-end ou le numéro de version principale se compose de trois parties : \< principales>. \< secondaire>. \< build>, où \< principales> est le numéro de version principale, \< secondaire> est le numéro de version secondaire, et \< build> est le numéro de build. Par exemple, 13.10.3077.  
  
## <a name="requirements"></a>Spécifications  
  
|Situation|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)