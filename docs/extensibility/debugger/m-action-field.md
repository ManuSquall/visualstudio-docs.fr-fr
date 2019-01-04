---
title: Champ m_action | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b41c5d0ae7733a2a9256882852b9016d8e05e0bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944455"
---
# <a name="maction-field"></a>champ de m_action
Délégué qui représente le code à exécuter dans le <xref:System.Threading.Tasks.Task> objet.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans *mscorlib.dll*)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Notes  
 Il s’agit du `action` paramètre dans le <xref:System.Threading.Tasks.Task.%23ctor%2A> constructeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)