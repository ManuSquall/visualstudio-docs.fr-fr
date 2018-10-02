---
title: Champ m_stateObject | Microsoft Docs
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
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d062d8a052ec89401d8b801ad329ed55ac86eb89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504802"
---
# <a name="mstateobject-field"></a>Champ m_stateObject
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [champ m_stateObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/m-stateobject-field).  
  
Objet qui représente les données utilisées par l’action.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Notes  
 Il s’agit du `state` paramètre dans le <xref:System.Threading.Tasks.Task.%23ctor%2A> constructeur. Il est également le champ de stockage pour le <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)

