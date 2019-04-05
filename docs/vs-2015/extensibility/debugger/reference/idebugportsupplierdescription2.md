---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3da559a2d843ddb1129236966093b8a41f4234b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938696"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Permet la [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] l’interface utilisateur pour afficher le texte à l’intérieur de la **informations de Transport** section de la **attacher au processus** boîte de dialogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par les fournisseurs de port.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugPortSupplierDescription2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Récupère la description et les métadonnées de description pour le fournisseur de port.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
