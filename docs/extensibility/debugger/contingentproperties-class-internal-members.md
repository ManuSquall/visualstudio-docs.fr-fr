---
title: Classe ContingentProperties - membres internes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa554cc3740819d892ca1c3a60028be97928b51e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922214"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties - membres internes
Contient des propriétés supplémentaires pour un <xref:System.Threading.Tasks.Task> objet.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Membres  
  
### <a name="fields"></a>Champs  
  
|Name|Description|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|La liste des tâches enfants qui sont inscrits auprès de cette tâche.|  
  
## <a name="remarks"></a>Notes  
 Le .NET Framework initialise les champs de cette classe uniquement lorsqu’elles sont nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Mécanismes internes d’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)