---
title: Champ m_children | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a681f3a58fddbb136383a1259aa5e4c0c3b96b69
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289626"
---
# <a name="mchildren-field"></a>Champ m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La liste des tâches enfants qui sont inscrits auprès de cette tâche.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Notes  
 Alors que la tâche est en cours d’exécution, seul le thread qui exécute la tâche doit accéder à ce tableau.  
  
 Si la tâche est terminée, autres threads peuvent accéder à ce champ tant qu’ils n’ajoutent rien à celui-ci ou ne supprimez quoi que ce soit à partir de celui-ci.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)

