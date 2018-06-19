---
title: m_children champ | Documents Microsoft
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
ms.openlocfilehash: e71bc592e77daac877b571b14acd2d62a8657b9f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109975"
---
# <a name="mchildren-field"></a>m_children champ
La liste des tâches enfants qui sont inscrits auprès de cette tâche.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Notes  
 Alors que la tâche est en cours d’exécution, seul le thread qui exécute la tâche doit accéder à ce tableau.  
  
 Si la tâche est terminée, autres threads peuvent accéder à ce champ tant qu’ils n’exigent pas ajouter quoi que ce soit ou supprimer tout élément à partir de celui-ci.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)