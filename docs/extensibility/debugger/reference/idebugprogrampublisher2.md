---
title: IDebugProgramPublisher2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721527"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Cette interface permet à un moteur de déboguer (DE) ou aux fournisseurs de ports personnalisés d’enregistrer des programmes de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Visual Studio implémente cette interface pour enregistrer les programmes en cours de débogage afin de les rendre visibles pour débogage à travers plusieurs processus.

## <a name="notes-for-callers"></a>Notes pour les appelants
Appelez la `CoCreateInstance` fonction `CLSID_ProgramPublisher` de COM avec pour obtenir cette interface (voir l’exemple). Un DE ou un fournisseur de port personnalisé utilise cette interface pour enregistrer les nœuds de programme qui représentent des programmes en cours de déboissailler.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
Cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Met un nœud de programme à la disposition des DE et du gestionnaire de débogé de session (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Supprime un nœud de programme de sorte qu’il n’est plus disponible.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Met un programme à la disposition des DE et du SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Supprime un programme de sorte qu’il n’est plus disponible.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Définit un drapeau indiquant qu’un débbuggeur est présent.|

## <a name="remarks"></a>Notes
Cette interface rend les programmes et les nœuds de programme disponibles (c’est-à-dire les « publie » pour les utiliser par les DE et le gestionnaire de débogé de session (SDM). Pour accéder aux programmes publiés et aux nœuds de programme, utilisez l’interface [IDebugProgramProvider2.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) C’est la seule façon pour Visual Studio de reconnaître qu’un programme est en cours de déboisation.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instantané l’éditeur du programme et enregistrer un nœud de programme. Ceci est tiré du Tutoriel, [La publication du nœud de programme](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
