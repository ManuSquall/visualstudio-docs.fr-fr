---
title: SetEnv, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec47adec3a9c979a21a543f2c073c440384b26d1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572177"
---
# <a name="setenv-task"></a>SetEnv, tâche
Définit ou supprime la valeur d’une variable d’environnement spécifiée.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **SetEnv**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Name**|Paramètre **String** obligatoire.<br /><br /> Nom d'une variable d'environnement.|  
|**OutputEnvironmentVariable**|Paramètre de sortie **String** facultatif.<br /><br /> Contient la valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**.|  
|**Prefix**|Paramètre `Boolean` obligatoire.<br /><br /> Si `true`, concatène la valeur du paramètre **Value** avant la valeur de la variable d’environnement spécifiée par le paramètre **Name**, puis affecte le résultat à la variable d’environnement. Si `false`, affecte uniquement la valeur du paramètre **Value** à la variable d’environnement.|  
|**Target**|Paramètre **String** facultatif.<br /><br /> Spécifie l’emplacement de stockage d’une variable d’environnement. Spécifiez « `User` » ou « `Machine` ».<br /><br /> Pour plus d’informations, consultez « Énumération EnvironmentVariableTarget » sur le site web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Valeur**|Paramètre **String** facultatif.<br /><br /> Valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**. Si le paramètre **Value** est vide alors que la variable existe, celle-ci est supprimée. Si la variable n’existe pas, aucune erreur ne se produit, même si l’opération ne peut pas être exécutée.<br /><br /> Pour plus d’informations, consultez « Méthode Environment::SetEnvironmentVariable » sur le site web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)