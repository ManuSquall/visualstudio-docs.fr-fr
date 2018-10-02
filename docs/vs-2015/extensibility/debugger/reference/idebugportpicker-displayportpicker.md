---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: f21168f249c10a4a7321b78195d86eba8c0a195a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496184"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugPortPicker::DisplayPortPicker](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker-displayportpicker).  
  
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

