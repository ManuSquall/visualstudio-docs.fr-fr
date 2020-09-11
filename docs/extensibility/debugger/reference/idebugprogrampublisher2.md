---
title: IDebugProgramPublisher2 | Microsoft Docs
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
ms.openlocfilehash: bc6f0643066aaca4ba12d9818d449785f6edb752
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011864"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Cette interface permet à un moteur de débogage (DE) ou à des fournisseurs de ports personnalisés d’inscrire des programmes pour le débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Visual Studio implémente cette interface pour inscrire les programmes débogués afin de les rendre visibles pour le débogage de plusieurs processus.

## <a name="notes-for-callers"></a>Notes pour les appelants
Appelez `CoCreateInstance` la fonction com avec `CLSID_ProgramPublisher` pour obtenir cette interface (Voir l’exemple). Un fournisseur DE port personnalisé ou DE port utilise cette interface pour inscrire des nœuds de programme qui représentent des programmes en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Met un nœud de programme à la disposition DEs et du gestionnaire de débogage de session (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Supprime un nœud de programme pour qu’il ne soit plus disponible.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Met un programme à la disposition DEs et du SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Supprime un programme afin qu’il ne soit plus disponible.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Définit un indicateur qui spécifie qu’un débogueur est présent.|

## <a name="remarks"></a>Notes
Cette interface rend les programmes et les nœuds de programme disponibles (autrement dit, les « publie ») pour une utilisation par DEs et le gestionnaire de débogage de session (SDM). Pour accéder aux programmes publiés et aux nœuds de programme, utilisez l’interface [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . C’est la seule façon pour laquelle Visual Studio peut reconnaître qu’un programme est en cours de débogage.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instancier l’éditeur du programme et inscrire un nœud de programme. Cela est tiré du didacticiel, [publication du nœud de programme](/previous-versions/bb161795(v=vs.90)).

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