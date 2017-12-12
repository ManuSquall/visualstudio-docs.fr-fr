---
title: "Gestion des ressources d’une application (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Gestion des ressources d'une application (.NET)
Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.  
  
Pour plus d’informations sur les ressources des applications de bureau .NET, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index). Pour plus d’informations sur les ressources des applications de bureau C++, consultez [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
Les applications UWP utilisent un autre modèle de ressources que celui des applications de bureau. Pour plus d’informations sur les ressources dans les applications Windows 8.x, consultez [Définition des ressources d’application (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Utilisation de ressources  
Dans un projet de code managé, ouvrez la fenêtre de propriétés du projet. Vous pouvez ouvrir la fenêtre de propriétés en procédant de l’une des façons suivantes :

- en cliquant avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**, puis sélectionnant **Propriétés**
- en tapant **propriétés de projet** dans la fenêtre **Lancement rapide**
- en choisissant **Alt + Entrée** dans la fenêtre **Explorateur de solutions**

Sélectionnez l’onglet **Ressources** . Vous pouvez ajouter un fichier .resx si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.  
  
Pour en savoir plus sur l’utilisation des ressources dans les projets C++, consultez [How to: Create a Resource](/cpp/windows/how-to-create-a-resource).