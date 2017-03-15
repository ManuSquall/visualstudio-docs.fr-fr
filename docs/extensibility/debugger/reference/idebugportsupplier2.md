---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "Interface de IDebugPortSupplier2"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Les orifices de puissance de cette interface à la session particulière nécessite le gestionnaire \(SDM\).  
  
## Syntaxe  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour représenter un fournisseur de port.  
  
## Remarques pour les appelants  
 Un appel à `CoCreateInstance` avec `GUID` d'un fournisseur de port retourne cette interface \(c'est la manière classique pour obtenir cette interface\).  Par exemple :  
  
```cpp#  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Un appel à [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) retourne cette interface, qui représente le fournisseur actuel de port utilisé par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md) retourne cette interface, qui représente le fournisseur de port qui a créé le port.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) représente une liste d'interfaces d' `IDebugPortSupplier` \(l'interface d' `IEnumDebugPortSuppliers` dérive d' [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), représentant tous les fournisseurs de port enregistrés avec [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\).  
  
 Un moteur de débogage en général n'interagissent pas avec un fournisseur de port.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugPortSupplier2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|obtient le nom de fournisseur de port.|  
|[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)|Obtient l'identificateur fournisseur de port.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|obtient un port d'un fournisseur de port.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|énumère les ports qui existent déjà.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Vérifie qu'un fournisseur de port prend en charge les nouveaux ports d'addition.|  
|[Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|ajoute un port.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Supprime un port.|  
  
## Notes  
 Un fournisseur de port peut s'identifient de nom et l'ID, ajouter et supprimer des ports, et énumérer tous les ports que le fournisseur de port fournit.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)