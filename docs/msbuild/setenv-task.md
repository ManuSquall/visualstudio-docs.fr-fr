---
title: SetEnv, tâche | Microsoft Docs
ms.date: 11/05/2018
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
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ec3170c9662cd9ef67521addfdf0d0095bd23b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747216"
---
# <a name="setenv-task"></a>Tâche SetEnv
Définit ou supprime la valeur d’une variable d’environnement spécifiée.

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche **SetEnv**.

|Paramètre|Description|
|---------------|-----------------|
|**Nom**|Paramètre **String** obligatoire.<br /><br /> Nom d'une variable d'environnement.|
|**OutputEnvironmentVariable**|Paramètre de sortie **String** facultatif.<br /><br /> Contient la valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**.|
|**Prefix**|Paramètre `Boolean` obligatoire.<br /><br /> Si `true`, concatène la valeur du paramètre **Value** avant la valeur de la variable d’environnement spécifiée par le paramètre **Name**, puis affecte le résultat à la variable d’environnement. Si `false`, affecte uniquement la valeur du paramètre **Value** à la variable d’environnement.|
|**Target**|Paramètre **String** facultatif.<br /><br /> Spécifie l’emplacement de stockage d’une variable d’environnement. Spécifiez « Utilisateur » ou « Ordinateur ».<br /><br /> Pour plus d’informations, consultez [EnvironmentVariableTarget, énumération](xref:System.EnvironmentVariableTarget).|
|**Valeur**|Paramètre **String** facultatif.<br /><br /> Valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**. Si le paramètre **Value** est vide alors que la variable existe, celle-ci est supprimée. Si la variable n’existe pas, aucune erreur ne se produit, même si l’opération ne peut pas être exécutée.<br /><br /> Pour plus d’informations, consultez [Environment::SetEnvironmentVariable, méthode](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)