---
title: SetEnv, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 960ebb94cf03ef293011645e732a0f0379d0fd47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852244"
---
# <a name="setenv-task"></a>SetEnv, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit ou supprime la valeur d’une variable d’environnement spécifiée.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **SetEnv**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Name**|Paramètre de **chaîne** obligatoire.<br /><br /> Nom d'une variable d'environnement.|  
|**OutputEnvironmentVariable**|Paramètre de sortie de **chaîne** facultatif.<br /><br /> Contient la valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**.|  
|**Préfixe**|Paramètre `Boolean` obligatoire.<br /><br /> Si `true`, concatène la valeur du paramètre **Value** avant la valeur de la variable d’environnement spécifiée par le paramètre **Name**, puis affecte le résultat à la variable d’environnement. Si `false`, affecte uniquement la valeur du paramètre **Value** à la variable d’environnement.|  
|**Cible**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie l’emplacement de stockage d’une variable d’environnement. Spécifiez « `User` » ou « `Machine` ».<br /><br /> Pour plus d’informations, consultez « Énumération EnvironmentVariableTarget » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**Valeur**|Paramètre de **chaîne** facultatif.<br /><br /> Valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**. Si le paramètre **Value** est vide alors que la variable existe, celle-ci est supprimée. Si la variable n’existe pas, aucune erreur ne se produit, même si l’opération ne peut pas être exécutée.<br /><br /> Pour plus d’informations, consultez « Méthode Environment::SetEnvironmentVariable » sur le site web [MSDN](https://msdn.microsoft.com/).|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
