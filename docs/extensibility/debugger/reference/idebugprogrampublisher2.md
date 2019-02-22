---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 616966eea58ab0f458abdfe2dace936a251ec8e0
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450293"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Cette interface permet à un moteur de débogage (dé) ou des fournisseurs de port personnalisé pour inscrire des programmes pour le débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
Visual Studio implémente cette interface pour enregistrer des programmes en cours de débogage afin de les rendre visibles pour le débogage entre plusieurs processus.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
Appel de COM `CoCreateInstance` fonctionne avec `CLSID_ProgramPublisher` pour obtenir cette interface (voir l’exemple). Un dé ou un fournisseur de port personnalisé utilise cette interface pour enregistrer des nœuds de programme qui représentent les programmes en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
Cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Rend un nœud de programme disponibles pour DEs et la session de débogage manager (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Supprime un nœud du programme afin qu’il n’est plus disponible.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Rend disponible pour DEs et le SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Supprime un programme afin qu’il n’est plus disponible.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Définit un indicateur signalant qu’un débogueur est présent.|

## <a name="remarks"></a>Notes
Cette interface permet de programmes et les nœuds de programme disponible (autrement dit, « » leur publication) pour une utilisation par DEs et le Gestionnaire de session de débogage (SDM). Pour accéder à des programmes publiés et les nœuds de programme, utilisez la [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface. Il s’agit de la seule façon de que Visual Studio puisse reconnaître qu’un programme est en cours de débogage.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instancier le serveur de publication du programme et inscrire un nœud de programme. Cela provient du didacticiel, [le nœud de programme de publication](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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
[Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)  
[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
