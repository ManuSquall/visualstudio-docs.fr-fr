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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f672a9d18e4963dba47b46a12e113e0a25a618
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001548"
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