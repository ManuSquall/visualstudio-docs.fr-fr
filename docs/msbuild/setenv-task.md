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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5df538e7eb86a20dfc06e6e6558bded577ba3d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632379"
---
# <a name="setenv-task"></a>Tâche SetEnv

Définit ou supprime la valeur d’une variable d’environnement spécifiée.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **SetEnv**.

|Paramètre|Description|
|---------------|-----------------|
|**Nom**|Paramètre de **chaîne** obligatoire.<br /><br /> Nom d'une variable d'environnement.|
|**OutputEnvironmentVariable**|Paramètre de sortie de **chaîne** facultatif.<br /><br /> Contient la valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**.|
|**Préfixe**|Paramètre `Boolean` obligatoire.<br /><br /> Si `true`, concatène la valeur du paramètre **Value** avant la valeur de la variable d’environnement spécifiée par le paramètre **Name**, puis affecte le résultat à la variable d’environnement. Si `false`, affecte uniquement la valeur du paramètre **Value** à la variable d’environnement.|
|**Cible**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie l’emplacement de stockage d’une variable d’environnement. Spécifiez « Utilisateur » ou « Ordinateur ».<br /><br /> Pour plus d’informations, consultez [EnvironmentVariableTarget, énumération](xref:System.EnvironmentVariableTarget).|
|**Valeur**|Paramètre de **chaîne** facultatif.<br /><br /> Valeur affectée à la variable d’environnement spécifiée par le paramètre **Name**. Si le paramètre **Value** est vide alors que la variable existe, celle-ci est supprimée. Si la variable n’existe pas, aucune erreur ne se produit, même si l’opération ne peut pas être exécutée.<br /><br /> Pour plus d’informations, consultez [Environment::SetEnvironmentVariable, méthode](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
