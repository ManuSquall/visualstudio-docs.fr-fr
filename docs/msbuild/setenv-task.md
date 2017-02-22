---
title: "SetEnv Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tasks"
  - "SetEnv task (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# SetEnv Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit ou supprime la valeur d'une variable d'environnement spécifiée.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche **SetEnv** .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Name**|Paramètre **String** obligatoire.<br /><br /> Nom d'une variable d'environnement.|  
|**OutputEnvironmentVariable**|Paramètre de sortie **String** facultatif.<br /><br /> Contient la valeur assignée à la variable d'environnement spécifiée par le paramètre **Name**.|  
|**Prefix**|Paramètre `Boolean` obligatoire.<br /><br /> Si `true`, concatène la valeur du paramètre **Value** avant la valeur de la variable d'environnement spécifiée par le paramètre **Name**, puis assigne le résultat à la variable d'environnement.  Si `false`, assigne uniquement la valeur du paramètre **Value** à la variable d'environnement.|  
|**Target**|Paramètre **String** facultatif.<br /><br /> Spécifie l'emplacement où une variable d'environnement est stockée.  Spécifiez "`Utilisateur`" ou "`Ordinateur`".<br /><br /> Pour plus d'informations, consultez « Énumération EnvironmentVariableTarget » sur le site [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Value**|Paramètre **String** facultatif.<br /><br /> La valeur assignée à la variable d'environnement spécifiée par le paramètre **Name**.  Si **Value** est vide et la variable existe, la variable est supprimée.  Si la variable n'existe pas, aucune erreur ne se produit même si l'opération ne peut pas être exécutée.<br /><br /> Pour plus d'informations, consultez la « Méthode Environment::SetEnvironmentVariable » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Notes  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)