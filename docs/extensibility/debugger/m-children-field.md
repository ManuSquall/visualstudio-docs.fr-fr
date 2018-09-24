---
title: Champ m_children | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e27704484e5cfb320c8b65432fb3efb283054019
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231146"
---
# <a name="mchildren-field"></a>champ de m_children
La liste des tâches enfants qui sont inscrits auprès de cette tâche.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans *mscorlib.dll*)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Notes  
 Alors que la tâche est en cours d’exécution, seul le thread qui exécute la tâche doit accéder à ce tableau.  
  
 Si la tâche est terminée, autres threads peuvent accéder à ce champ tant que qu’ils n’ajoutent rien à celui-ci ou supprimer quoi que ce soit à partir de celui-ci.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)