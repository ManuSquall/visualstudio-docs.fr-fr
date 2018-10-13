---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e718df47b45c66b32d88b57b69d81b8f69b9077c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285803"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Affiche la boîte de dialogue spécifiée qui permet à l’utilisateur de sélectionner un port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hwndParentDialog`  
 [in] Handle de la boîte de dialogue parent.  
  
 `pbstrPortId`  
 [out] Chaîne d’identificateur de port.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. La valeur de retour `S_FALSE` (ou une valeur de retour de `S_OK` avec la `BSTR` définie sur `NULL`) indique que l’utilisateur a cliqué **Annuler**.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

