---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6da3a4404c9d982081ce21c5b1e253f6992042b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216310"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment instancier le serveur de publication du programme et inscrire un nœud de programme. Cela provient du didacticiel, [le nœud de programme de publication](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp#  
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
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

