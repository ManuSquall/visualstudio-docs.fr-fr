---
title: Structure AsyncTaskMethodBuilder - membres internes | Microsoft Docs
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
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14b17ebde347d2558c8d18277d5c49d066243034
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508296"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Structure AsyncTaskMethodBuilder - Membres internes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [AsyncTaskMethodBuilder Structure - membres internes](https://docs.microsoft.com/visualstudio/extensibility/debugger/asynctaskmethodbuilder-structure-internal-members).  
  
Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> rubrique de référence.  
  
 **Namespace :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membres internes  
  
|Name|Description|  
|----------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|  
|[champ de m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Représente l’objet de Générateur générique auquel cette instance non générique délègue.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Valeurs internes d’extension parallèle pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

