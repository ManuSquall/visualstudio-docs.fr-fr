---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3a11e368b6260d00f3f6ed0b19d94aa26bd31a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683608"
---
# <a name="moduleinfo"></a>MODULE_INFO
Décrit un module particulier (EXE, DLL ou assembly).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Membres
 dwValidFields une combinaison d’indicateurs à partir de la [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) énumération qui spécifie quels champs sont renseignés.

 m_bstrName le nom du module.

 m_bstrUrl l’URL de module.

 m_bstrVersion la version du module.

 m_bstrDebugMessage un message facultatif sur le module, par exemple, « symboles ne peut pas être chargés. »

 m_addrLoadAddress l’adresse de chargement de module.

 m_addrPreferredLoadAddress l’adresse de chargement par défaut du module.

 m_dwSize la taille du module.

 m_dwLoadOrder l’ordre de chargement de module.

 m_TimeStamp l’heure de que dernière modification du fichier de symboles.

 m_bstrUrlSymbolLocation l’emplacement du fichier de symboles (par exemple, «.\\») spécifié dans le module. Utilisé comme un emplacement de départ pour rechercher des symboles pour un module.

 m_dwModuleFlags une combinaison d’indicateurs à partir de la [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) énumération qui décrit le module.

## <a name="remarks"></a>Notes
 Cette structure est passée à la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) méthode où il est renseigné.

 Cette structure correspond à chaque module répertoriée dans le **Modules** fenêtre.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)